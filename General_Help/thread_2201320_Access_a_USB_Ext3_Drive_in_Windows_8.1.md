---
title: "Access a USB Ext3 Drive in Windows 8.1"
date: 2014-01-23
forum: General Help
---

### Post by Thresholder on 2014-01-23
Hello everyone,

I need to access an usb drive formatted in Ext3 (might be ext 2 or 1 but cannot find out for sure).
This is the usb drive connected to my Samsung TV and that I use to record some programs.

I have searched all Internet for weeks and found many solutions(explore2fs,Paragon ExtFS for Windows,Ext2Read,DiskInternals Linux Reader) but none seems to works in Windows 8.1.
It might be that I am not using these applications the right way: for example I have no clue how to use Paragon ExtFS which seems to do nothing at all other than list all drives.

I would really appreciate if anyone has any suggestion please cause I am really out of options at this point.

Many thanks

---

### Post by Dave_L on 2014-01-23
Why not read the files from Ubuntu, then copy them onto a FAT32 or NTFS drive or partition on a USB device?

---

### Post by Dave_L on 2014-01-23
Why not read the files from Ubuntu, then copy them onto a FAT32 or NTFS drive or partition on a USB device?

Or use an internet service like Dropbox to transfer the files.

---

### Post by coldcritter64 on 2014-01-23
Does Win 8  and more particularly your hardware support virtualization (resources like memory, processor etc) ?

 Virtualbox, installed into Win 8, with  an Ubuntu guest  install would give native filesystem access to the usb stick data. Being that Win 8 would be running at the same time, the data can be gotten over quite easily with a virtualbox shared folder in such a set up.  Virtualbox (the Oracle version) supports usb in the guest when set up correctly.

Though note the danger of passing over viruses etc from the Ubuntu guest. I'd install a Linux virus scanner like Avast for Linux to scan any files prior to passing accross to windows.

I've never really found or heard of a decent direct way of accessing Linux filesystems in a MS OS.

---

### Post by Thresholder on 2014-01-23
> **Dave_L said:**
> Why not read the files from Ubuntu, then copy them onto a FAT32 or NTFS drive or partition on a USB device?

Or use an internet service like Dropbox to transfer the files.

Hi Dave_L

I don't understand your suggestions much I'm afraid:

1) I don't have Ubuntu installed anywhere as I have just one PC.
I tried to run Knoppix which had worked perfectly up to Windows 7 but I can't get it to work on Windows 8.1.
I have posted in Knoppix forum for help but if anyone can help on this too all the better.

2) My upload rate is ridiculous so uploading the files is not an option.
I could transfer the files wireless from the tv to my PC but even that transfer rate is crap.

> **coldcritter64 said:**
> Does Win 8  and more particularly your hardware support virtualization (resources like memory, processor etc) ?

 Virtualbox, installed into Win 8, with  an Ubuntu guest  install would give native filesystem access to the usb stick data. Being that Win 8 would be running at the same time, the data can be gotten over quite easily with a virtualbox shared folder in such a set up.  Virtualbox (the Oracle version) supports usb in the guest when set up correctly.

Though note the danger of passing over viruses etc from the Ubuntu guest. I'd install a Linux virus scanner like Avast for Linux to scan any files prior to passing accross to windows.

I've never really found or heard of a decent direct way of accessing Linux filesystems in a MS OS.

Amongst the many options I have tried Virtualbox too but when I try to install xubuntu (somewhere i found a post that recommended this distro fro my simple purpouse) but this is the error I get which I don't understand: [http://prntscr.com/2m0rmf](http://prntscr.com/2m0rmf)

