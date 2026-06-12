---
title: "upgrade from cifs vers=1.0 to vers=2.0"
date: 2022-07-08
forum: General Help
---

### Post by thomasfrei on 2022-07-08
Hi all,

on my linux system, I mount a drive from a linux server using cifs.
```
[COLOR=#232629][FONT=-apple-system]mount -t cifs -o user=xxx,vers=1.0 //share /mountpoint[/FONT][/COLOR]
```
The files, located on the server, appear as they should - this is very important for me.

Now I want to upgrade the protokoll version to vers=2.0 for performance reasons.

But, since the 2.0 is active, all files are owned by root:root!

I there any way to see the files as different users again?

My smb.conf looks like:

```
[global]
workgroup = SBSEUROPE
interfaces = 127.0.0.1 eth0 eth1 eth1:1 eth1:2 eth1:3
bind interfaces only = true
printing = cups
printcap name = cups
map to guest = Bad User
security = user
ntlm auth = yes
client ntlmv2 auth = yes
encrypt passwords = yes
passdb backend = smbpasswd
server string = Samba Server AugProd-TSWv1
#netbios name = aug-tsw2
domain master = false
domain logons = no
local master = no
preferred master = auto
load printers = no
ldap suffix = dc=example,dc=com
smb ports = 445
disable netbios = yes
#wins server = 3.30.223.11
wins support = No
usershare allow guests = No
ldap admin dn = 

oplocks = no
level2 oplocks = no
kernel oplocks = no 
nt acl support = no 
strict locking = no
server signing = desired

log level = 2
#log file size 10MB
max log size = 10

[tester1]
path = /home/tester1
browseable = yes
writable = yes
comment = Produktion tester1
directory mode = 0775
guest ok = no
valid users = tester1 TFrei 
force user = tester1
force group = tester
create mask = 0664

oplocks = no
locking = no
acl check permissions = false
level2 oplocks = no
strict locking = no
blocking locks = no ```

---

### Post by TheFu on 2022-07-08
a) On Ubuntu, we should choose the highest CIFS protocol version that is supported by the other systems. There are security and performance reasons for this.  

b) the /etc/samba/smb.conf file has only a few settings that related to CIFS mounting (as a client).  Most mount options get placed in the mount command, the fstab, or the autofs config files.  I generally test new mounts with a mount ..... command, then take those options into either the fstab (permanent mount) or into the autofs config files (for sometimes only) mounts.  I never (ok, 0.00001% of the time), use any GUI to remotely mount CIFS stuff. I will use a GUI to access sftp servers, occasionally, but even that isn't very often.

c) With CIFS, we need to provide the access credentials on the mount command.  BTW, Win7 supports vers=2.1.   win10 supports vers=3

The options I last used from Linux to mount Win7 CIFS storage was:
```
sudo mount -t cifs   -o iocharset=utf8,rw,vers=2.1,uid=thefu,gid=some_group,file_mode=0664,dir_mode=0775,credentials=/etc/samba/romulus-music.credentials \
      //{ip address}/sharename   /mountpoint
```

If there are spaces in the sharename or mountpoint, those need to be quoted.  Don't have any spaces in the options.  The 'mode' options are normal Unix chmod values, in octal. I think the leading zero isn't optional.

The uid/gid are on the Linux side. 
The romulus-music.credentials file looks like this:
```
username=Bob
password=My92Kewl^Password
```
This file is owned by root and cannot be read by any other user on the system.  This is because the login credentials are the same as handing over the login to the Windows system. That shouldn't be accessible.

After that works, putting the mount information into the /etc/fstab will mount the CIFS stuff before the user logs in, so services/daemons can run automatically at boot.

I've never used a workgroup. That information may need to be added to the credentials file.  There is a manpage which explains it, somewhere.  I'd guess it would be domain= as the option on a new line, but I didn't look it up.  mount.cifs probably has more.  Yep, the manpage for mount.cifs spells out the options.

---

