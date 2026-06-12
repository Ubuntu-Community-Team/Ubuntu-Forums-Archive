---
title: "Cannot Create Ubuntu 13.04 Startup Disk"
date: 2013-02-19
forum: General Help
---

### Post by Simeo on 2013-02-19
Hello, I'd like to install Ubuntu 13.04 to test and bug report but...... I have a bug. :lolflag:

Creating a startup USB gives me the following errors at the end:  The Application Startup Disk Creator has closed unexpectedly (It crashed) 

It's crashed a few times trying to make 13.04 usb and it won't load 13.04 on boot because I'm receiving an error that bootloader is not installed.

I have the error details still up on my machine. Do you need to know anything before I send it off?

Should I use a live usb or is there another way to install 13.04?  I'll be setting it up separately from my 12.10 install using a home partition so I could default to 12.10 if a problem occurs.

---

### Post by ventrical on 2013-02-19
The raring .isos are working very well as of late and also the SDC problem has been  fixed a while back. What version of Ubuntu are you using to create your startup disk?

---

### Post by Simeo on 2013-02-19
> **ventrical said:**
> The raring .isos are working very well as of late and also the SDC problem has been  fixed a while back. What version of Ubuntu are you using to create your startup disk?

Ubuntu 12.10. iso is a new download.

---

### Post by Simeo on 2013-02-19
> **Simeo said:**
> Ubuntu 12.10. iso is a new download.

Any ideas how I could install 13.04?

12.10 live USB creates and functions with no issues.

---

### Post by ventrical on 2013-02-19
It's often best to have a working install  of Ubuntu to use Startup Disk Creator.  You should be able to make the bootable Startup disk that way.  If You are using another 'live' USB then it would have to be a persitent 'live' USB and you could then try to download the 13.04 daily and stick another USB in another socket and try to install it that way.

 What do you have currently installed on your machine's hdd?

edit:

Ahhh .. ok .. you are running 12.10 and SDC is not working.

have you tried to update you 12.10?  Otherwise I know there have been bugs with SDC off and on intermittently.

---

### Post by Simeo on 2013-02-19
> **ventrical said:**
> It's often best to have a working install  of Ubuntu to use Startup Disk Creator.  You should be able to make the bootable Startup disk that way.  If You are using another 'live' USB then it would have to be a persitent 'live' USB and you could then try to download the 13.04 daily and stick another USB in another socket and try to install it that way.

 What do you have currently installed on your machine's hdd?

Right now I have Ubuntu 12.10 installed on my machine. To test if the error was in the 13.04 iso, startup creator, my usb or 12.10 I tried to create a startup usb using the 12.10 iso instead. The iso successfully created a 12.10 live usb using the same usb 13.04 failed on. I then restarted my machine, this time booting into USB and it was successful. 

However 13.04 will not do this using startup disk creator and the currently available iso... at least not for me.

---

### Post by ventrical on 2013-02-19
Thats very odd as I have never run across that scenario before.  The only thing I could assume is that perhaps the 13.04 is corrupt.. but  it is unlikley, however, if your Quantal install is producing bootable Quantal 'live' USB then there should be no problem with 13.04.

 How big is the USB (size in GBs?)

---

### Post by ventrical on 2013-02-19
Try the 'Discard on shutdown , unless you save them elsewhere' option. That has worked a lot of times for me.

---

### Post by Simeo on 2013-02-19
> **ventrical said:**
> How big is the USB (size in GBs?)

Right. It seems odd to me too. I tried downloading the iso file a couple times today to verify and still having the same issues. The USB is 2GB.

The iso will go through the whole process of being created to a live usb, then at the very end startup disk creator will crash. Perchance is there another way I could try to make a live usb?

---

### Post by Simeo on 2013-02-19
> **ventrical said:**
> Try the 'Discard on shutdown , unless you save them elsewhere' option. That has worked a lot of times for me.

Ok, will try now and report back.

---

### Post by ventrical on 2013-02-19
> **ventrical said:**
> Try the 'Discard on shutdown , unless you save them elsewhere' option. That has worked a lot of times for me.


Just quoting myself here .. or you could try UnetBootin or wait for someone else to jump in.

Regards,
Ventrical

---

### Post by ventrical on 2013-02-19
Also .. is that raring-desktop-amd64.iso ?

---

