---
title: "Samba share problems with Ubuntu 7.10"
date: 2008-02-17
forum: General Help
---

### Post by flippedup on 2008-02-17
Having some problems with Samba client/server under Ubuntu 7.10 Gutsy.

Versions
________

samba:
  Installed: 3.0.26a-1ubuntu2.3
  Candidate: 3.0.26a-1ubuntu2.3
  Version table:
 *** 3.0.26a-1ubuntu2.3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
        100 /var/lib/dpkg/status
     3.0.26a-1ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages

kernel:
  2.6.22-14-server #1 SMP Tue Feb 12 08:27:05 UTC 2008 i686 GNU/Linux

Information
___________

Server /etc/fstab:

/dev/fileserver/personal /mnt/four/personal  ext3 rw,defaults 0 0

Client /etc/fstab:

//four/personal /mnt/four/personal cifs credentials=/home/system/.smb,owner,uid=    system,gid=system,rw 0 0

Server /etc/samba/smb.conf:

[global]
  workgroup = flippedup
  server string =
  dns proxy = no
  log file = /var/log/samba/log.%m
  max log size = 1000
  syslog = 0 
  panic action = /usr/share/samba/panic-action %d
  encrypt passwords = true
  passdb backend = tdbsam
  obey pam restrictions = yes 
  invalid users = root
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
  socket options = TCP_NODELAY

  username map = /etc/samba/smbusers

  create mask = 0644
  directory mask = 0755
  force user = root
  force group = root
  guest ok = no
  browseable = no
  public = no

  map to guest = bad user
  guest account = nobody

[personal]
  path = /mnt/four/personal
  admin users = tlorenzo
  read only = no

Problem
_______

I am able to connect and read/write/modify the files on the share.  However, when I copy over a directory of folders/files from my local machine to the mounted share it throws the following error (this even happens when I try to access the share through smb://servername/sharename/):

"Error 'Access denied' while copying '/directory/'. Would you like to continue?"

At this point, I can keep pressing 'Retry' for each directory that it encounters and everything will copy correctly.

Copying a single or multiple files over doesn't throw any errors.

Any insight would be greatly appreciated!

Thanks!

---

### Post by honeydew on 2008-02-18
hrmm did you follow a guide to setup samba? I have a samba server running on 7.10 but am not experiencing the same issues.

here is a related post...
[http://ubuntuforums.org/showthread.php?t=227338](http://ubuntuforums.org/showthread.php?t=227338)

---

### Post by flippedup on 2008-02-20
No, I've been using samba for a while actually - I just made sure samba was installed, changed the smb.conf, added the user in linux, added the user to smbusers and assigned a samba password.  Now, I just changed browseable = Yes and that seemed to fix the copying directory problem when I access the share through smb://computer_name/share_name/.  It still doesn't seem to work with my mounted drives.  Although, if I open a shell and do sudo cp -R /my_directory/ /mnt/computer_name/share_name/ it copies without any problems.  I get a permission denied error if I don't prepend sudo.

---

