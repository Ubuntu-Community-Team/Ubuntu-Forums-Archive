---
title: "Can't boot into windows 7, mbr messed up and boot repair won't fix anything."
date: 2014-04-11
forum: General Help
---

### Post by jaym292 on 2014-04-11
Alright, long story short, my xubuntu got messed up and I had to delete the ext2 partition with my Gparted live cd, and the grub boot loader went with it. I had ubuntu installed on a second hard-drive with a boot loader installed on the first one. Just kept going into grub rescue mode at first.
I first tried using boot repair on my NEW installation of xubuntu after uninstalling the old one [(http://help.ubuntu.com/community/Boot-Repair]("http://help.ubuntu.com/community/Boot-Repair")) and all it did was fix the grub. No windows 7 boot option.
(paste for boot repair) [http://paste.ubuntu.com/7236149](http://paste.ubuntu.com/7236149)
Then I fixed it again, this time with options enabled to fix windows boot files.
[http://paste.ubuntu.com/7236180](http://paste.ubuntu.com/7236180)
Booted into second hard drive with boot-loader "installed", got error saying "Missing OS".
Then I tried one more time selecting the hard drive my windows installation was at.
[http://paste.ubuntu.com/7236214](http://paste.ubuntu.com/7236214)
Nothing... ](*,)

I need to get into windows 7 really bad. Can someone help please?
note: windows boot loader files were deleted, don't know why.

Computer Specs:
old dell optiplex gx270 pentium 4 with 2.70 ghz.
2 hard drives installed, one 80gb one (with windows 7)
other 160gb one (with a ntfs partition for files and a ext2 partition for Xubuntu)
2gbs ram and cd-rom rw

---

### Post by monkeybrain20122 on 2014-04-11
i think you need to do repair or something with a Win7 disk.
But why do you use ext2 for xubuntu? The standard nowadays is ext4.

---

### Post by oldfred on 2014-04-11
You want the Windows boot loader in sda, & grub in sdb. You did the opposite in Boot-Repair.
With a Windows boot loader in sda, you then can  choose sda and directly boot Windows.

Your Windows boot partition sda1 looks like it is missing a boot file & that is why os-prober is not finding it or why it may not directly boot.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr [COLOR=#ff0000]/NTDETECT.COM[/COLOR]
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /[COLOR=#ff0000]Boot/BCD /Windows/System32/winload.exe [/COLOR]

You have the files in RED which is one boot file from an old XP and two from Windows 7., You also need bootmgr in your Windows sda1 partition to boot. You may just need to copy one from your Windows repairCD or flash drive.

---

### Post by jaym292 on 2014-04-11
I don't have my install disk right now..

---

### Post by jaym292 on 2014-04-11
I have a REALLY old hard drive as the second one and it wouldn't install xubuntu with ext4

---

### Post by jaym292 on 2014-04-15
I was gone for a while with some info from you guys and I got it fixed. I'm putting the instructions here for anybody with the same problem :)

Step 1: Get a copy of your windows 7 install disc or the system repair disc, if you can download and burn to cds, download the repair disc [http://maximumpcguides.com/windows-7/create-a-windows-7-system-repair-disc/](http://maximumpcguides.com/windows-7/create-a-windows-7-system-repair-disc/) and burn it to a cd.

Step 2: Boot the system repair disc or install disc and choose system recovery options.

Step 3: Open the command prompt and execute these commands one at a time.
```
bootrec /fixmbr
```

```
bootrec /fixboot
```

Step 4: You should now be able to boot into windows, now download this program, [http://bbs.ipauly.com/viewtopic.php?f=2&t=2/](http://bbs.ipauly.com/viewtopic.php?f=2&t=2/) (I know it looks like it's in chinese but it's not.)

Step 5: In the selection box for destination disk, choose your second hard drive with ubuntu on it.

Step 6: Click "Process MBR"

Step 7: Select GRUB 2.0 and install it.

Step 8: Reboot into second hard drive and now you can boot into Ubuntu again!!!

Enjoy!

---

