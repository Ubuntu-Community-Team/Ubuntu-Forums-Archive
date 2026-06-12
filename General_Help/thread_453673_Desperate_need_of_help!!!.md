---
title: "Desperate need of help!!!"
date: 2007-05-24
forum: General Help
---

### Post by beadwindow2001 on 2007-05-24
Thank you first off for any assistance you can give me. I was trying to install the most updated version of Ubuntu on my brother's laptop. Unfortunately something is going wrong and I have searched everywhere for help. When I boot up the computer it gives me a "NTLDR" error. I was trying to make it a dual bootable computer with XP on the hard drive as well. That is just what I have been able to see so far. Any questions please let me know!

---

### Post by franck3d on 2007-05-24
it sounds like grub is not setup properly, and windows is trying to load but it's boot loading was removed by trying to install grub.   not sure of the solution, off hand 
but...

[fix to boot in windows]("http://askbobrankin.com/fix_mbr.html")

you might be able to boot from the Ubuntu CD and then fix grub from there.
good luck, and don't worry about it too much, it's fixable.
I'm sure you will get plenty of help around here.

---

### Post by beadwindow2001 on 2007-05-24
Thank you. One onter thing i forgot to add was that it is not allowing me to boot from the internal CD drive. I have to have an external CD drive to boot any CD.

---

### Post by threadmetal on 2007-05-24
The CD boot problem is either hardware or BIOS related -- probably the internal CD is set as lower priority than the HD as a (useful but annoying) security feature. If there's a prompt similar to "F12 to change boot order" you can use that, otherwise you have to change it in BIOS setup.

As for the NTLDR error, I have two educated guesses.

My first thought is that during the installation process, it sounds like you installed the Linux bootloader ("grub") to the boot sector of the installation partition, not the Master Boot Record for the drive.

The net result: the Windows boot loader (NTLDR) is still in the MBR, and last it knew, windows was the whole drive. Since you probably resized the old windows partition, things got moved around, and NTLDR doesn't know what's going on anymore.

if that is the problem, installing grub to your MBR should fix it: I'm not sure how to go about that from a non-booting system, so keep pounding the forums (fora?) for that info.

On the other hand, if you *did* install grub to your MBR (you get the grub boot screen and *then* the NTLDR error after selecting windows) either 

A: (very unlikely) the resize was not completed properly and Windows is now AFU
-or-
B: (more likely) the grub menu file (/boot/grub/menu.lst in your linux partition) is not configured quite right.

if *that* is the problem, the fix is to open /boot/grub/menu.lst (I recommend doing this from a terminal using "sudoedit /boot/grub/menu.lst") and make sure the section for the windows partition reads as follows:

<snippet>
title Really Unstable But Expensive Operating System, Public Beta Version 5
root **(from your problem description this line should be correct)**
chainloader +1
</snippet>

Again, without any more info, I can't say for sure, and I could be completely wrong. 
Nonethless, hope this helps!

---

