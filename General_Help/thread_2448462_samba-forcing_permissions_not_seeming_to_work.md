---
title: "samba-forcing permissions not seeming to work"
date: 2020-08-08
forum: General Help
---

### Post by jfaberna on 2020-08-08
I'm doing some testing on file permissions with samba/cifs between an Ubuntu 18.04 client and a Raspberry pi host.

I have setup the server smb.conf for the share under test with:
```
[jim]
path = /srv/jim
browsable =yes
writable = yes
guest ok = no
read only = no
force group = users
force user = jim
create mask = 0664
force directory mode = 2775

```
From Ubuntu if I mount using:```
sudo mount -t cifs //192.168.0.240/jim /mnt/rpi-nas -o user=jim,password=123456
```
My permission on the client look like: 755 root:root

However, if from Ubuntu I mount using:```
sudo mount -t cifs //192.168.0.240/jim /mnt/rpi-nas -o user=jim,password=123456,uid=jim,gid=jim
```
My permissions on the client look like: 755 jim:jim

On the server the permissions are 644 jim:user for any file created as user jim when the mount included the uid, gid.

Why are uid and gid required to get r/w access for user jim, and why are the permissions seen as 755 vs.644

---

### Post by Morbius1 on 2020-08-08
Samba is a client-server protcol.

The server is always in control over what the client can do and the resulting permissions of his actions. A client can never override those decisions.

CIFS on the client however creates a virtual filesystem with a "view" of that server with a set of permissions that pertains only to that "view" and only to that client. CIFS will by default mount with root as owner / group and permissions of 755. 

But the "view" can be modified to pretty much anything you want:

Want to change the owner / group: Add uid=jim,gid=jim

Want to change permissions: Add dir_mode=0755,file_mode=0644,nounix

Want to make it so every local user on the clinet has read / write access to the share: Add dir_mode=0777,file_mode=0666,nounix

[COLOR=#ff0000] Note: Even though you allow every local user on the client r/w access they are all still "jim"  to the server because that is the user whose credentials were accepted.[/COLOR]

[COLOR=#0000cd] *CIFS is sorta kinda like a network version of NTFS to Linux. Although the mechanism is different ntfs is also a virtual filesystem that creates a "view" but in this case of a partition.*[/COLOR]

---

### Post by jfaberna on 2020-08-12
> **Morbius1 said:**
> Samba is a client-server protcol.

The server is always in control over what the client can do and the resulting permissions of his actions. A client can never override those decisions.

CIFS on the client however creates a virtual filesystem with a "view" of that server with a set of permissions that pertains only to that "view" and only to that client. CIFS will by default mount with root as owner / group and permissions of 755. 

But the "view" can be modified to pretty much anything you want:

Want to change the owner / group: Add uid=jim,gid=jim

Want to change permissions: Add dir_mode=0755,file_mode=0644,nounix

Want to make it so every local user on the clinet has read / write access to the share: Add dir_mode=0777,file_mode=0666,nounix

[COLOR=#ff0000] Note: Even though you allow every local user on the client r/w access they are all still "jim"  to the server because that is the user whose credentials were accepted.[/COLOR]

[COLOR=#0000cd] *CIFS is sorta kinda like a network version of NTFS to Linux. Although the mechanism is different ntfs is also a virtual filesystem that creates a "view" but in this case of a partition.*[/COLOR]

Thanks, how would this be different if the smb.conf file had not included:
```
force group = users
force user = jim
create mask = 0664
force directory mode = 2775
```

---

### Post by Morbius1 on 2020-08-12
It all depends on who is accessing the share and from where - other local users on the server itself or client users on the network.

[COLOR=#b22222]**Lost my internet connection before I finished........**[/COLOR]

> [jim]
path = /srv/jim
browsable =yes
writable = yes
guest ok = no
read only = no
force group = users
force user = jim
create mask = 0664
force directory mode = 2775

On the server what you told samba to do is save new files and folders from the network client as owned and writeable to jim and all members of the "user" group ( assuming your default umask is 002 ). They will inherit the group of the parent - presumably "users". You may have a need for that on the server for some reason but it is not required for the samba client since everything is owned by "jim" and all client users appear as "jim"

To any network client accessing this share samba the server will see  them as "jim" because that is what you told samba to do "force user =  jim". The force group, masks, and modes - from a client perspective - will not break anything but are  irrelevant.

---

