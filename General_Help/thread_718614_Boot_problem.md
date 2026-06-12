---
title: "Boot problem"
date: 2008-03-08
forum: General Help
---

### Post by hhpeter on 2008-03-08
I have dual boot winxp and ubuntu.I don't know what I did the last time but now when I start the laptop grub comes ok if I go winxp everything boots ok but if I choose ubuntu I have this error:

[I][I]* checking file systems.....
fsck 1.40.2 (12-jul-2007)
fsck.ext3:Unnable to resolve "UUID=619cad3e......
fsck died with exit status 8

File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable
Please repair the file system manually.
*A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash:no job control in this shell
bash:groups:command not found
bash:lesspipe:command not found
bash:Command:command not found
bash:The:command not found
bash:dircolors:command not found
bash:Command:command not found
bash:The:command not found
root@peter-laptop:~#_[/I][/I]

If I press CTRL+ALT+DEL ubuntu boots ok but I don't see winxp partition anymore like before I guess its not mounted I'm not that good wit linux ...I tried to restore grub but nothing changes ....what should I do get rid of that error?

---

### Post by Rytron on 2008-03-08
try a [hirens]("http://www.9down.com/Hiren-s-BootCD-v9-4-Incl-Keyboard-Patch-22256/") boot cd. they are free to download. first ensure that you can boot from a cd. more than likely you can just pop the cd in and your pc will detect it.
they contain tools such as boot managers.
be careful though - before trying to use these boot manager tools - BACK UP ALL YOUR DATA first.

hope this helps.

---

### Post by hhpeter on 2008-03-09
I solved my problem found the solution here
[http://ubuntuforums.org/showthread.php?t=719406](http://ubuntuforums.org/showthread.php?t=719406)
just needed to delete the sda3 entry in /etc/fstab cause I dont have it anymore...deleted using gparted

---

