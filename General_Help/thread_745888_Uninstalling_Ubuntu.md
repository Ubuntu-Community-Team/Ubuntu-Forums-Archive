---
title: "Uninstalling Ubuntu"
date: 2008-04-05
forum: General Help
---

### Post by Tetreaus on 2008-04-05
I have to remove Ubuntu from one of my machines and I am having issues doing so.  I normally just put in the Windows CD, boot from it, and it worked but this time it is not letting me boot from the CD.  Is there reason that this is not working?

---

### Post by reyhan on 2008-04-05
Did you try it?

---

### Post by reyhan on 2008-04-05
[I]you just use the windows xp CD and remove the ubuntu partition and restart your computer and boot woth windows xp cd again and go to the recovery console and type this ```
fixmbr
```

---

### Post by Tetreaus on 2008-04-05
I was told to try that but I can not even get it to boot the windows CD. I do have it set to boot from CD and stuff. When I put it in it just acts like its not in there.

---

### Post by thecorleonefamily on 2008-04-05
I guess maybe you should try if the CD works. Or more specific, you should change the Boot Order in the BIOS options so that it boots from the CD ROM.

---

### Post by Tetreaus on 2008-04-05
I tried the CD on another machine and it worked just fine and I am sure it is set to boot from the CD.

---

### Post by thecorleonefamily on 2008-04-05
What is the structure of your hard drive (the one which you want to format),. I mean what partitions and all? 

If you are running, Linux: 

```
 sudo fdisk -l 
```

Else Windows, you can find out from Disk Management.

---

### Post by prshah on 2008-04-05
> **Tetreaus said:**
> I have to remove Ubuntu from one of my machines and I am having issues doing so.  I normally just put in the Windows CD, boot from it, and it worked but this time it is not letting me boot from the CD.  Is there reason that this is not working?

Are you using Ubuntu, Xubuntu, StikyBuntu or KUbuntu? StikyBuntu is tough to remove, you may need professional help.

Or maybe your CD drive or Windows CD is broken.

Does your ubuntu live CD boot? If it doesn't check your BIOS settings and CDROM drive. If it does, check your Windows CD. Don't use a StikyBuntu CD by mistake!

If Ubuntu live CD boots but Windows doesn't and that Windows disk works fine on another system maybe Windows _just_ doesn't WANT to go back on that system, probably feels jilted.

---

### Post by Tetreaus on 2008-04-05
> **thecorleonefamily said:**
> What is the structure of your hard drive (the one which you want to format),. I mean what partitions and all? 

If you are running, Linux: 

```
 sudo fdisk -l 
```

Else Windows, you can find out from Disk Management.

It gave me this..

```
Disk /dev/hda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009850f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2372    19053058+  83  Linux
/dev/hda2            2373        2480      867510    5  Extended
/dev/hda5            2373        2480      867478+  82  Linux swap / Solaris
```

I really don't know exactly what that means though -.-

---

### Post by thecorleonefamily on 2008-04-05
Ok, I am not sure how it is actually UNINSTALLED, but I will tell you how I did it.

Download, Gparted [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

The LiveCD works best.

Download the ISO, burn it and boot from the LiveCD.

If it boots, continue reading: else you **do** need to check your BIOS boot order settings.

Once the CD boots, it will present you with the partitions. Delete all partitions and format them to NTFS. If you delete all partitions, you should have one NTFS partition. (as in your case)

This way, when Windows boots, it will find the partition and hopefully install. 

I am not sure if this is the definitive solution, however it did work for me.

Post the results. Best of luck.

---

### Post by Tetreaus on 2008-04-05
OK well I booted from it and I got this.....

```
GNU GRUB  version 0.97 (638k lower / 785344K upper memory)

[ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible commands completions.  Anywhere else TAB lists possible competitions of a device/filename. ]

grub>
```

Kinda confused now >.<

---

### Post by thecorleonefamily on 2008-04-05
You seriously NEED to check everything about your CD ROM/ DVD ROM drive. I mean the jumpers and the boot order. 

Is your CD ROM on Master or on Slave? You need to check all this, cause I am sure something is wrong at that end only.

---

### Post by Tetreaus on 2008-04-05
It is set to the first and it is the master.

It boots from the Gparted thingy.. I think.. it says

Booting from CD: Loading stage2

then gives my that stuff I posted before.

---

### Post by thecorleonefamily on 2008-04-05
You have an ATA hard disk or a Serial ATA 

(Lots of wires or a single red connecting wire?)

---

### Post by Tetreaus on 2008-04-05
It's not SATA.

---

### Post by thecorleonefamily on 2008-04-05
[IMG]http://content.answers.com/main/content/img/CDE/_SATPAT.JPG[/IMG]

Assuming you have a PATA, this is what you need to do:

Whenever you attach a hard disk and a CD ROM drive using PATA interface, always make sure that your hard disk is on the master and the CD ROM on the slave. This can be done using the JUMPER pins. In short it means, that there are 2 end point of the PATA cable with a mid point cable. One end point is in the motherboard, fix the other end point to the hard disk and the midpoint to the CD ROM **AFTER** you have set the appropriate jumpers. 

Try this it should work. I got so fed up with this PATA thing that I switched to SATA. Single wire, no master slave problem. Anyways, thats not the point, you try the above thing and post back.

BLUE: Motherboard, BLACK: Harddisk, WHITE: CD ROM

---

### Post by Tetreaus on 2008-04-05
Yup.. I have it set up right.  Even opened it up and double checked.

---

### Post by thecorleonefamily on 2008-04-05
You said the CD ROM was on MASTER! 

> ""It is set to the first and it is the master.""

---

### Post by Tetreaus on 2008-04-05
That I did.. I have mine set up with two cables.. one like this

```
BLUE: Motherboard BLACK: CD 1 WHITE: CD 2
```

and the other like...

```
BLUE: Motherboard BLACK Hardrive WHITE: Nothing (would normally be a second HDD if one was in here...)
```

after realizing exactly what you said I opened it up and tried hooking it up like you said and nothing changed.

I really don't see how this is a hardware problem though.  Stuff booted from that drive before I had Ubuntu installed and stuff like the Ubuntu CD still do.

---

### Post by thecorleonefamily on 2008-04-05
Ubuntu cannot possibly modify your computer to that extent that you can't boot off from a CD ROM , this problem is definately hardware related. 

But you are right, it should boot at least.. Do one thing, remove the hard disk and then try booting from the CD. Does it help?

---

### Post by RedPandaFox on 2008-04-05
Hey, I can see your problem but the solution you wont like, 
Windows refuses to acknowledge anything but its own operating systems. I have tried in many ways and spent lots of time researching. It will not boot the CD if it knows there are other formatted partitions on there. 
I think this was part of that anti-competitive lawsuit against microsoft was about, they will not allow you to boot that CD if there is another os there.
It took me a long time and lots of trying but the only way I found to resolve this was reformat my HDD to remove all traces of the OS.
But something you should consider is that where I am (NSW Australia) We get a computing mag called APC, which has free rescue DVDs in every issue with partitioning wizards. Try reformatting the Linux partition to FAT32 or NTFS.

You need to get rid of all traces of the Linux before Microsoft will let you boot from there cds im sorry to say :(

Try finding a partitioning wizard online or a rescue CD or even the live CDs for Ubuntu have one in system I think

Hope this helps :)

---

