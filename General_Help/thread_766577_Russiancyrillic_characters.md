---
title: "Russian/cyrillic characters"
date: 2008-04-25
forum: General Help
---

### Post by Weaseal on 2008-04-25
So yesterday a friend gave me an mp3 CD with international music on it...some of the file names were written in Cyrillic (the alphabet used in Russian and most Slavic languages).

On Windows, all the file names showed up fine, however when I rebooted into Linux, all the Cyrillic characters came up as question marks, and I cannot access the file in any way -- can't copy, modify, or even rename it.

How do I properly add such support?

Thanks.

---

### Post by BryanKeith on 2008-05-12
Any luck with the Cyrillic fonts?  When I look at a windows share folder with the GUI, I see the Cyrillic fonts fine.  But when I use the terminal, the fonts appear as questions marks (???) as you describe.

Anyone have any ideas?

Bryan

---

### Post by BryanKeith on 2008-05-13
For me the problem ended up being how I mounted the drive with Samba.  I added "iocharset=utf8", and now the Cyrillic characters show up in the terminal.  The line in /etc/fstab looks like this:

//machinename/projects /mnt/projects smbfs
auto,gid=sambashare,uid=username,file_mode=0770,dir_mode=0770,iocharset=utf8,rw
0 0

I'm curious how drives are mounted in the GUI.  Is there a way to access those drives in the terminal without having to mount them (again)?

Bryan

---

### Post by Weaseal on 2008-05-13
Thanks for the update. I no longer have said CD but if I get it/another like it I will give your solution a shot :)

---

