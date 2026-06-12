---
title: "error: unknown filesystem"
date: 2014-01-02
forum: General Help
---

### Post by karasuman on 2014-01-02
I am painfully typing this on my PS3, for the record.

I knocked my computer over and had to restart it. I get the above error with a "grub rescue" command prompt. 

All of the solutions I've found online assume that I have a Windows 7 disc, a live cd, or both.  I have neither.

My initial setup was a partition for each, but I screwed up an upgrade and destroyed it.  I just downloaded the image to burn a few days ago. 

Please help me.  The only internet access I have now is my PS3, and typing with a controller is just bad.

UPDATE: I have successfully booted into my Windows 7 partition, using the steps described below.  But I don't know how to automate this process... how do you program a pilgrim to give up their Halloween candy?  Really, though, I have to go through the steps when I'm just logging on to check my email--if my computer turns off or shuts down, it's just me again.

---

### Post by jeanjd63 on 2014-01-02
Hello,

You can try this :
You boot on a LiveCD, you find your partition / by the commande :
[B]sudo  fdisk  -l
[/B]The partitions ubuntu have a ID=83
you do :
[B]sudo  fsck  -f -y  /dev/sdXY 
[/B]Where sdXY is to replace whith the good partition.
Then you reboot.
Bye

---

### Post by karasuman on 2014-01-02
I don't  have a live CD.  IfIget one, how will I know which partition is bad?  I also would like to get back into Windows 7.

---

### Post by karasuman on 2014-01-02
And how do I boot from a CD while my computer is giving me this error message?  It fails to respond to most linux and even DOS commands.

---

### Post by claracc on 2014-01-02
To boot from live CD you have to set into your BIOS. So you will enter into BIOS (the combination of keys are displayed when you turn on your computer), and then set to boot first from CD.

---

### Post by karasuman on 2014-01-02
I immediately get the error.  There no longer is a loading at all.  I see anything loading other than the error.

---

### Post by jeanjd63 on 2014-01-02
When you have install ubuntu, you have boot from a cd/dvd no? 
Can you put this cd/dvd in the dvd reader and reboot your computer.
If it is ok, you choose "try" and then you open à terminal (ctrl+alt+t) and you do commands of post #2

---

### Post by karasuman on 2014-01-02
I appreciate the help, but neither of your weapons work for me.  My computer would not recognize a CD and let me boot from it--I tried with an old 11.4 disc I still had.  My ubuntu won't load, and I keep meaning to reinstall, but, for some reason, I don't get around to it.

But the GOOD news is that I found a solution:

(1) **ls**: this gives you a list of what your computer thinks it has on it.  Even though I have a Windows partition, I did not see any partition labeled as msdos.  If you do, it's probably Windows.  I only had numbers, and not even all consecutive numbers: I had (hd0), (hd0,1), up through (hd0,8) but without (hd0,2) or (hd0,7).  I have no idea why.

(2) try **ls** on each partition, eg. ```
ls (hd0,X)
```.  Ideally, you get one that stands out.  For me, the difference between the responses changed from "does not exist" to "unknown format" for two partitions.  One of the two "unknown format" partitions allowed me to get back to Windows.  (Also, the lack of a space after the comma is important.  You want exactly (hd0,X).)

(3) use the following commands, with X as your partition:
```
set root=(hd0,X)
set prefix=(hd0,X)/boot/grub
insmod normal
normal
```

Unfortunately, step (3) is when you find out that you picked the wrong partition in step (2).  For me, "insmod" was declared to not exist.  If that happens, I guess you try another partition?  That doesn't seem to cause any harm, so you can try this with every listed partition until one works.  I broke my Ubuntu installation by downloading the install instead of doing a clean install, but I imagine that this would still work, because I wasn't booted directly into Windows--I got the list of OSs on my computer and had the ability to choose one of them.

I do not know why all of (3) works, but I'm glad that it does.  If someone can shed some light on exactly what "normal" does (I assume it's a program from ubuntu, which means this wouldn't fix the error on a system without an ubuntu partition?), that would be elucidating.

---

