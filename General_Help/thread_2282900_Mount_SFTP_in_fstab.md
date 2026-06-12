---
title: "Mount SFTP in fstab"
date: 2015-06-17
forum: General Help
---

### Post by CaptainMark on 2015-06-17
Can you mount SFTP from fstab, I tried a quick internet search but I just hit loads of posts about mounting sshfs in fstab which is what I'm doing now but it doesn't work well with symbolic links, SFTP works great so I'd rather use that if poss.

I'm excruciatingly aware that I'm being really dumb with this, soon enough something will click and I'll realise I've said something stupid.

Regards
Mark

---

### Post by CaptainMark on 2015-06-19
Don't like bumps but stuff can get buried here easily so, BUMP

---

### Post by Holger_Gehrke on 2015-06-19
It's not quite clear to me what the problem is; sshfs is fuse (filesystem in userspace) using SFTP for transport. Or are you using shfs (mind the missing second 's') which is an older kernel-module which starts ssh itself and doesn't use fuse. In what other way are you mounting an SFTP-server ? In the filemanager using gvfs (gnome virtual file-system) ? And in what way do symlinks fail with sshfs ?

---

### Post by CaptainMark on 2015-06-20
The problem about symlinks is that when I mount a directory from my server (remote) to my desktop (local) home folder (using sshfs) that any symlinks on the remote directory seem to point to the same directory (if it exists) on the local machine, not the remote machine. So on the server the symlink /home/mark/Documents points to /mnt/data/mark/Documents but when I mount server:/home/mark on my desktop using sshfs the symlink shows as a broken link saying the destination folder does not exist, presumably because /mnt/data/mark does not exist on the desktop. Im using the command
```
sshfs server:/home/mark /home/mark/server
```

However if I attempt to do a similar thing but instead go to the menu in my file manager (nemo) file>connect to server, select ssh as as connection option and fill in all the appropriate info for my server then the entire home folder for my server will correctly mount in desktop:/home/mark/server and symlinks will correctly link to server:/mnt/data/mark/Documents
It is my belief that this method uses sftp but I'm not an expert, but as you can see this method just works how I want it so I was asking how to mount it automatically on boot.

Regards
Mark

---

### Post by Holger_Gehrke on 2015-06-20
According to the [manual]("http://linux.die.net/man/1/sshfs"),sshfs has an option '-o transform_symlinks' that changes absolute symlinks on the server to relative ones. This *should* fix your problem if I understand it correctly.
Alternatively you could try to use 'gvfs-mount' for mounting; this is a command line tool that uses the gnome virtual file system just like your file manager does. Documentation for gvfs-mount is somewhat sparse, and doesn't go far beyond the output of 'gvfs-mount --help'. To the best of my knowledge, you can't use gvfs in the fstab, so you'd have to put the mounting command into into some kind of autostart script.
There is also a graphical tool named 'gigolo' that should be capable of automounting bookmarked virtual filestems.

---

### Post by CaptainMark on 2015-06-20
Well there's that click that I was talking about, amateur hour, I forgot to check the man page.
The option I needed was -o follow_symlinks
Thanks very much for your help.

Regards
Mark

---

