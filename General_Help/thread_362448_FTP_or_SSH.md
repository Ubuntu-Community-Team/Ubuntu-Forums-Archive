---
title: "FTP or SSH"
date: 2007-02-15
forum: General Help
---

### Post by jdm2 on 2007-02-15
I'm running drapper.  I want a way to access my files remotely.  I want to be able to copy/paste my docs from and to my machine.  I know I can do this will ssh but I would like a simple gui if that's possible.  I don't know want I need or what.  Can you help me?  Thanks for the help.

---

### Post by vloris on 2007-02-15
You can try to install package sshfs, that way you can mount a remote machine accessible by ssh in your local filesystem space.

---

### Post by punx45 on 2007-02-15
do you plan on doing this inside or outside your LAN?

if inside, just set up file sharing - SAMBA or NFS as the case may be.

if outside, use SSH, and then get a client that does SFTP (FTP over SSH) for the remote computer (if you are permitted to install software)  when I am at work on a windows PC I use WinSCP.   On my Mac I use Cyberduck

the bonuses of FTP via SSH are:  no need to set up FTP server, when you log in you can access ANY part of the filesystem (that the logged in user would have permissions to locally).   its secure by SSH encrypted traffic, and less services with open ports on your home machine.   (why open up 22 and 23 when you can get it all done through 22?)

---

### Post by ehowell on 2007-02-15
SSH is overall better from a security standpoint I believe. You can also use a program like WinSCP (obviously in windows) to use a GUI interface to copy files through SSH.

---

### Post by tlacuache on 2007-02-15
You can access files on remote servers running ssh directly from nautilus. In the nautilus location field, type:

sftp://username@host:/remotedirectory

So if your user was "user" and the host was "1.2.3.4", you would do something like:

sftp://user@1.2.3.4:/home/user/

That's pretty easy. :)

---

### Post by phork on 2007-02-15
gFTP is pretty sweet for this sort of thing too.  If you've ever used LeechFTP or FlashFXP the ui will be comfortable (does scp as well now).

---

### Post by jdm2 on 2007-02-15
I would like to use ssh since it will be much more secure.  The computer that I will use to access my ubuntu machine will be xp.  I will try the WinSCP.  Thanks for the help.  I won't be on my LAN when I want to access it.  I want to access it from school or work.  Thanks for the help.

---

### Post by jdm2 on 2007-02-15
I tried the WinSCP.  I like it so far.  Can you explain what all I can do with it.  It does use ssh?  Can I preview something before I copy it to the xp computer and can I paste stuff to my ubuntu box from xp?  Thanks for the help.

---

