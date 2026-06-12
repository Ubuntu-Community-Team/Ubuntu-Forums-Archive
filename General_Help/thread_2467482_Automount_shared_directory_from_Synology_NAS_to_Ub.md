---
title: "Automount shared directory from Synology NAS to Ubuntu 20.04LTS Failed"
date: 2021-09-28
forum: General Help
---

### Post by Minus63 on 2021-09-28
[URL="https://askubuntu.com/posts/1366058/timeline"]
[/URL]  
          
                                        Good morning everybody

Until now the NAS users were locally registered in the NAS, the users  had for simple login their identifier in the form «User», the mounting  of the volume via pam_mount worked perfectly with the line:

 ```
<volume fstype="cifs" server="172.16.0.50" path="data" mountpoint="/home/%(USER)/Reseau" user="*" sgrp="utilisa. du domaine" options="nodev,nosuid,dir_mode=0700,vers=2.1" />

``` Linux PCs are in an Active Directory domain, and for users, the AD session and local password in the NAS were the same. It forces users to change a default password in the nas to put the same one they use in the active directory domain
 And even if I wanted to force the mounting of a network disk with my  rights to use sudo the following command worked wonderfully:
 ```
sudo mount.cifs //172.16.0.50/data /home/mon_login_user/Reseau -o username=mon_login_user,vers=2.1,file_mode=0666,dir_mode=0700

``` Now I want to make things cleaner so the NAS is in the active  directory domain, and so for it users have for login «domain/user» and  no more «user»
 I have a new Synology NAS with DSM7.
 Writing **as root** this command works perfectly and **as root**, I can go read my network disk. So the editing is done well **as root** with this command.
 ```
mount.cifs //172.16.0.50/data /home/mon_login_admin/Reseau -o domain=mondomaine.lan,username=mon_login_user,vers=3,file_mode=0666,dir_mode=0700

``` But now **as User** with sudo rights if I type this same  command I no longer have access to the mount point, while I do have  read/write rights on this directory and that, with the same user, on  windows 10 pro, there is no problem:

 ```
sudo mount.cifs //172.16.0.50/data /home/monloginuser/Reseau -o domain=mondomaine.lan,username=mon_login_user,vers=3,file_mode=0666,dir_mode=0700

``` Network mount is unreadable for my user:

 ```
monloginuser@Test:~$ cd Reseau/
-bash: cd: Reseau/: Permission non accordée
serrec@Test:~$ ls -l
total 32
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Bureau
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Documents
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Images
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Modèles
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Musique
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Public
drwx------ 2 root   root                   0 sept. 20 10:57 Reseau
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Téléchargements
drwxr-xr-x 2 monloginuser utilisa. du domaine 4096 sept. 27 08:56 Vidéos

``` While the rights to the "Reseau" directory should be: monloginuser utilisa. du domaine
 And of course, with pam_mount level with the line:
 ```
<volume fstype="cifs" server="172.16.0.50" path="data" mountpoint="/home/%(USER)/Reseau" user="*" domain="mondomaine.lan" sgrp="utilisa. du domaine" options="nodev,nosuid,dir_mode=0700,vers=3" />

``` I have no mounting and error feedback of this type in /var/log/auth.log
 ```
Sep 27 09:45:21 Test sshd[2172]: pam_unix(sshd:session): session opened for user monloginuser by (uid=0)
Sep 27 09:45:23 Test sshd[2172]: (mount.c:72): Messages from underlying mount program:
Sep 27 09:45:23 Test sshd[2172]: (mount.c:76): mount error(13): Permission denied
Sep 27 09:45:23 Test sshd[2172]: (mount.c:76): Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)
Sep 27 09:45:23 Test sshd[2172]: (pam_mount.c:522): mount of data failed

``` I don’t see what the problem is with permission, there’s something that’s not going right, but I can’t find what
 I have another line in my pam_mount.conf.xml file that points to my  old NAS, with the user being registered locally (and not in the domain)  and on its side no worries, the automount of the network share directory  always done without problems.
 On the other hand, my windows machines have absolutely no problem  connecting to this NAS, despite the fact that the NAS is now in the  domain.
 So I conclude for my part that the concern does not come from the configuration of the NAS but from the configuration of Ubuntu.
 This is what I find as a trace of error in syslog when I want to open a AD user session
 ```
Sep 27 11:03:33 Test kernel: [ 5942.432006] CIFS: Attempting to mount \\172.16.0.50\data
Sep 27 11:03:33 Test kernel: [ 5942.445924] CIFS: Status code returned 0xc000006d STATUS_LOGON_FAILURE
Sep 27 11:03:33 Test kernel: [ 5942.445939] CIFS: VFS: \\172.16.0.50 Send error in SessSetup = -13
Sep 27 11:03:33 Test kernel: [ 5942.445956] CIFS: VFS: cifs_mount failed w/return code = -13
Sep 27 11:03:33 Ubuntu2004 kernel: [ 5942.474864] audit: type=1400 audit(1632733413.753:774): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/proc/601/cmdline" pid=690 comm="sssd_nss" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep 27 11:03:33 Test systemd[1]: Created slice User Slice of UID 236606829.

``` I’m out of ideas
 Thank you for your help.

