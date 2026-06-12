---
title: "USB drive to boot to Ubuntu"
date: 2013-01-28
forum: General Help
---

### Post by cwblanch on 2013-01-28
I've just re installed Ubuntu on my laptop, I'm dual booting with Windows 7 and the GRUB options for picking either Windows or Ubuntu aren't showing up. It ONLY shows up when I have the usb I installed with plugged in during start up.

I've used Ubuntu before, I've just not run across the GRUB not starting...or whatever it's doing. Since I've not run into this problem before I have had no luck searching it, so I apologize if this is a repeated post.

Thank you!

---

### Post by papibe on 2013-01-28
Hi cwblanch. Welcome to the forums ):P

It looks like grub wasn't properly installed in your hard drive.

You can use your installation media as a Live media, and repair grub. Take a look at this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") for details.

Let us know how it goes.
Regards.

---

### Post by cwblanch on 2013-01-29
I can't seem to run what it's telling me to in the tutorial, all it does is sit there.  It could be because I tether my phone to my laptop with easytether, I'm new to using it so I'm not sure if its impacting. 
Would installing a new terminal help this?

Also, does it have to be run as a Live media? Because when the flash drive is plugged in, all it does it take me to the grub menu, I click Ubuntu and it takes me there.

---

### Post by C.S.Cameron on 2013-01-29
Boot into Ubuntu with your USB plugged in.
Remove the USB.
In Terminal run:

```
sudo update-grub
```

---

### Post by cwblanch on 2013-01-30
> **papibe said:**
> Hi cwblanch. Welcome to the forums ):P

It looks like grub wasn't properly installed in your hard drive.

You can use your installation media as a Live media, and repair grub. Take a look at this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") for details.

Let us know how it goes.
Regards.

I'm trying to get the terminal to install the repository for me, but it just sits there for a while before giving me an error.
I'm not sure if this is because I'm using easytether to tether my phone to it or because the repository is broken or something.
Here's the error:
```

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (7, "couldn't connect to host")

```> **C.S.Cameron said:**
> Boot into Ubuntu with your USB plugged in.
Remove the USB.
In Terminal run:

```
sudo update-grub
```

That didn't seem to work. It ran like it should, but nothing changed on reboot. It just booted to windows 7.

---

### Post by Mark Phelps on 2013-01-31
Actually, there is an option that will allow you to add the capability to boot into Ubuntu using the Window boot loader.

It is known as EasyBCD and you can download and install it from the NeoSmart Technology forums. I did this on a Windows laptop where I wanted to run Ubuntu but I didn't want to run the risk of corrupting the Windows boot or filesystem in the process.

Once you install that, you use a menu option to add another OS and it will install NEOGRUB in the process -- GRUB written to run on a Windows filesystem.

For more details, you should visit their forums.

---

### Post by C.S.Cameron on 2013-01-31
> **Mark Phelps said:**
> Actually, there is an option that will allow you to add the capability to boot into Ubuntu using the Window boot loader.

It is known as EasyBCD and you can download and install it from the NeoSmart Technology forums. I did this on a Windows laptop where I wanted to run Ubuntu but I didn't want to run the risk of corrupting the Windows boot or filesystem in the process.

Once you install that, you use a menu option to add another OS and it will install NEOGRUB in the process -- GRUB written to run on a Windows filesystem.

For more details, you should visit their forums.

+1, works for me.

---

### Post by varunendra on 2013-02-01
> **Mark Phelps said:**
> Actually, there is an option that will allow you to add the capability to boot into Ubuntu using the Window boot loader.

It is known as EasyBCD..
+1 from me too.

I recently installed Ubuntu 12.04 on a desktop which already had Win7 + XP on a different HDD (with Win7 boot-loader being on the XP partition).

