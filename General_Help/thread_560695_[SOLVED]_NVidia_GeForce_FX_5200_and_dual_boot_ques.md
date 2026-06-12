---
title: "[SOLVED] NVidia GeForce FX 5200 and dual boot question"
date: 2007-09-26
forum: General Help
---

### Post by JersyDvl on 2007-09-26
Hello, wonderful community here. I recently upgraded my old 80gb hard drive to 160gb and wanted to partition and install Ubuntu on one and XP on the other (i have Dapper installed on my inspiron 1100 and love it). My problem is, i think ubuntu has a problem with my graphics card (Nvidia Geforce FX 5200, not top of the line, but just fine for the few windows games I do play). When I try to load up a live CD it wont load. When i try with the Alt instal cd, i can install the OS, but when i start the computer the load bar hangs at roughly 25% through the bar. When i go into the bios and set it to use the onboard graphics and switch the moniter (Samsung SyncMaster 225BW 22" widescreen 1680c1050) to the onboard plug i can get into ubuntu just fine. I tried installing the Nvidia drivers from this setup and switching back to the fx 5200 afterwards but the problem remains. 

I have searched the forums and found pieces of answers here and there, but nothing really helped as a whole. What i want to do is have both Ubuntu and WinXP boot up using the Nvidia card without having switch the bios settings and plug every time.

My setup is:
Asrock 775i65GV motherboard with latest bios
1500mb ram
2.8ghz Pentium 4
160gb Seagate Harddrive for OS's Games and Applications
60gb Seagate Harddrive for Music, Movies and other multimedia
NVidia GeForce FX 5200 PCI Graphics card
Intel 82865G Integrated Graphics card

Thank you in advance. Im really looking forward to having Ubuntu up and running on thie machine, and definately plan on moving exclusively to it once I am comfortable enough with it that i wont need Windows anymore, but until then I really need to dualboot.

---

### Post by JersyDvl on 2007-09-26
I installed the nvidia drivers using the Envy utility, and reconfigured xorg.conf and was able to get the nvidia card to work if i switched the cards while already in ubuntu. if i try to boot up from the nvidia card first, then the load bar hangs after 3 bars. any ideas?

---

### Post by louieb on 2007-09-26
I've got an evga brand FX5200 nvidia AGP in 2 different PC's. Nice card great price. 
Anyway I admit I never use the Ubuntu live CD. But other live CDs haven't had a problem with the card. And Ubuntu installed with the alternate CD works just fine out of the box. And once you get Ubuntu installed on the drive, you just get envy  to install the newest driver.

---

### Post by JersyDvl on 2007-09-27
i installed the driver with envy and then when i restart X the screen stays black and i can change the moniter plug form the onboard to the geforce and it works. however, when i restart the computer with it setup to use the nvidia, the load bar freezes. any ideas?

---

### Post by louieb on 2007-09-27
Are you trying to get the live CD to boot using the nviida driver?
Don't think the Ubuntu live CD saves stuff between sessions. Its designed to be a demo and provide a graphical install.
If you want to get the card working on boot without jumping through hoops you have a couple of options. 
1. Go ahead and set up the pc to dual boot widows and Ubuntu. 
2. Get a llive CD designed to save stuff between sessions. Puppy, Knoppix,  Slax, DSL, come to mind and I'm sure there are others.

---

### Post by JersyDvl on 2007-09-27
i have ubuntu and XP installed to dual boot already. my problem is, i cant boot into ubuntu using my nvidia card. also, the live cd wont work with the nvidia card either

---

### Post by louieb on 2007-09-29
I know I'm stumped. No good reason.  Ubuntu should work with that card. So I'll give y ou a bump.

One thing you might try. At the GRUB menu press** e** to edit the Ubuntu selection and remove the the **quiet splash **from the kernel line. And see what message if any show up.

---

### Post by JersyDvl on 2007-09-29
This was the last thing that  was displayed when i took out quiet and splash [IMG]http://i3.photobucket.com/albums/y77/JersyDvl/Other/DSCF0274.jpg[/IMG]

---

### Post by JersyDvl on 2007-09-29
I was just playing with it again and it seems that Ubuntu is willing to run with the Nvidia card, however, it will not boot up with the MB set to use the nvidia card before the onboard card. its almost like its something during booting that doesnt like nvidia and not ubuntu itself. (can you tell im no expert yet? hehe)

---

### Post by dpar on 2007-09-29
I use the FX5200 and have no problems whatsoever. I just installed restricted drives and everything is good to go. I use both Feisty and Gusty with compiz fusion and it works great!
I hope you figure out your problem with the bootup, because there is no problem with that card as far as I know.

---

### Post by louieb on 2007-09-29
Just on a hoot. Try [DSL information]("http://damnsmalllinux.org/")  it has great hardware detection. It a 50 MB download.  I'm not an expert but I do throw stuff at the wall just to see what sticks Just kinda weird that you can use the card if you change to it on the fly. But can't boot to it. .

---

### Post by JersyDvl on 2007-10-01
bump. still lost :-(

---

### Post by JersyDvl on 2007-10-03
bump

---

### Post by JersyDvl on 2007-10-15
bump

---

### Post by JersyDvl on 2007-10-22
after a little research it seems that completely disabling my onboard video card. the problem is there seems to be no way of doing that on my motherboard [MoBo Model]("http://www.asrock.com/mb/overview.asp?Model=775i65GV&s=n"). there is an option to change the order of use between onboard, pci and agp, as well as an option to change the amount of memory the onboard graphics card can use but no option to disable it. can anyone offer any suggestions? thanks in advance

---

### Post by munim on 2007-12-24
I have this problem with each and every version of linux for the past 3 years.. I have googled on this problem for last 3 years and have not found a solution. I guess its a bug which nobody bothered to correct as it exists in only one non standard motherboard.
It exists on this specific motherboard Asrock i865gv with an external AGP card.
The problem is Asrock has put an AGI port on a intel chipset motherboard which doesn't support AGP. rather the graphics card runs on the PCI bus. I think this is the problem.
Now, I just use my onboard card with linux and use my nvidia 6200 when I am going to windows to play games. :-(

---

