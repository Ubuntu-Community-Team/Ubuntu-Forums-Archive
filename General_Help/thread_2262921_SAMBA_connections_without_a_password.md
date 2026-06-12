---
title: "SAMBA connections without a password"
date: 2015-01-28
forum: General Help
---

### Post by james251822 on 2015-01-28
I've been running Ubuntu 12.04 with Samba 3.x and using security = share. This has allowed my windows machines to connect to a few shares without any password prompts. It also works well for my XBMC (or Kodi now) systems. I'm now installing 14.04 LTS and it has SAMBA 4 so I can no longer use share-level security - I must use user level security. I've followed the advice to put map to guest = bad user in the smb.conf file but I'm still getting the prompt for a login. Can anyone help?

```

[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
dns proxy = no

 unix extensions = no
 wide links = yes
 follow symlinks = yes

#============================ Share Definitions ==============================
[Anonymous]
path = /home/james/allaccess
browsable =yes
writable = yes
guest ok = yes
read only = no

[music]
path = /mount/disk2/landingzone/music
available = yes
browsable = yes
public = yes
writable = yes
dfree command = /usr/bin/greyhole-dfree
vfs objects = greyhole
guest ok = yes

[pictures]
path = /mount/disk2/landingzone/pictures
available = yes
browsable = yes
public = yes
writable = yes
dfree command = /usr/bin/greyhole-dfree
vfs objects = greyhole

[share]
path = /mount/disk2/landingzone/share
available = yes
browsable = yes
public = yes
writable = yes
dfree command = /usr/bin/greyhole-dfree
vfs objects = greyhole

[sam]
path = /mount/disk2/landingzone/sam
available = yes
browsable = yes
public = yes
writable = yes
dfree command = /usr/bin/greyhole-dfree
vfs objects = greyhole

[video]
path = /mount/disk2/landingzone/video
available = yes
browsable = yes
public = yes
writable = yes
dfree command = /usr/bin/greyhole-dfree
vfs objects = greyhole



```

---

### Post by lukeiamyourfather on 2015-01-28
Under the global settings use "security = user" and an example share is below.

```

[engineering]
   path = /tank/engineering/engineering
   browsable = yes
   guest ok = yes
   read only = no
   writable = yes
   public = yes
   guest account = nobody

```

Set the owner of the files to nobody:nobody and it should work. Or change nobody to something else on the config and the files like if you want it to map to your local user instead.

---

### Post by james251822 on 2015-01-29
Thanks for the response.

I made the changes you suggested but I'm afraid it made no difference. I'm getting the password request on my windows machine when I point it at \\server-ip-address\ so before the shares even show up. Any other pointers?

EDIT: Just added  [FONT=courier new]auth methods = guest[FONT=verdana] to the global section and it all seems to work as desired!
[/FONT]
[/FONT]

---