I installed with that HDD disconnected to make sure Grub gets installed on the Ubuntu HDD. Everything was fine except when booting to XP from Grub (Grub > Win7 boot loader > XP), it returned error (don't remember exactly, but it was something 'corrupt boot.ini' related). Win7 itself loaded fine though, and XP too when booting from the windows HDD.

So I tried EasyBCD (it automatically detected the Ubuntu installation) and added Ubuntu to the Win7 boot menu instead. Worked like a charm!

---

### Post by cwblanch on 2013-02-01
> **Mark Phelps said:**
> Actually, there is an option that will allow you to add the capability to boot into Ubuntu using the Window boot loader.

It is known as EasyBCD and you can download and install it from the NeoSmart Technology forums. I did this on a Windows laptop where I wanted to run Ubuntu but I didn't want to run the risk of corrupting the Windows boot or filesystem in the process.

Once you install that, you use a menu option to add another OS and it will install NEOGRUB in the process -- GRUB written to run on a Windows filesystem.

For more details, you should visit their forums.

Wow, this looks like it will really work, but just to clarify; I have to install this through Windows? 
Also, is it necessary to register for it? Or is there another place I can download it?

---

### Post by varunendra on 2013-02-02
> **cwblanch said:**
> Wow, this looks like it will really work, but just to clarify; I have to install this through Windows? 
Also, is it necessary to register for it? Or is there another place I can download it?
Yes, it is a Windows software, and has to be installed there. It only works with versions that use "BCD" as boot loaders, in other words - Vista onwards.

And I used the free version available on Softpedia (there are also other links available though) : [http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml](http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml)

Hope it helps :)

---

### Post by arpanaut on 2013-02-02
Would it not just be more simple to install grub into the mbr of the hard drive?

Sometimes the installer (ubiquity) identifies the usb drive as the primary boot drive aka sda, and install grub there so when the usb drive is removed the system will just boot into windows.

So if you have a single hard drive (physical drive) on your system then the simple solution is to just to install grub into the mbr of that drive.
```

sudo fdisk -lu
```will help you identify how your system is identifying your hard drives.
So after booting into Ubuntu remove the usb then run that command in the terminal.

this will give you a list of drives on your system. eg. sda, sdb, sdc.
so from there find the drive you have your installation on and then run
```

sudo grub-install sdX
```  change X to the proper drive annotation, and ater that you system will boot with the option to which installation you want to start up.

See:   [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

You may want to read more on that page for more information about installing and re-installing grub.  If you want to maintain your windows boot loader and not Ubuntu's  then use what has been suggested above.

---

### Post by cwblanch on 2013-02-02
> **varunendra said:**
> Yes, it is a Windows software, and has to be installed there. It only works with versions that use "BCD" as boot loaders, in other words - Vista onwards.

And I used the free version available on Softpedia (there are also other links available though) : [http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml](http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml)

Hope it helps :)
Thank you 
I've downloaded it, but I'm going to give the other suggestion on here a shot before I continue with that.

> **arpanaut said:**
> Would it not just be more simple to install grub into the mbr of the hard drive?

Sometimes the installer (ubiquity) identifies the usb drive as the primary boot drive aka sda, and install grub there so when the usb drive is removed the system will just boot into windows.

So if you have a single hard drive (physical drive) on your system then the simple solution is to just to install grub into the mbr of that drive.
```

sudo fdisk -lu
```will help you identify how your system is identifying your hard drives.
So after booting into Ubuntu remove the usb then run that command in the terminal.

this will give you a list of drives on your system. eg. sda, sdb, sdc.
so from there find the drive you have your installation on and then run
```

sudo grub-install sdX
```  change X to the proper drive annotation, and ater that you system will boot with the option to which installation you want to start up.

