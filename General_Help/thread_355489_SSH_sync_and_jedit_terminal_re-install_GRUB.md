---
title: "SSH sync? and jedit terminal? re-install GRUB?"
date: 2007-02-07
forum: General Help
---

### Post by mattgaunt on 2007-02-07
Hey every1

A few random questions

1.) I do alot of work on the servers at uni over ssh, is there a program to synchronise my folders on the uni servers so i have the same thing on my computer, since jedit will not pick up any files over ssh i have to save them to home directory

2.)Does anyone know the plugin i need so i can have a terminal in jedit? (So useful for programming)

3.)Im re-installing windows xp onto a small hard driver so i can have all my music and files on a large hard drive so both windows and xp can read and write to it

Any help on any of the above would be fantastic

Thanks in advance

Best Wishes to all ):P 

Matt

---

### Post by llamakc on 2007-02-07
1) rsync will work for you.

---

### Post by bodhi.zazen on 2007-02-07
> **mattgaunt said:**
> Hey every1

A few random questions

1.) I do alot of work on the servers at uni over ssh, is there a program to synchronise my folders on the uni servers so i have the same thing on my computer, since jedit will not pick up any files over ssh i have to save them to home directory

rsync ?

> 2.)Does anyone know the plugin i need so i can have a terminal in jedit? (So useful for programming)

Not I

> 3.)Im re-installing windows xp onto a small hard driver so i can have all my music and files on a large hard drive so both windows and xp can read and write to it

is this your grub question ?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Also you may want to go with ext3 for file sharing with windows:

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

> Any help on any of the above would be fantastic

Thanks in advance

Best Wishes to all ):P 

Matt

:lolflag:

---

### Post by mattgaunt on 2007-02-07
Do you have any good guide or anythin to use rsync to make it just automatically sync with an ssh folder??? 

and thanks fors the guide on installing GRUB it looks like it should do the trick although it doesnt look like it would install GRUB onto the windows partition dnt know if this is true but im sure i can add it to the GRUB boot menu

---

### Post by bodhi.zazen on 2007-02-07
rsync : 

[http://sunsite.dk/info/guides/rsync/rsync-mirroring.html](http://sunsite.dk/info/guides/rsync/rsync-mirroring.html)

[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

[http://www.fredshack.com/docs/rsync.html](http://www.fredshack.com/docs/rsync.html)

Grub should be installed into the MBR not your windows partition ...

---

### Post by mattgaunt on 2007-02-07
i dont think rsync is working, not sure if my uni server has rsync installed

---

### Post by llamakc on 2007-02-07
You could investigate sshfs. This won't sync folders but will let you view a folder from a remote host as if it were local because it will be mounted.

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/) is the first Google return for "sshfs ubuntu" and here's a howto:

[http://doc.gwos.org/index.php/Sshfs](http://doc.gwos.org/index.php/Sshfs)

---

