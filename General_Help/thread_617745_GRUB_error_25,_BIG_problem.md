---
title: "GRUB error 25, BIG problem"
date: 2007-11-19
forum: General Help
---

### Post by 127.0.0.1 on 2007-11-19
Yes hello 127.0.0.1 here and i have a big problem with grub and being that i cant boot. my computer takes like 5 min to load grub, than grub takes like another 5 min to load, and it gives me a error 25. 

i think i can solve this with a simple fdisk /mbr command but i dont see a command line anywere? can someone please help me! thank you :)

---

### Post by LinuxGuy1234 on 2007-11-19
> **127.0.0.1 said:**
> Yes hello 127.0.0.1 here and i have a big problem with grub and being that i cant boot. my computer takes like 5 min to load grub, than grub takes like another 5 min to load, and it gives me a error 21. 

i think i can solve this with a simple fdisk /mbr command but i dont see a command line anywere? can someone please help me! thank you :)

Sounds like **2** problems.
1. GRUB depends on two things: the BIOS and the memory. Try upgrading it.
2. Modify your grub.conf file (the hard way). First press ESC and press "e" 2 times. Then fix these lines:
root
kernel
initrd
and press "b". Then run (in a terminal):
```
sudo nano /boot/grub/grub.conf
```

and fix root, kernel and initrd and save it and exit and tada!

If this doesn't help, please file a bug in Launchpad under the package grub.

---

### Post by 127.0.0.1 on 2007-11-19
> **LinuxGuy1234 said:**
> Sounds like **2** problems.
1. GRUB depends on two things: the BIOS and the memory. Try upgrading it.
2. Modify your grub.conf file (the hard way). First press ESC and press "e" 2 times. Then fix these lines:
root
kernel
initrd
and press "b". Then run (in a terminal):
```
sudo nano /boot/grub/grub.conf
```

and fix root, kernel and initrd and save it and exit and tada!

If this doesn't help, please file a bug in Launchpad under the package grub.

can you be more specific as to HOW to fix thr root, kernel, and initrd lines please? Thanks for the suggestion.

---

### Post by 127.0.0.1 on 2007-11-20
heres some more information that might help, i am unable to mount my internal HDD, according to the error message windows didn't shutdown correctly, i remeber my mom was using windows when it suddenly crashed and had to turn off the computer with the power switch. This might explain why i am getting this grub error.

question is, how to fix it...:(

---

### Post by kellemes on 2007-11-20
You could try [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), it can fix Grub in most cases.. Download/Burn/Boot..

Some links that *may* be helping since this seems to be a rather strange problem..
[http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/]("http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/")
[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html]("http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html")
[http://www.mepis.org/node/5782]("http://www.mepis.org/node/5782")

But try SuperGrubDisk first.. it can't hurt an unbootable system right? :popcorn:

---

### Post by 127.0.0.1 on 2007-11-20
> **kellemes said:**
> You could try [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), it can fix Grub in most cases.. Download/Burn/Boot..

Some links that *may* be helping since this seems to be a rather strange problem..
[http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/]("http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/")
[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html]("http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html")
[http://www.mepis.org/node/5782]("http://www.mepis.org/node/5782")

But try SuperGrubDisk first.. it can't hurt an unbootable system right? :popcorn:

thouse links are people with error 21. i am getting error 25. but i will try thr Super GRUB Disk thanks :)

---

### Post by kellemes on 2007-11-20
> **127.0.0.1 said:**
> thouse links are people with error 21. i am getting error 25. but i will try thr Super GRUB Disk thanks :)

Your first post talks about error 21.

---

### Post by 127.0.0.1 on 2007-11-20
> **kellemes said:**
> Your first post talks about error 21.

crap, i ment 25 terribly sorry =$

---