See:   [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

You may want to read more on that page for more information about installing and re-installing grub.  If you want to maintain your windows boot loader and not Ubuntu's  then use what has been suggested above.

Ok I got the list of drives, but I'm a bit confused, Ill post what it returned to me:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   116571756    58182454+   7  HPFS/NTFS/exFAT
/dev/sda3       116572158   312580095    98003969    5  Extended
/dev/sda5       116572160   308535295    95981568   83  Linux
/dev/sda6       308537344   312580095     2021376   82  Linux swap / Solaris

```
it says my /dev/sda is my main 160GB HDD, would that mean it would boot from there?
Also it says /dev/sda1 is my boot, and thats the Windows 7 partition, not the flash drive I use.
I might be over thinking this :lolflag:
I'm not sure which drive to specify to install grub to.

---

### Post by varunendra on 2013-02-03
> **arpanaut said:**
> Sometimes the installer (ubiquity) identifies the usb drive as the primary boot drive aka sda, and install grub there so when the usb drive is removed the system will just boot into windows.True, and most probably what is happening here. EasyBCD is just an alternate 'Windows' way. Some find it easier when obvious Grub methods fail :)

As for grub, [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") is the usual recommendation and should be able to fix it automatically. If not, what Mark and I suggested could be next 'easy' fix.

> **cwblanch said:**
> it says my /dev/sda is my main 160GB HDD, would that mean it would boot from there?
Yes, it is the drive you have to boot with. So it would be /dev/sda for you in arpanaut's example. But be aware that installing Grub to sda would overwrite the windows7 mbr which is currently booting that drive.

Although it is usually fairly easy and safe to use grub to boot win7, I'd suggest you to **create a System Recovery cd** from Control Panel > System Backup (or something similar, I don't remember exactly) in win7 before trying anything. Just in case something goes wrong, you can use this cd to restore Win7 MBR and do some other repairs if required.

For your information, sda (or sdb, sdc etc.) means the drive itself, while sda**1**, sda**2**,.. etc. are its partitions. Grub2 doesn't like to be installed in a partition *(although it is possible)*.

* Installing grub in **/dev/sda** would install it on the drive's MBR (Master Boot Record),

* Installing it on any of sda1, sda2, etc. will install it on the given partition's PBR (Partition Boot Record) - you don't want to do that :)

Also, fdisk is listing your sda1 as Boot partition because it IS a boot partition. It doesn't necessarily has to be the one from where you are booting currently. If you are booted from a live USB, it may not show up since it is being used as a 'live cd' *(mounted as a loop device to emulate a cdrom)*, so the live session 'sees' it as a cd.

Hope it clears your doubt :)

Good luck, and don't forget to create the system repair cd before trying anything else.

---

### Post by cwblanch on 2013-02-07
> **varunendra said:**
> True, and most probably what is happening here. EasyBCD is just an alternate 'Windows' way. Some find it easier when obvious Grub methods fail :)

As for grub, [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") is the usual recommendation and should be able to fix it automatically. If not, what Mark and I suggested could be next 'easy' fix.


Yes, it is the drive you have to boot with. So it would be /dev/sda for you in arpanaut's example. But be aware that installing Grub to sda would overwrite the windows7 mbr which is currently booting that drive.

Although it is usually fairly easy and safe to use grub to boot win7, I'd suggest you to **create a System Recovery cd** from Control Panel > System Backup (or something similar, I don't remember exactly) in win7 before trying anything. Just in case something goes wrong, you can use this cd to restore Win7 MBR and do some other repairs if required.

For your information, sda (or sdb, sdc etc.) means the drive itself, while sda**1**, sda**2**,.. etc. are its partitions. Grub2 doesn't like to be installed in a partition *(although it is possible)*.

* Installing grub in **/dev/sda** would install it on the drive's MBR (Master Boot Record),

* Installing it on any of sda1, sda2, etc. will install it on the given partition's PBR (Partition Boot Record) - you don't want to do that :)

Also, fdisk is listing your sda1 as Boot partition because it IS a boot partition. It doesn't necessarily has to be the one from where you are booting currently. If you are booted from a live USB, it may not show up since it is being used as a 'live cd' *(mounted as a loop device to emulate a cdrom)*, so the live session 'sees' it as a cd.

Hope it clears your doubt :)

Good luck, and don't forget to create the system repair cd before trying anything else.

Ok, recovery disk made.
Just to be 100% clear, where exactly do I install the grub in that code? The sda right...?
You said that would overwrite the win 7 mbr, so win 7 wouldn't boot anymore? Or would it boot thru grub?

---

### Post by varunendra on 2013-02-08
> **cwblanch said:**
> Ok, recovery disk made.
Good! Now before trying anything else, it would be a good idea to test that disc.
Boot with it and make sure it gives you the option to repair the current windows installation, fix MBR etc.

> **cwblanch said:**
> Just to be 100% clear, where exactly do I install the grub in that code? The sda right...?
Right.
Try it when you are in your installed ubuntu (not in a live session running from the usb drive). The exact commands would be -
```
sudo grub-install /dev/sda
sudo update-grub
```
The second command will make sure the grub files are configured correctly. If it doesn't work, retry with the USB unplugged (plug-in to boot, remove it and try above two commands)

> **cwblanch said:**
> You said that would overwrite the win 7 mbr, so win 7 wouldn't boot anymore? Or would it boot thru grub?
It would boot through grub (after doing "update-grub" as mentioned above).

Let us know how it goes.

---

### Post by cwblanch on 2013-02-08
> **varunendra said:**
> 
Right.
Try it when you are in your installed ubuntu (not in a live session running from the usb drive). 

I'll give it a shot, but that confused me. It hasn't been running as a live session from the usb. All I do is plug it in to get the grub to show up then unplug it when its done booting. Does that matter at all?

---

### Post by varunendra on 2013-02-09
> **cwblanch said:**
> I'll give it a shot, but that confused me. It hasn't been running as a live session from the usb. All I do is plug it in to get the grub to show up then unplug it when its done booting. Does that matter at all?
Sorry for causing confusion.
From your description so far, it seems that two things are working together to make that usb key the 'key to boot Ubuntu' ;). These (I believe) are -
[LIST]
[*]The USB key has been set as 'First boot device' in the BIOS - intentionally or accidentally doesn't matter. Then -
[*]the GRUB boot loader was therefore installed to the USB key instead of the internal Hard drive.
[/LIST]
The result is -
[LIST]
[*]when there is no USB key plugged in, the boot order defaults to hard disk where it gets windows boot loader and boots straight to Windows.
[*]when the USB key is plugged in, the system boots from GRUB on it, which reads its configuration files from the installed Ubuntu to give you the GRUB menu.
[/LIST]
If so, the USB key 'only' has the GRUB boot-loader and everything else is on the hard disk as should be.

As soon as you install GRUB on the hard disk (/dev/sda), you will no longer need to plug in the USB key. Just make sure to run 'update-grub' immediately after installing GRUB.

Although I explained above to give you an understanding of what is probably happening, if that causes any further confusion, just ignore everything for now and run the two commands from my previous post when you are in Ubuntu.

Should anything go wrong (which is highly unlikely), you already have the system repair cd, don't you? :P

---

### Post by cwblanch on 2013-02-24
> **varunendra said:**
> Sorry for causing confusion.
From your description so far, it seems that two things are working together to make that usb key the 'key to boot Ubuntu' ;). These (I believe) are -
[LIST]
[*]The USB key has been set as 'First boot device' in the BIOS - intentionally or accidentally doesn't matter. Then -
[*]the GRUB boot loader was therefore installed to the USB key instead of the internal Hard drive.
[/LIST]
The result is -
[LIST]
[*]when there is no USB key plugged in, the boot order defaults to hard disk where it gets windows boot loader and boots straight to Windows.
[*]when the USB key is plugged in, the system boots from GRUB on it, which reads its configuration files from the installed Ubuntu to give you the GRUB menu.
[/LIST]
If so, the USB key 'only' has the GRUB boot-loader and everything else is on the hard disk as should be.

As soon as you install GRUB on the hard disk (/dev/sda), you will no longer need to plug in the USB key. Just make sure to run 'update-grub' immediately after installing GRUB.

Although I explained above to give you an understanding of what is probably happening, if that causes any further confusion, just ignore everything for now and run the two commands from my previous post when you are in Ubuntu.

Should anything go wrong (which is highly unlikely), you already have the system repair cd, don't you? :P

Sorry about the delay in getting back, I've been busy.
It worked perfectly, thank you.
Both Ubuntu and windows 7 boot as they should.

---

### Post by varunendra on 2013-02-24
No problem!

Glad it worked, and thanks for taking time for the feedback.
.

---

