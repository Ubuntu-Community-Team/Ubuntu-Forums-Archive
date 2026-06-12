---
title: "Ubuntu Bootup Problem"
date: 2008-06-10
forum: General Help
---

### Post by SteeleCratos on 2008-06-10
Hey everyone here at Ubuntu forums! I'm a new member here, but I've been around the forums for a while as a guest, checking out all the different forums for a while before signing up, and I'm impressed that ubuntu has such a large community! I'm glad that I'm a member of this forum, and I hope to contribute to the growth of the OS in the future. 

But anyways, now to get to the root of why I'm posting. I've been curious with Ubuntu for a while now, but having barely any experience with partitioning, gave up for a while. But then a friend recommended using Wubi to try out ubuntu. I downloaded it from wubi-installer.org onto my desktop, and the installation ran rather smooth, despite it being somewhat slow. (took around 10 minutes for the files to be downloaded). After a while, it told me to reboot. 

So I did, and i got to the BIOS section where you choose which OS to boot up in. I chose Ubuntu, but now this is where my problem lies. The screen just says this:

**. . . upper memory. . . **

What does this mean? It's not doing anything, or booting up to ubuntu. It just remains stuck on this, even for 3 hours!

What's going on? Is my system too weak for ubuntu, or is there something wrong with wubi?

-Peace-

---

### Post by ago on 2008-06-10
[https://wiki.ubuntu.com/WubiGuide#head-6df166f107af3217e325fbc219745868b6612c75](https://wiki.ubuntu.com/WubiGuide#head-6df166f107af3217e325fbc219745868b6612c75)

---

### Post by SteeleCratos on 2008-06-10
I looked through the topic, and I tried replacing the stuff in the zip file into the folder, and I tried inputting the commands at the GRUB> command line, but it gives me ERROR 15. I'm sure that I don't have any multiple drives, or that anything is corrupted or anything else of the like. 

Should I try to run wubi from the LiveCD?

-Peace-

---

### Post by ago on 2008-06-11
error 15 means that grub worked. so you are beyond the original error.

see the next section in the wubiguide

---

### Post by SteeleCratos on 2008-06-11
Ok, I followed the instructions stated, and I replaced all files with the ones in the zip file, and etc. etc. And I am proud to say that I don't get the upper memory message anymore. 

But now I get a command line that's telling me to input a command with the starting line grub>

I already looked through the other topic that's linked in the wiki, but it doesn't work. 

```
find --set-root /menu.lst
configfile /menu.lst
```

I tried to input this code in, as detailed here:[http://ubuntuforums.org/showpost.php?p=4998884&postcount=40]("http://ubuntuforums.org/showpost.php?p=4998884&postcount=40"), but it keeps giving me:

**error 15: file not found**

Should I put in menu.lst in the root directory?

-Peace-

---

### Post by ago on 2008-06-11
copy c:\ubuntu\winboot\menu.lst to c:\

---

### Post by SteeleCratos on 2008-06-11
Did that. Now I got a NEW error message (WHEN DOES IT END?!)

It keeps blinking on and off, so I can't really make it out, but from what I can get, it says:

**Warning: Unrecognized partition table for drive 81. Please rebuild it using a Microsoft-compatible FDISK tool(err=28 ).**

Wow. I never thought that installing Linux could be this hard...

-Peace-

---

### Post by ago on 2008-06-11
The warning is normally not problematic. Try to press esc after Ubuntu and select one of the other options.

---

### Post by SteeleCratos on 2008-06-11
It won't let me do that. It's basically the same thing going on as the . . . upper memory . . . message, I guess.

I tried pressing INSERT multiple times, and it got out of it, and started giving me details as to the problem, but I have no idea what any of it means. 

So should I take out menu.lst from the C:\ drive and try selecting a different option from the menu after ubuntu?

-Peace-

---