---

### Post by TheFu on 2021-09-28
CIFS is user-to-server.
NFS is system-to-server (or server-to-server)
If we use NFS, then user access is managed by their local userids ( can use LDAP too).  It provides native file permissions and nearly all the same features that we come to expect from native Unix file systems which NTFS and CIFS do not support.  If your synology supports NFSv4, it can be faster too. Kerberos is available in NFSv4 with server-to-server tickets.

NFS has support to understand mounting user HOME directories too, so you could place /home on the NAS, if you like.  Or call it /u/{userid}.  In large environments, there may need to be hundreds of different home directory mounts to support the thousands of users on a system.  That's where using the automounter system matters, not to be confused with the use of "automount" above, really it should be said as automatice mounting unless the actual tool - "automount" is being used.   Automounter has been around since the early 1990s on Unix. In Linux, we use **autofs** to access it.  [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)  [http://manpages.ubuntu.com/manpages/bionic/man8/autofs.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/autofs.8.html) have have more details.

We  can use [https://help.ubuntu.com/community/AutofsLDAP](https://help.ubuntu.com/community/AutofsLDAP)  LDAP too.  I haven't done this, but I use autofs all the time across systems here and have for longer than Ubuntu has existed.
I have used LDAP for centralized user management, just not the MSFT flavor. It follows the POSIX schema for Users on Unix systems.

In short, use NFS, the native network file system for Unix systems.

BTW, finding people here using AD will be hard.  I've never used it or managed it. 
If you have users and groups working in Linux feed by AD, then using NFS to allow access to shared directories is pretty easy.  Setup the directory to be shared with users, ensure they are all in the same group, if they need write access, then use the setgid and group-write permission bit on that directory and make the top directory use the same group.  Every new object below that top directory will inherit the group and write permissions automatically. Any existing files/directories won't be altered, so if you need to make those available to all the clients too, you'll want to fix those permissions and groups and set the setgid bit on every subdirectory.  That's just 2 or 3 commands.
[https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) explains with an example for the group and permissions.

---

### Post by Minus63 on 2021-09-29
Thank you for all theses informations

I did a graphical test under 20.04LTS:

Open the file explorer / connect to a server (enter smb://ip_of_my_nas), in the window that opens I enter my username/domain/password, register the information or not, and everything is OK and i can see all my directory and files.

How can i script this without, for example, used credential file, or make an automatic mount (by capture user login and user password) at the opening of the session?

---

### Post by TheFu on 2021-09-29
I don't think it is possible if Kerberos is being used by AD.
Also, the GUI connections for CIFS are usually slow, nothing like what autofs or /etc/fstab mounts provide.

I'd strongly suggest you look at NFS.  Don't know what more I can say.  Unix uses NFS.

---

### Post by Minus63 on 2021-09-30
Thank you for everything ;)

---

### Post by Minus63 on 2021-09-30
Finally solved problem by replacing line:

```
<volume fstype="cifs" server="172.16.0.50" path="data" mountpoint="/home/%(USER)/Reseau" user="*" domain="mondomaine.lan" sgrp="utilisa. du domaine" options="nodev,nosuid,dir_mode=0700,vers=3" />
```

by

```
<cifsmount> mount.cifs //172.16.0.50/data /home/%(USER)/Reseau -o domain=mondomaine.lan,username=%(USER),vers=3,file_mode=0777,dir_mode=0777 </cifsmount>
```

The new file /home/user/Reseau have 777 rights and the owner is root:root, but all rights rwx are managed by the NAS and active directory.

---