### Post by mc4man on 2013-02-19
> **Simeo said:**
> 
The iso will go through the whole process of being created to a live usb, then at the very end startup disk creator will crash. Perchance is there another way I could try to make a live usb?
As mentioned you could use  UnetBootin

If SDC is crashing then usually it will produce a .crash. (/var/crash/
Take a look, if there right click on > Open with report a problem & see what the crash is.

---

### Post by Simeo on 2013-02-19
> **mc4man said:**
> As mentioned you could use  UnetBootin

If SDC is crashing then usually it will produce a .crash. (/var/crash/
Take a look, if there right click on > Open with report a problem & see what the crash is.

It did produce a crash report which I sent off each time, but maybe since my last reboot it doesn't appear. 

I forgot about Unetbootin but..... 13.04 finally worked on the last one. I checked the "Discard on shutdown , unless you save them elsewhere" option (which I had done before) but it worked this time. I'm currently in the 13.04 live usb making this reply and will create the new install. 

Quick question: I'm using a shared home partition with one partition being my 12.10 and will make another partition 13.04. Looking at gparted 12.10 only takes up 5gb of space. What should I resize my OS partitions to?

PS Thank you for being awesome, ventrical.

---

### Post by ventrical on 2013-02-19
At least 10GBs to be safe .... but how big is the hdd?

---

### Post by Simeo on 2013-02-19
> **ventrical said:**
> At least 10GBs to be safe .... but how big is the hdd?

500gb. I have 150gb for Win7 and the rest is for Ubuntu /, swap, and /home

---

### Post by ventrical on 2013-02-20
> **Simeo said:**
> 500gb. I have 150gb for Win7 and the rest is for Ubuntu /, swap, and /home


I guess then it would depend how much experimenting you would want to do with raring 13.04. 10GB is sufficient for experimenting ... but a larger partition would suffice if you plan to make it a rolling distro.

---

### Post by Simeo on 2013-02-20
> **ventrical said:**
> I guess then it would depend how much experimenting you would want to do with raring 13.04. 10GB is sufficient for experimenting ... but a larger partition would suffice if you plan to make it a rolling distro.

Ok I understand that part. I guess I'd like to know how much space would be needed for a permanent/rolling OS because now that I'm using the separate /home partition I'd like to be able to devote as much space as possible to my home files (music, documents, etc). 

Stupid Win7 on a bare bones install (programs only) is already taking up 100gb of my hard drive. -_-*

---

### Post by ventrical on 2013-02-20
I have one machine with a 500GB SATA (no windows) with 4 partitions at about 120GB per partition. I am about to back up all my important work files and reformat because I upgraded the BIOS and now have some issues with installing certain filesystems.

I had Maveric, Raring, Precise and Quantal all on the same drive.

---

### Post by The Cog on 2013-02-20
I believe you can create a startup stick with recent Ubuntu images purely by using dd to transfer the iso image to the stick. Apparently, this is made possible by some fancy dual-format voodoo magic. It worked for me after I found that the startup disk creator kept crashing.

---

### Post by Simeo on 2013-02-20
> **ventrical said:**
> I had Maveric, Raring, Precise and Quantal all on the same drive.

:shock:

---

### Post by ventrical on 2013-02-20
> **ventrical said:**
> I have one machine with a 500GB SATA (no windows) with 4 partitions at about 120GB per partition. I am about to back up all my important work files and reformat because I upgraded the BIOS and now have some issues with installing certain filesystems.

I had Maveric, Raring, Precise and Quantal all on the same drive.


Actually I had to belay the above as I discovered it was yet something else. So all is working well here now.

To answer your question specifically, I would use about 110GBs for a Raring Partition.

---

### Post by Simeo on 2013-02-20
> **ventrical said:**
> Actually I had to belay the above as I discovered it was yet something else. So all is working well here now.

To answer your question specifically, I would use about 110GBs for a Raring Partition.

Is that so it has it's own home folder? I never knew a Ubuntu distro to take up so much space without personal files. Right now I'm using 12.10 with a separate home partition. 12.10 is using about 5.8gb in a 140gb partition and my /home partition is using 180gb. 

Could I do the following without issues: Resize my 12.10 partition to 20gb and create a 20gb partition for 13.04 while having them share the /home partition of 300gb?

That way I don't need to touch my personal files while I'm testing 13.04 and I'll be able to use 13.04beta in the same way I use my stable OS for work (at the same time providing a safety net in case 13.04 breaks).

I figure using 13.04 (like normal) and reporting any bugs that come along is the best way for me to contribute. Will 13.04 'break' my home partition or render 12.10 unable to use the /home partition?

---

### Post by ventrical on 2013-02-20
> **Simeo said:**
> Is that so it has it's own home folder? I never knew a Ubuntu distro to take up so much space without personal files. Right now I'm using 12.10 with a separate home partition. 12.10 is using about 5.8gb in a 140gb partition and my /home partition is using 180gb. 

Could I do the following without issues: Resize my 12.10 partition to 20gb and create a 20gb partition for 13.04 while having them share the /home partition of 300gb?

That way I don't need to touch my personal files while I'm testing 13.04 and I'll be able to use 13.04beta in the same way I use my stable OS for work (at the same time providing a safety net in case 13.04 breaks).

I figure using 13.04 (like normal) and reporting any bugs that come along is the best way for me to contribute. Will 13.04 'break' my home partition or render 12.10 unable to use the /home partition?

  There would most likely be issues (in my opinion ) if you did it that way. The best way to install raring is to do a side by side (resize). I mean I haven't tried it the way you have it suggested. Resizing the partition can be touchy and finicky.  Most often I use a lot of space. I have a laptop with a 120GB SATA and I made small partitions on that  and I ran into some difficulties in the sense that it takes a little more time to organize partitons if you intend on delelting partitons in the future.

  It seems to me that  you are intent on keeping your Windows 7 in tact. Partitoning a drive with a development release *could* bork your system.  For the most part Ubuntu is rock solid and there is not much to worry about .. but there is always the chance.

 As long as I leave ample space for partitions I have not had a problem. So I would just allow the partitioner to split by default the 140 to approximately 70 GBs or there abouts for the quantal install and the raring install and raring will also create it's own Home directory and it you want to mount your quantal home then nautilus will allow you to do that easily with both quantal and Windows 7.

---

### Post by Eric Buist on 2013-07-13
Seems now everyone is having different problems while this works for majority, other things work. I am stuck with the exact same issue, tried with Discard on shutdown, same result. The tool copies the files over my 2Gb USB stick then dies with the unexpected error. Seems I would have to install 12.10 then dist-upgrade to 13.04, but my goal is to perform a clean install of 13.04 to iron out other issues. Other than that, the only remaining options iis to remaster the ISO to trim it down to a CD-R (seems a LOT of work!) or set up a network install (seems a lot of work as well). So I need to find some place to order a USB stick with Ubuntu 13.04 and wait weeks to get it. Better off trying out another Linux distribution then.

---

### Post by VMC on 2013-07-13
> **The Cog said:**
> I believe you can create a startup stick with recent Ubuntu images purely by using dd to transfer the iso image to the stick. Apparently, this is made possible by some fancy dual-format voodoo magic. It worked for me after I found that the startup disk creator kept crashing.
Yes, Ubuntu now uses "Hybrid" ISO files, so the dd command will work:
[Replace **sdb** with your usb flash device location]
```
[COLOR=#000000][FONT=Consolas]sudo dd if=/path/to/file.iso of=/dev/sdb bs=1M[/FONT][/COLOR]
```

_Use the 'dd' command with the up most caution._

---

### Post by Eric Buist on 2013-07-13
Figured out SDC was not picking up the right ISO after I chose it from the Other button. I managed to get it to pick the Ubuntu 13.04 ISO, the creation process went further but crashed again. Seems I have to limit myself to virtual machines or tackle the network-based install. No regular user will attempt such convoluted process. This just makes no sens to package a Linux distro requiring so much fiddling around to install. I hope 13.10 will at least trim down the ISO size to 700Mb. Any variant of Ubuntu with such an ISO file? Booting up from a CD is slower but at least it works.

---

### Post by Eric Buist on 2013-07-13
The dd command did the trick. Of course I double-checked my target device to not overwrite one of my partitions. I am now booted to the live USB. Thanks.

---

### Post by coffeecat on 2013-07-13
We're now well into the 13.10 dev cycle. 

*Thread moved to **General Help*** from the U+1 forum.

---

### Post by jerrylamos on 2013-07-13
> **Simeo said:**
> ...Should I use a live usb or is there another way to install 13.04?  I'll be setting it up separately from my 12.10 install using a home partition so I could default to 12.10 if a problem occurs.
I boot the development test iso's directly from the hard disk.
zsync the .iso and put it into the first directory of a partition.
Example below uses partition 6 on the boot hard drive
```
sudo gedit /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "saucy64 13.10" {
set isofile="/saucy-desktop-amd64.iso"
loopback loop (hd0,6)$isofile 
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
save
exit
sudo chmod 777 /etc/grub.d/40_custom
sudo update-grub
sudo grub-install /dev/sda            (whatever /dev/sd? you boot from)
sudo reboot
```

Faster for me than creating a USB.  Of course, does not test the ability/inability of whatever ubuntu you're using to create a USB.
Sometimes it's /casper/vmlinuz.efi and sometimes it's /casper/vmlinuz.  With file manager select the .iso, which may allow you to browse the .iso to see which vmlinuz it is.

After rebooting, the grub entry you just made with 40_custom should be on the bottom.
Select & see if it boots....
Play with the live image if you wish.
Then
Ctrl-Alt-t
to get a terminal session
df
to see which /dev is the isodevice, no surprise in this case /dev/sdb6
sudo umount -rl /dev/sdb6
exit the terminal session if you wish
open the install.

A bit long winded to read about after doing this a bunch of times I usually remember everything...

Note, I'm testing saucy on a USB hard drive, an SSD.  
The pc is set up to boot on the USB so during boot grub thinks the USB is /dev/sda
After boot, file manager, gparted, and install show it as /dev/sdb
Go figure.
BTW, if you intend to boot off a USB hard drive like I do, watch that install puts the boot image on /dev/sdb.  Whatever your setup is.
Also you can have multiple 40_custom entries for multiple .iso's.  Repeat and modify everything from menuentry to the final }

---

### Post by lptr on 2013-10-30
> **Eric Buist said:**
> Figured out SDC was not picking up the right ISO after I chose it from the Other button. I managed to get it to pick the Ubuntu 13.04 ISO, the creation process went further but crashed again. Seems I have to limit myself to virtual machines or tackle the network-based install. No regular user will attempt such convoluted process. This just makes no sens to package a Linux distro requiring so much fiddling around to install. I hope 13.10 will at least trim down the ISO size to 700Mb. Any variant of Ubuntu with such an ISO file? Booting up from a CD is slower but at least it works.

=D>
Great job Canonical.

Recently I found out, that this dreaded create startup usb disk (nonsense) is still valid for Ubuntu 13.10, either. The prog uses to crash without an understandable hint what went wrong. It not even dumps something to /var/log/*. It simply dies. Sometimes the crash report comes up. But the messages don't lead to a solution, either.

That program seems to have at least two problems built into.
1st) It needs a BLANK FORMATED FAT USB STICK. The cleanup routine seems to have several internal problems or need some unknown prerequisites.
2nd) The USB stick MAY NOT HAVE MORE THAN ONE FAT PARTITION. If it has the boot image installer has problems.

In the past I always used to have a second FAT partition (at least on drives of size 8 GB or larger) to have persistent data on it. With this approach this does not work anymore.

My workaround was the following:
I first have had to install netbootin from repos on a 12.10 machine to get a working 13.10 kubuntu install stick. Booting from this one I could create a 13.10 ubuntu install USB stick. This one I used again (with above mentioned two preconditions/restrictions) to create the final kubuntu install USB stick. 

Netbootin does provide its own (character based) boot menu. Therefore I did overwrite that kubuntu install disk another time.


As Eric stated out: It would be highly appreciated and a very good idea to make this procedure as bullet proof as possible. Or to at least provide another simple way to bring Ubuntu painless on a new machine. DVD is a bad choice as everything lasts to long.

Hope the tests with the server image will bring more joy and less surprises with it.

---

### Post by lptr on 2013-10-30
> **coffeecat said:**
> We're now well into the 13.10 dev cycle. 

*Thread moved to **General Help*** from the U+1 forum.

True, but the trouble stays... #-o

---

### Post by coffeecat on 2013-10-30
> **lptr said:**
> True, but the trouble stays... #-o

@lptr, no need to smite your brow. :) It's why I moved the thread over three months ago. It was in the Ubuntu +1 development forum. It will get wider exposure here in General Help. The alternative was to leave it where it was and close it, which would have been less helpful.

---

