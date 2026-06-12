---
title: "Replacing Ubuntu with windows 7"
date: 2013-04-30
forum: General Help
---

### Post by Ragi1992 on 2013-04-30
So, I have the iso for windows 7. I have used GParted to try to use my falshdrive to boot from usb flashdrive, I have tried to use WinUSB, as well as startup disk creator.. Nothing has worked! When I use WinUSB it says Missing operating system (Same when I extract the iso and put files into flashdrive) And when I just put the iso itself into the flashdrive it says bootmgr not found. 

I love Ubuntu, but I want to save my money and get another computer for Linux, because I currently need windows.  

How am I suppose to replace Ubuntu 12.04 with Windows 7?

:confused::confused::confused:

---

### Post by papibe on 2013-04-30
Hi Ragi1992.

Use 'Brasero', or install 'Gnome Baker'.

In Brasero, select 'Burn Image'.

In Baker, Tools -> Burn DVD Image.

Regards.

---

### Post by Ragi1992 on 2013-04-30
> **papibe said:**
> Hi Ragi1992.

Use 'Brasero', or install 'Gnome Baker'.

In Brasero, select 'Burn Image'.

In Baker, Tools -> Burn DVD Image.

Regards.

With Brasero and Gnome Baker, don't I have to have a DVD? I don't have a cd drive so I can only use a flashdrive. I'm sorry I should have specified.

---

### Post by papibe on 2013-04-30
> **Ragi1992 said:**
> With Brasero and Gnome Baker, don't I have to have a DVD?.
Ohh I see.

Then try 'Startup Disk Creator', or install 'UNetbootin'.

Let us know how it goes.
Regards.

---

### Post by C.S.Cameron on 2013-04-30
Format your flash drive to NTFS using gparted and set the boot flag.
Extract the ISO to the flash drive using Archive Manager.

That is all there is to it.

---

### Post by Ragi1992 on 2013-04-30
> **C.S.Cameron said:**
> Format your flash drive to NTFS using gparted and set the boot flag.
Extract the ISO to the flash drive using Archive Manager.

That is all there is to it.

It worked! Thanks:D

But now it will not let me put windows on my hard drive (Ubuntu 12.04 is on it) It says its not the right format. How would I go about making it NTFS? I think I have a general idea on how to do it, but I don't want to ruin my computer by some stupid mistake..

---

### Post by Iowan on 2013-04-30
> **Ragi1992 said:**
> .. but I don't want to ruin my computer by some stupid mistake..
:-# /me refrains from making OS comment... ;)

---

### Post by Ragi1992 on 2013-04-30
> **Iowan said:**
> :-# /me refrains from making OS comment... ;)

Lol I apologize for my ignorance. I just really don't want to somehow mess up my hard drive. Is there anyway for me to reformat it?

---

### Post by C.S.Cameron on 2013-04-30
If you have the Ubuntu Live CD you can run gparted from that. 

I thought you could also format when booting the W7 installer.

---

### Post by Iowan on 2013-04-30
That WAS intended as humor...
We still use XP at work, and I use Ubuntu at home - so my experience with W7 is quite limited.
 I would expect the installer to have a formatting tool.

[edit]...and outtyped again, too...

---

### Post by Ragi1992 on 2013-04-30
> **Iowan said:**
> That WAS intended as humor...
We still use XP at work, and I use Ubuntu at home - so my experience with W7 is quite limited.
 I would expect the installer to have a formatting tool.

[edit]...and outtyped again, too...

Actually both of you were right.. However while the button is there it is nonclickable.. So I guess I'll have to do it while using linux. Is this even possible?

---

### Post by Ragi1992 on 2013-04-30
To make it even more fun, GParted will not allow me to reformat my harddrive or unmount it to reformat it.

---

### Post by C.S.Cameron on 2013-04-30
You need to format the drive when booted from a second drive, say the Live CD.

---

### Post by Ragi1992 on 2013-04-30
I no longer have the live CD/DVD :\ All I have is the windows 7 iso and thats it.

---

### Post by Ragi1992 on 2013-05-01
I ran the command ```
dd if=/dev/zero of=/dev/hda bs=521 count=1
```
and it came out to this..

