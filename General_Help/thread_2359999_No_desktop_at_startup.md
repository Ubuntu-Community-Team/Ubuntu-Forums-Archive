---
title: "No desktop at startup"
date: 2017-04-30
forum: General Help
---

### Post by hbbco on 2017-04-30
I am using ubuntu studio xenial with 16 gb ram and one samsung SSD 250 GB. Several days ago when I wanted to work with the computer, the system failed, I do not have the desktop and I only have a command console that asks me for the login and the password. The file system it mounts is read-only. The computer runs smoothly with the grub, if I let the normal time pass without pressing any key, it happens what I described above. But if I press enter I get errors from sysmctl and the network interface, getting the same screen. I tried to correct the problem with a program to solve grub problems, believing they were there, but the problem persists. The kernel is 4.4.0-75-low-latency. I apologize for my English but is not my current language.

---

### Post by Bashing-om on 2017-04-30
hbbco; Hey ...

As we have:
> 
The file system it mounts is read-only. 

Let's "presume" that the system is protecting it's self from further damage.
We can try a simple file system check/repair :
You can also force a file system check at boot time by passing fsck.mode=force, as a kernel parameter. This will check every filesystem you have on the machine.

Boot to the grub boot menu, with the latest kernel selected as boot, press the 'e' key for edit mode -> boot parameter screen.
Here arrow down to the line starting with linux, and arrow across to 'quiet splash' . replace quiet splash with the term fsck.mode=force.
Key combo ctl+x to continue the boot process. Let the file system check complete, and attempt now to log into the system.

What is the result of logging in ?

[INDENT][INDENT]maybe all good now ?
[/INDENT][/INDENT]

---

### Post by hbbco on 2017-05-05
Thanks for your answer. The problem was an update that changed the fstab file in a very strange way.

---

### Post by QIII on 2017-05-05
I am curious:  in what strange way did an update change your fstab?

---

