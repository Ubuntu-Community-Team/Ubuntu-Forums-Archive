---
title: "OS Issues/Multi-Problem (Nasty Stuff)"
date: 2018-02-12
forum: General Help
---

### Post by agodby1991 on 2018-02-12
wynd0 here,
The solution is below a few comments in this thread. Good luck!


Hello Ubuntu community. First of all, ya'll the best. Okay, so this problem has been driving me up a wall for days. I am convinced it's just my lack of understanding of basic mechanismns, however the symptoms here have kind of snowballed and I'm stuck at a point we're booting into Ubuntu fails. 

**All I want to do is go back to Ubuntu** and go along my Merry Little way with my fuzzy dog Toby, but...

Here is all the facts...

1. Dell Inspirion AMD64 Laptop originally with windows 8.1 
[M# M531R - 5535
Also given M# P28F]

In case it matters:
-Was running Gnome Desktop Environment
-8Gb ram..
-1.7gHz AMD quad-core 64-bit...

2. Ubuntu Budgie 16.04.3 was the ONLY OS installed. (removed windows- however, 931 gb of 1TB after multiple formats would suggest a hidden recovery partition??)

3. Everything was perfect until installation (via github i believe) of katoolin, then apt-get update...

4. PC began to get stuck in desktop environment login loop. Noticed background went back to default picture. my password would work, dark screen for a moment (as if it worked) then, back to login screen.

5. The problem then became in the boot init, the error message i was getting is, missing isolinux.bin, and it would fail.
(Why would it even ask for something it does not need to boot?)

6. Bootable usb's are of no effect, I've even tried using Windows 8 recovery disks to no effect. 

7. The only two accessible environments are the BIOS from the Dell manufacturer, and if I insert the Windows recovery disk I can get to a command shell however without being wrapped in an operating system (a full OS) I am very limited with what I can do, no?

+---CURRENTLY STUCK AT BLACK SCREEN AFTER MFG SPLASH SCREEN. IT JUST SHOWS THE FLASHING UNDERSCORE---+

+---Also, i noticed after this point it was only booting a Kali GNU/Linux Rolling..... I could not get it to revert using the ctl alt f3 to access command line.. ---+

8. WHAT SKILLS/STUFF THAT I HAVE RELEVANT TO SOLVE THIS: 
I have the ability to remove the hard drive and access it from a rooted Linux system in order to do any sort of manual configurations, I also can solder into Hardware connections very basic nothing too crazy limited skill. I have a fantastic little dog named Toby who loves to run, and I also have my Dell service tag but I do not have my Windows product ID.
Also: Raspberry Pi 3 B....running Debian and gnome...

(((I also refuse to pay the Dell service cost for the answer to this problem I believe that those types of companies horde proprietary information and software for the sole purpose to collect on profit which I don't agree with obviously)))

If anyone can please please please help I will be more than happy to upload pictures and do anything I need to do to solve this problem but I'm really really poor right now and I have only this laptoper to work with..

Final thought: I also booted a virtual PC with exact copy of working OS before install of katoolin and apt-get update..... i can resimulate to failure & break it down but how TF do i fix this?? Haha its above my paygrade...

Thanks Ubuntu family 
Yours Truly,
wynd0

---

### Post by oldfred on 2018-02-12
I believe katoolin is some sort of python script to install Kali tools.
Not part of Ubuntu, so not sure if compatible or not.

Most suggest using Kali as a live installer, it really is not intended to be installed.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by oldos2er on 2018-02-12
> Everything was perfect until installation (via github i believe) of katoolin, then apt-get update...

So you didn't see the warning on [https://github.com/LionSec/katoolin](https://github.com/LionSec/katoolin) *not* to run apt update until you remove the Kali repositories? Mixing repositories for two distinct distros is nearly always a recipe for disaster.

---

### Post by agodby1991 on 2018-02-12
No, i did not. I understand i messed that one up, lol sometimes i have to learn the hard way... but resolutions are in order sir. Haha

Edit : this is why i asked for help

---

### Post by oldos2er on 2018-02-12
A reinstall of Ubuntu Budgie would surely fix it, but you might want to wait for someone knowledgeable about katoolin to reply.

---

### Post by agodby1991 on 2018-02-12
> **oldos2er said:**
> A reinstall of Ubuntu Budgie would surely fix it, but you might want to wait for someone knowledgeable about katoolin to reply.

Agreed. But how? bootable usb doesnt work

---

### Post by oldos2er on 2018-02-12
Does your computer use MBR or UEFI?

---

### Post by agodby1991 on 2018-02-12
I can boot legacy or UEFI

---

### Post by oldfred on 2018-02-12
New UEFI systems have fast boot as an UEFI setting. That assumes no system change and immediately starts system booting.
You usually then do not have time to press any key.

Often then a full cold boot will force UEFI to go thru its full start up checks and give you time to press key(s) to get into UEFI or into UEFI boot menu to boot flash drive.
You have to turn power off and hold power key for 10 seconds or more to drain all power. If laptop remove battery first.
Some have had to remove coin battery on motherboard or jumper pins on motherboard. Note that resets UEFI settings, you you have to turn fast boot and Secure boot off again. And any other settings also.

---

### Post by agodby1991 on 2018-02-14
Hello Ubuntu family! wynd0 here. Toby and I are ever so pleased to present the solution for this to anyone else who may incur the wrath of login loops/self stupidity. Hahaha 

The Solution: 
After removing the internal hard drive, resetting the CMOS, hooking up the drive to another Ubuntu system and using dd to reformat, i was able to successfully boot into dell recovery disk i created to reinstall sys bios, then loaded an ububtu usb drive to reinstall. I hope this helps, message me if you have a similar issue. I will do my best to help resolve.

Good Day Gentle Humans
regards,
wynd0

---

### Post by oldos2er on 2018-02-14
Please mark the thread "Solved" under Thread Tools at the top of the page. Thanks for posting the solution!

---