```
dd: opening `/dev/hda': Permission denied
```

I was trying to remove the linux partition and try to install from my USB again. Obviously that didn't work.. I'm getting very frustrated.

---

### Post by Ragi1992 on 2013-05-01
Is there a way to wipe my hard drive without using a live CD/DVD?

---

### Post by CoreyB. on 2013-05-01
If you can boot to your Windows 7 flash drive, [this]("http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html") guide should help you.

Though when I've installed Windows 7, I've never seen steps 2 and 3, it just skips from 1 to 4, but that may be because I'm never connected to the internet when I install.

EDIT: Make sure you have a valid legal Windows 7 key before you install.

---

### Post by Ragi1992 on 2013-05-01
So a random thing popped up on my files application under devices:

1.1 GB filesystem

Because its mounted its not allowing me to make another partition table?

---

### Post by HermanAB on 2013-05-01
Dual booting is so last century...

Install Virtualbox and make a Windows VM.  Then you can run Windows in a window where it belongs.  In some respects Windows actually runs faster in Virtualbox than natively on the same hardware.

There is a Virtualization forum for this.

---

### Post by Ragi1992 on 2013-05-01
> **HermanAB said:**
> Dual booting is so last century...

Install Virtualbox and make a Windows VM.  Then you can run Windows in a window where it belongs.  In some respects Windows actually runs faster in Virtualbox than natively on the same hardware.

There is a Virtualization forum for this.

I can't use virtualization for what I'm wanting.

---

### Post by C0NFU53D2 on 2013-05-01
if you are indeed running the live version of ubuntu, make sure you are not trying to format your usb, make sure you are formating the hard drive.  i would assume the 1.1gb filesystem is your USB.  also, if it says your filesystem(HDD) is mounted and it wont let you format it, then you need to unmount it, and then try to format.

i, personaly, have never had any issues with dual booting/reinstalling OS's.  it is odd that you cannot format from within the win7 live usb.  make sure you didn't somehow lock or protect your hdd in your BIOS, i don't know what else would cause this issue you are experiancing.

im not sure if you did or didn't get the win7 usb to boot, but all i have had to do is copy the files from inside the ISO directly to the USB formatted in FAT32 or NTFS.

---

### Post by Ragi1992 on 2013-05-01
> **C0NFU53D2 said:**
> if you are indeed running the live version of ubuntu, make sure you are not trying to format your usb, make sure you are formating the hard drive.  i would assume the 1.1gb filesystem is your USB.  also, if it says your filesystem(HDD) is mounted and it wont let you format it, then you need to unmount it, and then try to format.

i, personaly, have never had any issues with dual booting/reinstalling OS's.  it is odd that you cannot format from within the win7 live usb.  make sure you didn't somehow lock or protect your hdd in your BIOS, i don't know what else would cause this issue you are experiancing.

im not sure if you did or didn't get the win7 usb to boot, but all i have had to do is copy the files from inside the ISO directly to the USB formatted in FAT32 or NTFS.

I did get it to boot from USB, but it won't format from within installation. How do I check to see if I locked my HDD?

---

### Post by C0NFU53D2 on 2013-05-01
i belive it would say in the BIOS under various names/subsections depending on your BIOS verson and computer manufacturer, if the ability is included on your particular computer.  probably uner advanced, drive management, or protection, etc.  to get to your bios there are normally directions when your computer ***first*** starts up, useually a F#(eg F1, F2...) key, or Esc.

---

### Post by Ragi1992 on 2013-05-01
> **C0NFU53D2 said:**
> i belive it would say in the BIOS under various names/subsections depending on your BIOS verson and computer manufacturer, if the ability is included on your particular computer.  probably uner advanced, drive management, or protection, etc.  to get to your bios there are normally directions when your computer ***first*** starts up, useually a F#(eg F1, F2...) key, or Esc.

The password says clear so I assume my HDD isn't locked..

---

### Post by C0NFU53D2 on 2013-05-01
i am researching this issue, i think i had a similar issue once when booting a win7 usb, when you boot the windows 7 usb makesure you click on the hard drive you want to format before you try to format it.  i know it sounds dumb, but i think that happened to me once. :P

if that doesn't work you can try this:
[http://superuser.com/questions/445887/why-doesnt-windows-7-allow-me-to-format](http://superuser.com/questions/445887/why-doesnt-windows-7-allow-me-to-format)

---

