---
title: "Wine Configuration Problem"
date: 2006-10-22
forum: General Help
---

### Post by jasjason on 2006-10-22
Hi guys, i need help here. after i have install wine and i run the winecfg for the first time. I cannot open the audio tag. It also give me this following error:

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c29db60 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

After "starting debugger", my whole winecfg just freeze there. may i know what is the problem and how do i fix this issue? Thanks in advance.

---

### Post by joshgtv6 on 2006-10-22
EDIT: This problem was solved for me in the following thread but I'll leave my initial problem so others can see it and then venture to this thread for a solution. 
[http://ubuntuforums.org/showthread.php?p=1650580#post1650580](http://ubuntuforums.org/showthread.php?p=1650580#post1650580)


when i click the audio tab in wine i get this error.  

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/jpeifley/.kde/socket-jpeifley-desktop.
can't create mcop directory
jpeifley@jpeifley-desktop:~$

---

### Post by jasjason on 2006-10-23
Hi thanks alot for the reply and your post means alot to me now. Cause i now have more solution to the problems i faces now.

---

### Post by mad_alfred on 2007-02-11
> **joshgtv6 said:**
> EDIT: This problem was solved for me in the following thread but I'll leave my initial problem so others can see it and then venture to this thread for a solution. 
[http://ubuntuforums.org/showthread.php?p=1650580#post1650580](http://ubuntuforums.org/showthread.php?p=1650580#post1650580)


when i click the audio tab in wine i get this error.  

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/jpeifley/.kde/socket-jpeifley-desktop.
can't create mcop directory
jpeifley@jpeifley-desktop:~$

Hi, even though i gave the command:

sudo mkdir -pv /home/chris/.kde/socket-chris-desktop

I still receive the following error message:

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: Is a directory
*** glibc detected *** free(): invalid pointer: 0x7c06b860 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

and eventually winecfg freezes :(

Am i doing something wrong?:confused:

---

### Post by jasjason on 2007-02-13
well i not sure what u have gone wrong but i solve the problem base on the link given by joshgtv6. You may want to go and take a look to that.

[http://ubuntuforums.org/showthread.php?p=1650580#post1650580](http://ubuntuforums.org/showthread.php?p=1650580#post1650580)

---

