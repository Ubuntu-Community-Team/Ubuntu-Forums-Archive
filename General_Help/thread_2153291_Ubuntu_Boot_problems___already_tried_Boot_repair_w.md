---
title: "Ubuntu Boot problems _ already tried Boot repair with live CD"
date: 2013-06-10
forum: General Help
---

### Post by BrettPrice on 2013-06-10
Hi folks, 

     Recently I decided I wanted to go back to Ubuntu after a stint with XP ( the OS I have always used). I tried Ubuntu about 6 months ago with a dual boot setup and was very impressed with it. I believe sometime around when I had the dual boot going on that some of my boot files got corrupted. Later I decided to go back to XP only ( so I could use Ableton live). Recently I have installed Ubuntu 12 directly over XP. I was hoping this would solve some of the problems I was having while booting. It did not. Now I realize that boot files are totally seperate from OS installs. I have tried to fix this problem with Boot Repair using the Ubuntu live CD to no avail. I tried the Grub and MBR solutions without positive results. Below is the URL complied by Boot Repair. Any help would be much appreciated.

[http://paste.ubuntu.com/5748822](http://paste.ubuntu.com/5748822)

                                                                           Best regards, Brett

---

### Post by ajgreeny on 2013-06-10
You do not seem to have grub installed at all in the MBR of the disk but syslinux instead, so I'm surprised that boot-repair did not work for you.  All I can now suggest is that you try a restoration of grub using the info at section 13 of [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

Good luck!

---

### Post by BrettPrice on 2013-06-10
AJ, 

   Thanks for your lightning fast response. I followed your instructions and tried the [COLOR=#333333][FONT=Ubuntu]Purging & Reinstalling GRUB[/FONT][/COLOR]. option. I was positive this would do the trick but I get the same messages when I try and boot. 

Under the CLIENT MAC ADDR , I get the following 

PXE-E53 : No boot filename received
PXE-M0F : Exiting Intel Boot Agent                                             

  I would be Ok with just trying to re-install Ubuntu again over everything but I would like to graduate beyond this "solution" in terms of computing.  Would this be viable?

Also, here is the new Boot repair URL     [http://paste.ubuntu.com/5753130](http://paste.ubuntu.com/5753130)

                                Regards, Brett

---

### Post by VMC on 2013-06-10
> **BrettPrice said:**
> ...
PXE-E53 : No boot filename received
PXE-M0F : Exiting Intel Boot Agent                                             
...
                                Regards, Brett

In the BIOS, change net boot to HD boot as this solution suggests:

> [COLOR=#000000][FONT=HPRegular]This error comes if the OS or any boot device is not found in network boot, where the system tries to boot from Network or Boot Rom. Seems that teh BIOS setting is lost. To resolve the issue. Enter BIOS by pressing F10 or F1 and reach the Boot tab (on the top with right arrow key). In the Boot tab there should be an option related to boot device priority, Select First Boot as HDD and then save settigs by pressing F10, select Yes for confirmation.[/FONT][/COLOR]

---

### Post by BrettPrice on 2013-06-10
We have a solution! I tried VMC's solution first with no luck but a second attempt mixed with two bios changes fixed it. 1) disable usb boot 2)disable boot to network. Thank you both for your time.  

                                                                Brett

---

### Post by BrettPrice on 2013-06-10
If you would like to mark this solved somehow I can.

---