### Post by TheFu on 2022-07-08
BTW, if you are sharing storage between linux and linux, why not use the the native NFS?  It is faster and provides Unix permissions, so things "just work."

---

### Post by Irihapeti on 2022-07-09
*Thread moved to **General Help** as it's a support request.*

---

### Post by thomasfrei on 2022-07-11
Hi theFu,
thank you for the reply.

I found out, that the uid and gid can be set with the gid/uid parameter, but this sets ALL files to this uid/gid!
What I need is, that the different files still belong to the different users as on the server.

This was possible with vers=1.0.

I think/hope, this is still possible with vers=2.0 or higher.

---

### Post by TheFu on 2022-07-11
> **thomasfrei said:**
> Hi theFu,
thank you for the reply.

I found out, that the uid and gid can be set with the gid/uid parameter, but this sets ALL files to this uid/gid!
What I need is, that the different files still belong to the different users as on the server.

This was possible with vers=1.0.

I think/hope, this is still possible with vers=2.0 or higher.

To my knowledge, CIFS mounts will only use 1 Unix-side username.  If you want full permissions control, use NFS.
There is an exception - HOME directories.  The [homes] stanza on the samba server, will connect the clients to the $HOME directory based on the credentials supplied.  1 user = 1 HOME directory, so if steve and alfonzo are users on the Linux host, any connection using their credentials will go to the correct $HOME for each, respectively.  steve will be presented /home/steve and alfonzo will get /home/alfonzo.

But for remote storage between any Unix systems, nfs is best.

---

### Post by thomasfrei on 2022-07-13
Hi,

home mounts are not working for me, because I need tht different owners - its not working if the files belong to one singe user - no matter if its root ore any other user.

I also tried NFS - yes, it's working properly but very, very, very, very slow - so this is no solution for me. (I need to speedup network)

any other idea?

Best regards

---

### Post by TheFu on 2022-07-13
> **thomasfrei said:**
> Hi,

home mounts are not working for me, because I need tht different owners - its not working if the files belong to one singe user - no matter if its root ore any other user.

I also tried NFS - yes, it's working properly but very, very, very, very slow - so this is no solution for me. (I need to speedup network)

any other idea?

Best regards

The "home" mount will work for different users.  I use it all the time.  But the files are specific to each HOME directory for the specific user. If you need all the files to be shared by multiple users, that's specifically when I'd use NFS and standard Unix groups.  CIFS is per-user connections and the underlying Samba effectively ignores the Unix file system permissions.  In ubuntu, the root user shouldn't be used for any sort of remote access or storage.  If a different user is necessary, then a different CIFS share is needed.

NFS should be faster than CIFS for typical uses. If it isn't that's odd.  I think the only time when CIFS might be faster is when huge files are involved. NFS performance handles lots of small file accesses better than CIFS. Oddly, CIFS doesn't work as well for streaming video media. This is a well-known issue in the Kodi forums ... and their solution after removing wifi and other choke points to the networking is to switch to NFS.  [https://kodi.wiki/view/NFS](https://kodi.wiki/view/NFS)

NFS v4.x includes multi-channel mounts controlled with the nconnect= mount option.  When I tested here, with 1, 2, 4, 8, 12, 16 connections per mount, the difference between 2 and 12 was tiny, so I chose to use just 2 connections.  An auto.nfs line:
```
/VMs  -fstype=nfs,nconnect=2,proto=tcp,rw,async  romulus:/raid/media/VMs 
``` on a client system.

It also appears that some 'global' settings aren't in the global stanza, like they need to be.  Run **testparm -s** to see what Samba is actually seeing as the config file.  It also appears that the config file has some left over, invalid settings that don't apply post-v1. Remove those. This will require reading the manpages carefully to see which settings only apply to vers1 CIFS. I don't have them all memorized, since we haven't used vers1 in decades.

BTW, usernames should be all lowercase on Unix systems (and for Samba).  This avoids problems.

---