These are my (crappy) PC specs: [http://prntscr.com/2m0h0n](http://prntscr.com/2m0h0n)

Many thanks

---

### Post by Dave_L on 2014-01-23
That error message means that you're trying to using a 64-bit version of Xubuntu on a 32-bit platform.  The solution is to use a 32-bit version of Xubuntu.

---

### Post by coldcritter64 on 2014-01-23
> **Thresholder said:**
> ...
Amongst the many options I have tried Virtualbox too but when I try to install xubuntu (somewhere i found a post that recommended this distro fro my simple purpouse) but this is the error I get which I don't understand: [http://prntscr.com/2m0rmf](http://prntscr.com/2m0rmf)

These are my (crappy) PC specs: [http://prntscr.com/2m0h0n](http://prntscr.com/2m0h0n)

Many thanks

Your AMD processor is 64 bit. From an [[COLOR=#0000ff]A4-3420 spec sheet[/COLOR]]("http://www.cpu-world.com/CPUs/K10/AMD-A4-Series%20A4-3420.html").

> 
[LIST]
[*] AMD64 / AMD 64-bit technology 
[*] AMD-V / AMD Virtualization technology 
[/LIST]
 and with 4 GB of RAM I'd set up a normal 32 bit ubuntu install into the virtual machine, even on 64 bit hardware.

Any Linux distro installed into virtualbox will give the needed ext3 support, there are many to choose from.

Edit: to use virtualization some BIOS settings made need changing, ie. the hardware has to be set up for the virtualization software to work first. Not doing so may cause errors on trying to set up a virtual machine.

Edit2:** I just noted an easier solution** above (Dave_L), copy contents onto a second NTFS formatted usb stick in Linux (boot from a live cd / usb stick if you don't have a bare metal Linux install). Give that copy to Windows to read. 
Cost, 1 more usb stick,: Savings, 1 major virtualbox headache :).

---

### Post by Thresholder on 2014-01-23
> **Dave_L said:**
> That error message means that you're trying to  using a 64-bit version of Xubuntu on a 32-bit platform.  The solution is  to use a 32-bit version of Xubuntu.

I think I am 64 bit but anyway i tried both versions getting the same error.

> **coldcritter64 said:**
> Your AMD processor is 64 bit. From an [[COLOR=#0000ff]A4-3420 spec sheet[/COLOR]]("http://www.cpu-world.com/CPUs/K10/AMD-A4-Series%20A4-3420.html").

 and with 4 GB of RAM I'd set up a normal 32 bit ubuntu install into the virtual machine, even on 64 bit hardware.

Any Linux distro installed into virtualbox will give the needed ext3 support, there are many to choose from.

Edit: to use virtualization some BIOS settings made need changing, ie. the hardware has to be set up for the virtualization software to work first. Not doing so may cause errors on trying to set up a virtual machine.

Edit2:** I just noted an easier solution** above (Dave_L), copy contents onto a second NTFS formatted usb stick in Linux (boot from a live cd / usb stick if you don't have a bare metal Linux install). Give that copy to Windows to read. 
Cost, 1 more usb stick,: Savings, 1 major virtualbox headache :).

Hi,

In the meanwhile i loaded Knoppix into Virtualbox and it worked.
Unfortunately I cannot find the usb drive: can i see it through Knoppix or i have to install Ubuntu like advised?

Regarding your Edit2 solution i am sorry but i don't get it.
As i said i have tried to boot from Knoppix but for whatever reason Windows 8.1 doesn't agree with that.

Thanks

---

### Post by coldcritter64 on 2014-01-23
> **Thresholder said:**
> I think I am 64 bit but anyway i tried both versions getting the same error.



Hi,

In the meanwhile i loaded Knoppix into Virtualbox and it worked.
Unfortunately I cannot find the usb drive: can i see it through Knoppix or i have to install Ubuntu like advised?

Regarding your Edit2 solution i am sorry but i don't get it.
As i said i have tried to boot from Knoppix but for whatever reason Windows 8.1 doesn't agree with that.

Thanks

The USB support for the Linux guest (the "guest additions") must be downloaded and installed from the Oracle site. Not automatically installed if I recall correctly. With the guest additions installed you will be able to set the USB device to the guest install's control in the virtualbox menus in Win8, only then the USB device will be recognized by the Linux guest.


Edit: note this is booting the hardware directly with a cd/usb, this is **not** in a VM

Re edit 2 my earlier post :1. **boot an ubuntu or any live cd** / usb (**not** your **knoppix** install). 
2. Plug in the data usb (ext3)
3. Plug in a brand new usb stick (it is likely fat32 formatted already...if not format it to NTFS or FAT32 in gparted).
4. copy over data from old ext3 stick to the new stick.
5. Reboot into Windows, access the now available NTFS or FAT32 stick with your data on it.
   
-- The easiest way to do it --

---

### Post by Thresholder on 2014-01-23
> **coldcritter64 said:**
> The USB support for the Linux guest (the "guest additions") must be downloaded and installed from the Oracle site. Not automatically installed if I recall correctly. With the guest additions installed you will be able to set the USB device to the guest install's control in the virtualbox menus in Win8, only then the USB device will be recognized by the Linux guest.


Edit: note this is booting the hardware directly with a cd/usb, this is **not** in a VM

Re edit 2 my earlier post :1. **boot an ubuntu or any live cd** / usb (**not** your **knoppix** install). 
2. Plug in the data usb (ext3)
3. Plug in a brand new usb stick (it is likely fat32 formatted already...if not format it to NTFS or FAT32 in gparted).
4. copy over data from old ext3 stick to the new stick.
5. Reboot into Windows, access the now available NTFS or FAT32 stick with your data on it.
   
-- The easiest way to do it --

Thanks, i will search Oracle's site to see if i need to install something else.

I understand the "boot an ubuntu or any live cd" option and that is what i tried to do trying to boot in Knoppix.
Isn't Knoppix a linux live cd?
Otherwise which one should i download as i only know Knoppix.

Many thanks.

---

### Post by coldcritter64 on 2014-01-23
> **Thresholder said:**
> Thanks, i will search Oracle's site to see if i need to install something else.

I understand the "boot an ubuntu or any live cd" option and that is what i tried to do trying to boot in Knoppix.
Isn't Knoppix a linux live cd?
Otherwise which one should i download as i only know Knoppix.

Many thanks.

Originally I started showing/explaining about virtualbox.
I then noted an easy solution in Dave_L's post.

Virtualbox and the guest additions is one way (your Knoppix install is in a VM). You could access the data this way...
[B]
OR[/B]

Use Dave_L's suggestion, copy over the data to an NTFS formatted device from Linux (I am suggesting any Linux DIRECTLY booted on the hardware -- not a VM install, until virtualbox is fully setup).

I gave the steps in my last post for the second possible way (IMO the easy way) to get the data across.

Sorry for any confusion. My virtualbox suggestion works, but takes a lot of setting up. Dave_L's suggestion is a quick / easy method but involves directly booting a Linux system (I recommended a live cd/usb earlier, using it as a tool disc not as an installation media). 

Hope this makes things a bit clearer. You have an easier choice than messing with virtualbox if you wish.

---

### Post by startas on 2014-01-24
Easy answer : free drivers for windows [http://www.paragon-software.com/home/extfs-windows/](http://www.paragon-software.com/home/extfs-windows/)

---

### Post by Thresholder on 2014-01-24
> **coldcritter64 said:**
> Originally I started showing/explaining about virtualbox.
I then noted an easy solution in Dave_L's post.

Virtualbox and the guest additions is one way (your Knoppix install is in a VM). You could access the data this way...
[B]
OR[/B]

Use Dave_L's suggestion, copy over the data to an NTFS formatted device from Linux (I am suggesting any Linux DIRECTLY booted on the hardware -- not a VM install, until virtualbox is fully setup).

I gave the steps in my last post for the second possible way (IMO the easy way) to get the data across.

Sorry for any confusion. My virtualbox suggestion works, but takes a lot of setting up. Dave_L's suggestion is a quick / easy method but involves directly booting a Linux system (I recommended a live cd/usb earlier, using it as a tool disc not as an installation media). 

Hope this makes things a bit clearer. You have an easier choice than messing with virtualbox if you wish.

Hi coldcritter64,

I think i understood both solutions presented but was just asking for which live cd to use since wikipedia lists tons and knoppix is one of them.
Anyway i went with Ubuntu but I still couldn't boot from it for the same reason i cannot with Knoppix which I think is this:
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Not being very experienced and only having this one PC makes me wary of mucking in the bios.

> **startas said:**
> Easy answer : free drivers for windows [http://www.paragon-software.com/home/extfs-windows/](http://www.paragon-software.com/home/extfs-windows/)

Hi startas,

I already tried this as i mentioned in my first post but have no clue how to use it.
It just lists my drives but how do i access the ext3 one?
Do you know?

This is what I get and I assume i have to mount the drive I want to access but it is greyed out:
[http://prntscr.com/2m6cl8](http://prntscr.com/2m6cl8)

Thank you.

---

### Post by startas on 2014-01-24
Well, that is not ext3 partition, trololol :D this is exfat - newer version of fat32, which is windows native file system, and you can just use it out of the box, just go my computer, or as the name changed in windows 8.1 - "this pc" and use your hard drive. And consider buying glasses.

---

### Post by Thresholder on 2014-01-24
> **startas said:**
> Well, that is not ext3 partition, trololol :D this is exfat - newer version of fat32, which is windows native file system, and you can just use it out of the box, just go my computer, or as the name changed in windows 8.1 - "this pc" and use your hard drive. And consider buying glasses.

Well that is what that program says but it's not true or Windows wouldn't try to format a disk that it can read like i reported, wouldn't it?
That hdd has a small fat32 partition and a big one formatted by the TV in ext3 (according to Samsung forum).

---

### Post by startas on 2014-01-24
Well, i suggest you to copy as much important data from external hdd to your pc's internal hdd with ubuntu live cd/usb, and then from windows format external hdd to exfat or other file system, whatever you need. Seems like you have made a big mess.

---

### Post by Thresholder on 2014-01-24
> **startas said:**
> Well, i suggest you to copy as much important data from external hdd to your pc's internal hdd with ubuntu live cd/usb, and then from windows format external hdd to exfat or other file system, whatever you need. Seems like you have made a big mess.

Thanks for the help but maybe you should read my previous posts or I'll just end up copying previous replies: Windows 8 makes it complicated to boot from other media, live cds included.
And I ain't made no big mess: if i was on 7 or any previous Windows I would have had no issues at all.
Also i cannot decide how to format the usb hdd: the tv decides the formatting method and I have no choice on that.

---

### Post by coldcritter64 on 2014-01-24
> **Thresholder said:**
> Thanks for the help but maybe you should read my previous posts or I'll just end up copying previous replies: **Windows 8 makes it complicated to boot from other media**, live cds included.
And I ain't made no big mess: if i was on 7 or any previous Windows I would have had no issues at all.
Also i cannot decide how to format the usb hdd: the tv decides the formatting method and I have no choice on that.

That is right, now I noted that; You may need to go into BIOS (most likely an UEFI bios if a modern machine) and ensure **secure boot is turned off** if it is currently on, that should let you boot any live cd. _*Turn it back on before you try to reboot into windows 8 though.*_ While secure boot is turned off use any live cd to do as previously described. Sounds as if the Knoppix installer has UEFI booting support.

With some problems, accessing BIOS settings becomes essential, you do need to take special care with any changes made. Usually one of the boot screens will tell you which key to press to "Enter Setup", my tower uses the delete key other hardware can vary as to the specific key. 

Even if you don't alter any settings, go into bios and _*see*_ if secure boot is on, that would explain your inability to boot most live cds.

---

### Post by coldraven on 2014-01-25
Another method but one that I have not tried is to install Total Commander from here: [http://www.ghisler.com/](http://www.ghisler.com/)
Then click on "Addons" on the left hand menu of the web-site, then "File System plugins".
There are three different plugins that seem to have Ext3 support, I do not know which one is best.
Maybe try the **DiskInternals Reader plugin.** It says it can open Ext2/3/4
To install plugins read this: [http://www.ghisler.ch/wiki/index.php/Plugin](http://www.ghisler.ch/wiki/index.php/Plugin)

Total Commander is a two pane file manager. 
If the plugin works you should be able to copy the files from one pane to the other by drag and drop or by pressing F5.

---

### Post by Thresholder on 2014-01-26
> **coldcritter64 said:**
> That is right, now I noted that; You may need to go into BIOS (most likely an UEFI bios if a modern machine) and ensure **secure boot is turned off** if it is currently on, that should let you boot any live cd. _*Turn it back on before you try to reboot into windows 8 though.*_ While secure boot is turned off use any live cd to do as previously described. Sounds as if the Knoppix installer has UEFI booting support.

With some problems, accessing BIOS settings becomes essential, you do need to take special care with any changes made. Usually one of the boot screens will tell you which key to press to "Enter Setup", my tower uses the delete key other hardware can vary as to the specific key. 

Even if you don't alter any settings, go into bios and _*see*_ if secure boot is on, that would explain your inability to boot most live cds.

Yeah this is why I am wary of attempting this.
Anyway i just did a disk image of my system to be on the safe side.

> **coldraven said:**
> Another method but one that I have not tried is to install Total Commander from here: [http://www.ghisler.com/](http://www.ghisler.com/)
Then click on "Addons" on the left hand menu of the web-site, then "File System plugins".
There are three different plugins that seem to have Ext3 support, I do not know which one is best.
Maybe try the **DiskInternals Reader plugin.** It says it can open Ext2/3/4
To install plugins read this: [http://www.ghisler.ch/wiki/index.php/Plugin](http://www.ghisler.ch/wiki/index.php/Plugin)

Total Commander is a two pane file manager. 
If the plugin works you should be able to copy the files from one pane to the other by drag and drop or by pressing F5.

Thanks for this option which unfortunately i had tried too because before I go bothering people on the Internet I do try everything I can find.
Unfortunately when I try to install the DiskInternals Reader plugin TC crashes.

I also tried DiskInternals Reader as a standalone but it crashes the same.

I really have no clue why of all these problems.

---

### Post by Thresholder on 2014-01-26
So I have finally managed to disable UEFI and get the option to boot from a dvd.

Unfortunately whatever I try to boot from (Knoppix, Ubuntu.Xubuntu) stops halfway.

The screen resolution changes constantly and the monitor loses the signal several times and than I only get some garbled colours like when you try to play an encrypted video or just a black screen.

Any idea what causes this?

Thank you.

---

