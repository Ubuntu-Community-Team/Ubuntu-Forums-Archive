---
title: "ubuntu 15.04 upgrade to 15.10"
date: 2015-11-18
forum: General Help
---

### Post by adam171 on 2015-11-18
Hello, IO don't know if any one can help me, i'm in a right dire starits.
I recently upgraded from15.04 to 15.10 and thats when it all happened and it's a nightmare.
The upgrade was fine no problems, then i restarted the laptop and it just got worse, i kept getting a blank screen so i used my windows partition to get a live cd done which i did.
then i proceeded with the cd to fix problems and instead ended up with partitions that are now completely the wrong size and inadequate for running ubuntu but also messed up my windows partition and now it wont run whatsoever with no space on the hard drive. the only way i can access ubuntu is through the live cd because i cant re-install it with so little space. i have tried to fix it but its gone very badly wrong for me and although i know i can find most of my data ive lost through testdisk and other software it's just a major headache and im completely stressed now.
Something so easy has gone so badly wrong i like ubuntu and prefer it a million time more than windows.any sugestions would be welcomed.

---

### Post by Geoffrey_Arndt on 2015-11-18
Well Adam171, 

The right way to figure out what's going on is:

1).   Provide detail specs on your laptop (make, model, cpu, ram, video chipset, and onboard storage (single hdd, twin hdd, ssd, etc.)
2).   Is your goal to retain a dual-boot, or just run Ubuntu?
3).   Provide a graphic (screenprint) of your current partitions on hdd's or ssd's so we can see what's installed (can do this via the "gparted" program on any Live Linux Dvd/CD/usb flash-stick)
4).   Install/run "Boot Repair" program & attach the report link:   [http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

---

### Post by grahammechanical on 2015-11-18
The past is the past. From where i am sitting the future for you is recovering as much of your data as possible. and then re-installing both Windows & Ubuntu.

---

### Post by adam171 on 2015-11-18
it would of been a sensible thing to do that from the start really

ubuntu 15.10 memory 3.7gib intel celeron(r) cpu b820 @1.70ghz x2 intel sandybridge mobile 64bit disc is 2.0gb

---

### Post by howefield on 2015-11-19
It is likely that no one here will se that picture apart from you, seeing as you have simply posted a path within you own computer. Try using the paperclip icon with the posting window to attach an image to your posting. (You won't see the paperclip icon in the quick reply window, use the Reply to Thread button).

---

### Post by adam171 on 2015-11-19
i did it 4 ways, the one you said, cut and copy and paste, drop and draged it and used image insert icon. as you cant tell im having quite a few problems, before you think (damn newbie) ive used a dual boot process for a number of years ive used ubuntu when it was a few grades from the start 5.04 i think it was, i know my way round a computer i know what it all does. thats why im so stressed in all my time ive never encountered a problem such as this.

[ATTACH=CONFIG]265680[/ATTACH] hooray it let me do it

---

### Post by Geoffrey_Arndt on 2015-11-19
What is your graphics system on the PC?   Are you using Intel integrated, or is it nVidia or ATI/AMD?    It doesn't look like you're running an EFI system but can you confirm?   

Re your current situation, will the Live CD mount all of your partitions in the file manager and allow you to copy off those files you need?   As Graham mentioned, first priority will be data recovery (especially, if you don't have a saved backup).   With the state of the hard drive (375 GiB swap!!??) . . . . . and only 1 full ntfs partition,  a full Windows reinstall might be your best option.   But let's see if more experienced forum members than I can see other ways to salvage the PC.

---

### Post by adam171 on 2015-11-19
intel 2nd generation 64 bit 33mhz and obviously it's vga compatible and yes BIOS

one of my biggest problems is generating space, there is tons of it but i cant resize anything other than unallocated space which is useless because its obviously unallocated. and for my system to run ubuntu and windows it needs space, soi you can see why ive been banging my head a against a wall, oh and for me to retrieve or recover data i need to download or install it through terminal and i cant.

---

### Post by Geoffrey_Arndt on 2015-11-19
If you do more resizing, moving, etc., then it makes recovering data harder.    Why do you think you have to use the terminal to recover your data?   In other words, you CAN install recover apps by using the LIVE cd/dvd/usbstick, but the installed program must be used during the live session.   Of course, the other option is to create a "'persistent" Live media - perhaps using another computer (even at a library or friend/relative, etc.).   You may have to think outside the box.   

Also, here's another option - - _can order a live-usb stick_ (and parted magic is the best live media imho):   [https://partedmagic.com/downloads/](https://partedmagic.com/downloads/)

---

### Post by howefield on 2015-11-19
> **adam171 said:**
> one of my biggest problems is generating space, there is tons of it but i cant resize anything other than unallocated space which is useless because its obviously unallocated..

Try right clicking on the swap partition (sda9) and select Swapoff - that should let you you resize it (or remove altogether given that you already have another swap partition on sda2) and then in turn the move/resize the other partitions starting from the one immediately left of swap. In any event it looks like you have wiped out your Windows installation except for the recovery partition. 

If it were mine I'd probably use the Live CD/USB to save any required data that I had been foolish enough not to have a backup of, then try to use the Windows recovery partition to reinstall Windows, putting the machine back to the way it was when first switched on after purchasing.

Once done with that, use the Windows tools to resize windows making space for an Ubuntu install.

---

### Post by adam171 on 2015-12-05
thanks to every one of you for your input, insight and help. I have managed to rectify the problem and recover all of my data and photos, however the most startling aspect of this whole exercise was that the recovery tool i used was extremely detailed and i am really really concerned about what it recovered and if this fell into the wrong hands.

---

