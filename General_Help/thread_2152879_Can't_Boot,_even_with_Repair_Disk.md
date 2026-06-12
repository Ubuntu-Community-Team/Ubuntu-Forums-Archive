---
title: "Can't Boot, even with Repair Disk"
date: 2013-06-09
forum: General Help
---

### Post by lengsfield on 2013-06-09
Hi

For two or three years I've been running Ubuntu on a Toshiba Satellite A215, AMD 64 dual core, 2gb ram, 160gb hdd (currently loaded w 12.04).    The computer crashed during loaded, which may or may not have been related to a dead battery caused by bad connecter on the powercord (since replaced).  

I've been unable to boot ever since.  When I let it boot, it shows a grub screen offering me the opportunity to choose Ubuntu, Memtest, etc.  As soon as I touch a key, it freezes.  I tried to boot with an Ubuntu 13.04 install disk, but it doesn't work.  I tried with an ubuntu repair disk, which seems to open properly, but it freezes when I hit a key (say to choose English.)  If I let it go without choosing a language, it goes to a blinking cursor that stays in that position indefinitely.  

Any ideas?  

thanks.

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]lengsfield; Hi ! Welcome to the forum.

Are we looking at a situation where an update broke the proprietary graphics driver ?

From that grub menu selection screen on your install, what results if you choose to boot a "recovery" kernel ?
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by lengsfield on 2013-06-09
I don't get a choice for a recovery kernel.  The choices I see are:

Ubuntu
Adv Options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

But I can't choose any of them.

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]lengsfield;
Panic not. [/COLOR]Just proceed in a calm and orderly fashion. 

What version/distro do you have installed ?
On the 13.04 install disk... when you created the disk -> did you check the md5sum of the .iso file and also verify the disk's integrity from that disk's boot menu ?

and the biggy here, to boot that liveDVD have you reset the boot priority in your bios ?
[INDENT]
small things may have big consequences

[/INDENT]

---

### Post by lengsfield on 2013-06-09
Hi, 

I didn't check the integrity of the disks, but I did try two different disks, one a straight 13.04 install and the other a rescue disk.  12.10 was the last install running. 

To boot from the DVD, I just changed the boot sequence in startup, which is what I've done in the past.   Do I need to change something else? 

Many thanks.

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]lengsfield;

What has worked in the past ...should work now to boot.
OK, have either of the two boot disk ever been booted up ?
If yes and they will not boot now ...then I suggest that the bios has become corrupted... now that may not be a big deal... \Set bios back to the default settings... how to do that varies with each machine and the bios installed... one needs to consult the manual for directions on how to reset bios to default. I have seen it where a hardware reset was required and that method requires opening up the box and repining CMOS temporarily and pinning back to original pins.

Before taking this course of action I would verify that the boot disk are good ...another machine of the same architecture !
[/COLOR][INDENT=2][COLOR=#000000]
there is light at the end of a tunnel

[/COLOR][/INDENT]

---

### Post by lengsfield on 2013-06-09
I wondered about that.  Is it enough to pull the battery?  Assuming that I can reach it.

Thanks again.

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]lengsfield; 

Generally, pulling the battery on a DeskTop box will clear reset the bios to default.

