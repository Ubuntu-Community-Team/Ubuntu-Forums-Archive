---
title: "How do I bind mount a directory after my ecryptfs home is mounted?"
date: 2013-08-06
forum: General Help
---

### Post by halfbeing on 2013-08-06
How do I get a directory to bind mount at startup to a location on my ecryptfs encrypted home directory? I can't use fstab because that gets dealt with before my home is mounted.

I need to do this because I keep a lot of files outside of my home directory (/home/robert) in an unencrypted location (/home/unencrypted) in order to maximise performance, but I need to be able to expose all my files in a single Samba share, which isn't possible with symlinks. So I want to mount /home/unencrypted on /home/robert/unencrypted.

Thanks in advance.

---

### Post by sioxs on 2013-08-06
The reason system links won't work in Samba from your home directory is that you don't have the linked file within a share directory.
If you want to mount to a new location to be accessed do:
$ mkdir /your/path/to/folder  // for the new mount point
# mount /old-dir /new dir
use $ man mount  // for more details

Peace!
sioxs
*"if we did all the things we are capable of doing we would literally astound ourselves"*

---

### Post by halfbeing on 2013-08-06
Thanks for replying.

I'm sorry that I wasn't very clear. What I meant was how can I get this nested mount to happen automatically so that it is already set up when I log in?

---

### Post by sioxs on 2013-08-06
If your folder resides on a separate partition you need only enable auto mounting when the system starts and your created "empty" folder should point to the correct location   once you login.
Alternatively you can still add a line to your /etc/fstab file which gets parsed again once the encrypted drive mounts and your user space gets loaded
$ sudo echo "/mount-point /new-mount-location  defaults  0    0" >> /etc/fstab
if it still doesn't work for you there is a way to add the mount to your startup scrips when you login but other than creating a small script to run at login the location for those startup scripts escapes me at the moment.  ~/.bash_login ? (if it exists) or ~/.profile ?
see /usr/share/doc/bash/examples/startup-files for examples. 
 the files are located in the bash-doc package.
 
Hope that helps
Peace!

---

### Post by halfbeing on 2013-08-06
Thanks again for the suggestions.

I tried adding the line to fstab, but it didn't work, but then I discovered that there is in fact a way to get Samba to allow symlinks out of a share, which is what I was hoping to be able to do in the first place :)

---

