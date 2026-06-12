---
title: "Canno't access to my own /home files! - Permission problems?"
date: 2008-02-24
forum: General Help
---

### Post by Diego10 on 2008-02-24
Suddenly I am noticing that I am not able to modify files in my own home folder. I try to move or delete a file and Nautilus says I do not have permissions.

"...Cannot move "/home/dieg...S_FTP.LOG" to the trash because you do not have permissions to change it or its parent folder..."

Even from the terminal, where I can clearly see that I am the owner of the file it blocks the access:


diego@homero:~/Documents$ ls -o WS_FTP.LOG
-rwxrw---- 1 diego 129 2008-02-24 19:53 WS_FTP.LOG
diego@homero:~/Documents$ rm WS_FTP.LOG
rm: cannot remove `WS_FTP.LOG': Permission denied

What might be happening????  BTW, I can still move/delete issuing sudo before the command.

Help appreciated!
Thanks,
Diego

---

### Post by bettlebrox on 2008-02-24
U didn't make any changes to /etc/passwd, /etc/group or /etc/shadow by any chance?

It could one of many things, maybe permissions got messed up somehow, or there's something wrong with your drive ...  

First I'd look at the full permission of the files:
ls -l WS_FTP.LOG

Then check to see your userID to make sure it's hasn't changed somehow:
[INDENT]id[/INDENT]

Make sure none of the disks are full:
[INDENT]df -h [/INDENT]

Check to see how the disk is mounted:
[INDENT]mount | grep home[/INDENT]

Provide the output of those commands and let's see if we can figure out what's up! :)

---

### Post by skillet on 2008-02-24
you probably wrote those files to your home directory using a program that was running as root thus the file is owned by root.

---

### Post by Diego10 on 2008-02-25
First of all thank you everybody for your help!

I did not make any change (at least not that I am aware of)  to /etc/passwd , /etc/group/ or /etc/shadow directories.
Nonetheless, the folder containing the file I tried to remove (/home/diego/Documents) and all the folders contained in it had the user (diego) write flag disabled. I do not know exactly how this flag got changed but the case is that to fix it I started nautilus with root privileges (I am a still learning how to effectively use the terminal commands) and changed the permissions associated with my user (diego). Now everything seems to work fine again.

Ubuntu is still running with some glitches because my crappy Acer Aspire doesn't get along very well with some power management drivers. When I turn off my laptop I am seeing a 'System halted' message and I have to press the power button to turn it off completely. I am wondering if that procedure might have caused this permission mess up.

Anyway, thank you so much again!
Diego

---

