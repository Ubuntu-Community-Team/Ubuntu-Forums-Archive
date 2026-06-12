---
title: "Unable to login"
date: 2007-05-13
forum: General Help
---

### Post by A*p on 2007-05-13
[SIZE="3"]I am no longer able to login to ubuntu edgy eft on my laptop.  Every time I get to the login prompt and enter my details the screen will go blank for about 3 seconds and then show the login prompt again.  I have tried all session options and the same happens for each one.[/SIZE]

[SIZE="2"][background info relivent or not?]
I had not installed anything or made any changes to the system prior to the reboot other than trying to add a firefox extension.  I had noticed firefox acting strange before I decided to reboot though, I am not sure if it is related or not.  Anyway the strange thing it did was loose my search engines list so it would be blank (top right).  The addon to firefox I tried to install was download them all, which I have had installed fine on my other systems.  Firefox crashed and would not relaunch so I rebooted my laptop and now I can not get any further than the login prompt.[/SIZE]

I am able to boot into the recovery mode terminal.

---

### Post by bapoumba on 2007-05-13
hello,
from the recovery mode, run:
```
df -H
```
You may be running out of room.

To clear space on your root (/) partition:
```
# aptitude clean
```
Note that from recovery mode, you are root with a # prompt.

Also see in your /home if you can remove files (look in ~/.Trash also).

When you are done:
```
# reboot
```

---

### Post by A*p on 2007-05-13
I am back up and running, from terminal I started aptitude and found some dependencies that needed resolving.  No idea as to why it would cause such a problem for me, especially since the packages were installed a good while ago, the firefox thing was just a coincidence me thinks.  Also Aptitude showed dependency problems when Synaptic did not.:confused:

---

### Post by ramjet_1953 on 2007-05-13
If the above doesn't do the trick, follow this link, it may help:

[http://ubuntuforums.org/showthread.php?t=375391&highlight=Lost+Password](http://ubuntuforums.org/showthread.php?t=375391&highlight=Lost+Password)

Regards,
Roger :cool:

---

### Post by A*p on 2007-05-13
Thanks bapoumba, you know I think you could be right about running out of room, and me removing a package in resolving some dependencies could have freed up enough space, if more was needed to login.  The laptop was very full at the time with a large trash folder that had not been emptied in a long while.

---

### Post by bapoumba on 2007-05-13
Going back to login screen when trying to login is one of the symptoms for a full partition (either /, /var if separate, or /home). I recall either a spec or a bug report have to set up a pompt with some friendly message when this happens.
Once you know the symptom, its easy to fix. But when you get back to the login screen, and have no clue about it, well, you cannot guess it :/

---

### Post by sdil on 2007-05-13
along ago, my computer also like that but now it is OK. Are you have a 3D / video card on your notebook ? Have you tried login safe mode ( on choosing at boot ). It will go to root mode.:(

---

### Post by A*p on 2007-05-13
Thanks all, the issue is resolved, I am putting it down to a low disk space problem that caused it.

---

### Post by k5787 on 2007-05-13
im having a simialr problem. i was downloading some music and then a little window poped up and it said that disk uasge was full. i reboot and now i cant log in. i used a comand to see what was on the drive and it said that my home was 100% full. how can i access this folder in terminal and delete some files so as to be able to log in. i dont want to reinstall, because i have some real important stuff within this home folder. please help anyone.

---

### Post by bapoumba on 2007-05-14
@ k5787: boot in recovery mode. Be careful, you'll be root. login, you should be in your /home directory.
Look for files to delete.

ls : lists the file in a directory (subdirectories will appear in color).
cd : change directory
cd .. : goes up to parent directory
rm <file_name> will remove the specified file in the current directory. (there are ways to remove a whole bunch of files at a time, but I would not recommend that to you, because if misused, not in the correct directory, not with the correct arguments,  you can end up with a broken system).

Remove only your own stuff, no config files, no system files. Look for big files like videos and such.
```
du -ah | sort -rn | head
```
Will list you the biggest files in current directory. **Do not remove anything starting with a dot** or within a directory which name starts with a dot.

---

