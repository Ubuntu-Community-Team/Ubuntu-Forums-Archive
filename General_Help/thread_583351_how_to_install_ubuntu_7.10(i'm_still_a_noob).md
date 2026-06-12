---
title: "how to install ubuntu 7.10(i'm still a noob)"
date: 2007-10-20
forum: General Help
---

### Post by tomak on 2007-10-20
can some one tell me how to install ubuntu 7.10 step by step....starting from the iso file....-.-'

---

### Post by hooplah on 2007-10-20
You burn the ISO to a blank CD-ROM using nero, or any other program that has these capabilities. Then, you insert the newly-burnt CD into your drive, reboot your computer, make sure your computer primarily boots off from the CD, and then follow throught the simple installer. Good luck!

---

### Post by tomak on 2007-10-20
i've already done that and when i boot(still reading disc) then nothing happend and it's just start the window normaly...

---

### Post by bobyy on 2007-10-20
Hi i don`t know if is the same problem, but oane of my colleague have this simptom...jut hit ALT+F1 after the boot loader "was loaded":)        good luck...

---

### Post by tomak on 2007-10-20
hemmmmmm.....whar do u mean by boot loader "was loaded"/?????

---

### Post by tomak on 2007-10-20
owh....i've alreadysolce the boot prob....and now.....after it boot the dvd that i've just burn it say like this
[DR-DOS]A://
sumthing like that.....owh and i extrac the iso then burn the whole extracted file(sorry for my english)

---

### Post by bobyy on 2007-10-20
I understand ,ubuntu was installed ...yes?
 after you start the computer , the boot screen it will be appear..yes?
 hit ENTER ...and Ubuntu will start to load...
 ii understand fro you this is the last thing what is happening ..yes?
 if its just a black screen hit ALT+F1 ...and it will start if is the same bug   
like on mi friend comp...

regards bobyy

---

### Post by tomak on 2007-10-20
no,yes,no.....hemmmm...i try to reboot wth my iso file then press alt+F1...

---

### Post by maybeway36 on 2007-10-20
Where in the world did DR-DOS come from? Weird...

---

### Post by bobyy on 2007-10-20
Men...after you install Ubuntu restart the comp...but REMOVE the cd...

---

### Post by tomak on 2007-10-20
i still don't know.....-.-'....so sad now...btw i really like ubuntu

---

### Post by LanDan on 2007-10-20
> **tomak said:**
> owh....i've alreadysolce the boot prob....and now.....after it boot the dvd that i've just burn it say like this
[DR-DOS]A://
sumthing like that.....owh and i extrac the iso then burn the whole extracted file(sorry for my english)

you are not supposed to extract the iso
you should burn the iso

---

### Post by tomak on 2007-10-20
how can i finish my instaling if it haven't start yet????

---

### Post by tomak on 2007-10-20
i already burn the iso file in the other disc after reboot it it just start the window normaly

---

### Post by tomak on 2007-10-20
now....back to the real prob....i follow the guide [how to burn ISO image]
>>> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
then i put the cd in again after finish burning, reboot then blablabla ram,bios and stuff
booting CD, an underscore blinking....then nuthing

---

### Post by drs305 on 2007-10-20
Perhaps we should start with the basics.

When you look at the iso cd, do you see a list of folders and files. You should. You should not see one file named *.iso.

Have you verified the checksum of the iso image you downloaded? If you don't know how to do this, there is a windows program called md5sums.exe  If you drag the iso file over the md5sums.exe file in Explorer it will provide you with a checksum that verifies the iso was properly downloaded. If you have access to linux, open a terminal and go to the directory the iso image is in and type:
```
md5sum <name of the iso file>
```
For example:  md5sum ~/Desktop/ubuntu-7.10-alternate-amd64.iso

The codes for the most common gutsy iso's are:

ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso

Here is the link: [http://no.releases.ubuntu.com/releases/7.10/MD5SUMS](http://no.releases.ubuntu.com/releases/7.10/MD5SUMS)

If you still have problems determining the checksum, there are many threads here that can explain it.

If the checksum is correct, next make sure that your computer is set to boot from the cdrom first. Does the computer try to read from the cdrom before it boots from the hard drive (you should hear your cd/dvd player spinning if it does). 

From your last post, it sounds like it is trying to boot from the cd but can't. Making sure you have a good disc is a start.

---

### Post by tomak on 2007-10-20
ok thx 4 the tips.....i'll try that

---

### Post by tomak on 2007-10-20
now here's another prob........every time i downlaod the ubuntu it don;t have the same mdsum....can some one yell me why???

---

### Post by pieisgood4589 on 2007-10-20
OK...... Here's it STEP BY STEP

1. Download the .iso file. Got that? Good.
2. Get some .iso burning software (I'd recommend ultra-iso or nero) and burn the .iso file into a CD
3. Make sure your bios is set to boot directly into the CD (hit F1 or some other combination to enter bios)
4. Hit "enter"
5. Once the graphical desktop is booted, double click the "install" icon
6. Follow the simple installer pop-up
7. Voila! DONE!

good luck! :popcorn:

---

### Post by pieisgood4589 on 2007-10-20
> **tomak said:**
> now here's another prob........every time i downlaod the ubuntu it don;t have the same mdsum....can some one yell me why???
 Try downloading the torrent, or requesting the free CD via Shipit. Torrents tend to be more reliable...
The download could be corrupt from the download off of the server.

---

### Post by tomak on 2007-10-20
i try the torrent download....hope it work....thx

---

### Post by tomak on 2007-10-21
hey i already know what is my prob....each time i download the ubuntu iso i use the download accleter(wrong speeling haha) then after it finish it just a blank icon.early today i download it the normal way then the icon not just blank it had the ultra iso icon......owh and my laptop is intel centrino duo i download the ubuntu-7.10-desktop-amd64 iso....is that correct???

---

### Post by tomak on 2007-10-21
now i got this prob......after rebooting and reading the disc there's many option like start and install ubuntu or sunthing like that and i choose the 1st one(loading linux carnel.if i'm not wrong)then it said up CUP don't support long mode please choose 32-bit blablabla.....help me

---

### Post by pieisgood4589 on 2007-10-21
OK... The AMD64 version of Ubuntu is for AMD machines ONLY. You have a Pentium, so you should have downloaded the i386 version, or the version with the "i" in front of it. Good luck! :popcorn::guitar:

---

### Post by tomak on 2007-10-22
ok......bt my pc is intel centrino Duo

---

### Post by Nunu on 2007-10-22
Centrino, Pentium they all use the i386 package. The AMD64 is for 64 bit AMD processors. and will NOT work on an Intel based machine.

---

### Post by tomak on 2007-10-22
owh....lol just wastimg my time downloading it.....thx 4 da tips Nunu....-.-'

---

### Post by pieisgood4589 on 2007-10-22
LOL. Post back with your results! :popcorn::guitar::lolflag:

---

### Post by tomak on 2007-10-23
hey...it works....thx....people. and my tips is 
if ur pc is 32 bit download = Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
and is 64 bit = 64bit AMD and Intel computers
don't get confuse if the other one say intel computer......hope u understand

---

### Post by pieisgood4589 on 2007-10-23
lol this is ironic. You are posting our facts and tips as yourself? I'm sorry I ever helped you.:mad:

---

### Post by songshu on 2007-10-23
> **pieisgood4589 said:**
> lol this is ironic. You are posting our facts and tips as yourself? I'm sorry I ever helped you.:mad:

and what are you doing? you were born as a natural?

---

### Post by pieisgood4589 on 2007-10-24
NO. I explored on my own. Everything that I post is what I KNOW. I'm not a thief. :KS

---

### Post by DagMan on 2007-10-24
Hi
> and is 64 bit = 64bit AMD and Intel computers
Yes, If you have an intel processor that is built for 64 bit execution, then then the AMD 64 edition will run run on the machine.  A couple of people have stated in the thread that you need an AMD processor to run this.  AMD 64 has become a sort of generic term and the naming is for all the x86_64 processors [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)
This includes some pentium 4's and many intel architectures after that.  Most if not all core 2 duo processors are 64 bit capable and will run either 32 or 64 bit operating systems.

Edit:  I think I was a bit confused by the thread authors bad english.  I was trying to clarify and didn't see he was setting people up to be mocked.  Sorry bout that.

---

### Post by tomak on 2007-11-15
-.-'.....

---