I do not know about a laptop, if that is what is in reference here, and will not advise that course of action.... as difficult as it is to sometimes break open a lap top... I would think the manufacturer would exercise the forethought to permit resetting to default by some other means.
[/COLOR][INDENT=2][COLOR=#000000]
just my thought

[/COLOR][/INDENT]

---

### Post by lengsfield on 2013-06-13
Hi, 

 I tried to reset the defaults in setup, and then I followed directions to short the two jumpers that are supposed to re-set the BIOS.  So far, nothing is working and nothing has changed. 

Any other ideas? 

thanks

---

### Post by Bashing-om on 2013-06-13
[COLOR=#000000]lengsfield;
Let's cover all the other bases. -assuming now that bios is "good",
1. In bios check(again) that 1st boot priority is the CD or DVD drive - whichever you device you are booting from(DVD disk for DVD device, CD disk for the CD device)
2. If your bios has "secure" boot ...turn it off,
3. Does your system incorporate "UEFI",
4. Check the md5sum of the downloaded .iso image file.
5. When you do boot the liveDVD , when the bios screen clears depress and hold the shift key -> boot menu;
in this boot menu is an option to "check disk" integrity or some such... do so ..check the disk integrity.
6, reboot and advise us where the boot up stalls, what do you see, how far in the booting process of the liveDVD do you get ?

Bear in mind I still look at the great possibility of a broken graphics driver..just let us rule out a problem in these basics...
We want to be able to boot up a liveCD/DVD (CD is fine in the case of version 12.04), If you were able earlier to boot a liveCD, and now cannot...and the new CD has been checked and verified ..and still unable to boot...
We will try some of the boot options available on the liveCD and see what the response is.
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by lengsfield on 2013-06-14
Hi,
1.  I'm able to change the boot order to CD/DVD.
2. Can't find any options that refer to Secure Boot.  There is a password set to Clear, but it doesn't ask for the password. 
3. Don't think that it's using UEFI.
4. Didn't check the [COLOR=#000000]md5sum of the iso files, but both disks - Ubuntu 13.04 and the Boot Rescue Disk - work on another laptop.
5. Can't get far enough to do the memtest.
6. The regular boot from hdd goes to the grub screen, but is frozen.  The Ubuntu disk freezes when I get the first purple screen w/ only the one small graphic at the bottom of the page.  The rescue disk freezes when I hit a key to choose a language, but if I don't choose and allow it to time out then it goes to a black screen with a blinking cursor and stays there. 

Wonder if I need to physically pull the battery to reset the BIOS.  All the instructions I found showed how to short two jumpers that would reset the password. 


Many thanks. 
[/COLOR]

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]lengsfield; Hey...

Quite frankly, this is not making too much sense to me....Machine was booting and was able to boot from the cd drive; and now it is not... bios settings have been reset to default to preclude any changes affecting any "hand off" to the operating system, and still not booting with a known good medium// can not even get to the boot options screen to affect any change in the booting process.........->

OK, let us say the CD drive is at fault. Can you ,or have access to, boot from a usb thumb drive...  to boot from... see then ?
[/COLOR][INDENT=3][COLOR=#000000]
just my thought
 [/COLOR][/INDENT]

---

### Post by lengsfield on 2013-06-15
Hi, 

I have been unable to boot in any form. 

It recognizes the Ubuntu 13.04 dvd and Rescue Disk, but hangs up immediately.  Don't think that it's a fault in the drive, as the behaviour is roughly the same as when it tries to boot from HDD.

I'm not sure that've actually reset the BIOS.  I shorted the jumpers, but that's supposed to clear the password.  I hit the reset to defaults, but that doesn't mean that it actually happened.  I may explore removing the battery, but that involves a fair bit of disassembly.

Other ideas?  Can I flash the BIOS from a disk or USB if I can't boot? 

Thanks again.

---

### Post by Bashing-om on 2013-06-15
[COLOR=#000000]lengsfield

Flashing Bios: A means of last resort, if it ain't broke, please do not fix it .. To directly answer your question, yes one may flash the bios. There exist a couple of avenues to do so. Bear in mind, changing bios may introduce new problems but if needed, it is needed. make sure it is needed ! The easy method is if you have a utility in your bios to do the update for you;
else next is a utility within Windows to make the update;
else one must go to the bios manufacturer, download the bios update file, make up a DOS boot disk, combine on that disk the new bios file with a flashing utility -> can be done, many prefer this ...you have control on what version and how it gets installed; not recommended for a novice. One should have experience with manipulating bios, building system files, and familiar with the command line before attempting. If you make a mistake,and your mainboard's bios is not on-chip, throw that computer in the trash as there may be no way to burn that eprom. Unless you know what you are doing.... DO NOT go there.

If you know your liveDVD is good,
if you are certain your drive is good,
And you do not boot to the grub menu(if you can get to the grub menu then other measures may be looked at);

Then all that is left is bios... it can do no harm in the long term to make adjustments to the superficial setting in bios, so long as clock rates are not tampered with, one may always reset the values back to default. If you have not done so yet, get the manual for your machine's bios. Read and heed... Unless some one is running the exact same machine with that same version of bios, none can advise how to set it up precisely.


Bottom line: If you can not boot the DVD to grub... check the settings in bios, read the manual to know what the setting affect.
[/COLOR][INDENT=2][COLOR=#000000]
my thought, my opinion ..yours may vary

[/COLOR][/INDENT]

---

