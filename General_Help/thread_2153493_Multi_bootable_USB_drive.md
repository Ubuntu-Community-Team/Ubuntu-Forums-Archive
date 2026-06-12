---
title: "Multi bootable USB drive?"
date: 2013-06-11
forum: General Help
---

### Post by TNFrank on 2013-06-11
Wasn't sure where to put this so I'll stick it here.  Is there a way that I can place multi copies of an OS onto a single USB drive and make them all bootable?   I have a 32GB USB thumb drive that I've used with Startup Disk Creator when I want to install Ubuntu onto a system but I always format it and only have a single bootable copy of the OS(32 bit for my system, 64 bit for my wife's) and I'd like to store both in bootable form onto the USB drive for future use. Can this be done or will it confuse the computer as to which copy to boot to on startup?  It seems I saw a TechZilla show where they did just this thing but until I get my WiFi problems worked out my Roku player is off line ad I can't watch the shows.
 Would it just be easier to buy a couple 2GB USB drives and put a copy of each OS on each drive for future use or maybe I could just try to burn a bootable copy to CD again(something that didn't work too well first time I tried it) and just use CDs.  Anyway, thanks for any help ya'll can give.

---

### Post by gigenieks on 2013-06-11
> 
Is there a way that I can place multi copies of an OS onto a single USB drive and make them all bootable?

Yes, [check this!]("https://help.ubuntu.com/community/Grub2/ISOBoot")

As far as I know, you just install GRUB 2 on you USB drive. Copy needed iso files. Configure your grub.cfg accordingly and you should be ready to go.

[check ajgreeny post with some examples]("http://ubuntuforums.org/showthread.php?t=2153159&p=12685435#post12685435")

Is this what you needed?

---

### Post by TNFrank on 2013-06-11
I'd like to make bootable CD's but here's the problem I run into.  I open "Startup Disk Creator" and I see my downloads but I don't see my CD drive with the blank disk in it so I can choose it to make a bootable startup disk. 
 Now if I install the USB drive it'll see it and I can write to it and make it bootable, not sure what gives here.  Does the Boot Loader take up so much space that the 700MB CD isn't a large enough volume to write to or what?

---

### Post by TNFrank on 2013-06-11
I plug in my USB drive and it automatically sees it and wants to write a bootable "disk" to it but it won't see the CD drive, what gives???????

---

### Post by TNFrank on 2013-06-11
Ok, I opened the files and looked to "extract" them and they're both over 727MB so that may be why the startup disk creator isn't seeing the CD, there's just not enough room on it to write the file to. Funny that they're both under 700MB at download though.

---

### Post by Cheesemill on 2013-06-11
All recent versions of Ubuntu are too large to fit on a CD, you need to write the iso file to a DVD.


If you have access to a Windows machine then you should take a look at [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") for creating a USB drive with multiple bootable iso's on it.

Alternatively there are also hardware solutions such as the Zalman [ZM-VE300]("http://www.zalman.com/global/product/Product_Read.php?Idx=674"), [ZM-VE400]("http://www.zalman.com/global/product/Product_Read.php?Idx=750") and the [isostick]("http://isostick.com/"). I'm quite tempted by one of these hardware devices myself as it will get rid of my massive piles of installation media CD's as well as boot from ***any*** iso (grub cant boot from Microsoft or some other iso files).

---

### Post by TNFrank on 2013-06-11
So I guess I either need to buy a couple 2GB USB drives to store the .iso's on or get a couple DVD's. Either way I'd like to keep a bootable copy of both 32 and 64 bit Ubuntu 12.04 on hand "just in case" I need to do a reinstall on my or my wife's computer. Anyway, thanks for the help. ;)

---

### Post by gigenieks on 2013-06-11
> 
So I guess I either need to buy a couple 2GB USB drives to store the .iso's on or get a couple DVD's.

No, you don't. (Did you check links in [#2 post]("http://ubuntuforums.org/showthread.php?t=2153493&p=12686871#post12686871")??)

[In fact, I just did it myself.]("http://ubuntuforums.org/showthread.php?t=2153159&page=3&p=12687019#post12687019")

---

### Post by C.S.Cameron on 2013-06-11
MultiBootUSB automates the process of making multi boot grub2 USB drives and works with dozens of different distributions.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by TNFrank on 2013-06-11
I'm not trying to create a "Live" USB Drive to boot to, I'm trying to store each op system on something so if I need to install it onto a computer I'll have it to boot to for a complete install.  Seems like if I had two differen Op Systems on a single USB the computer wouldn't know which one to boot to.  Or does it open up and give me the option of installing the 32 bit op sys or the 64 bit op sys??

Let me try and explain it this way. I'm not trying to create a USB disk to boot to for the purpose of running an op system, I'm just trying to store an os so I can install it on either my computer if something happens to it or on other computers in place of the current op system. 
 Yes, I understand I can boot to and run another os from a USB but that's not what I'm wanting to do. I want something akin to an install disk to install an os on a computer.

---

### Post by gigenieks on 2013-06-11
Just added Ubuntu 13.04 (64 bit) to my USB drive.

> 
I'm just trying to store an OS so I can **install** it on either my computer if something happens to it...

When you login in live environment you can install if you want. Or just use it temporarily. 

I now have an 16 USB flash drive which contains:
[LIST]
[*]Ubuntu 13.04 (32 bit)
[*]Ubuntu 13.04 (64 bit)
[/LIST]
And if I choose I can install whichever I choose.
Were you worried you will have just "live environment" without install capabilities? Or am still missing something?

---

### Post by TNFrank on 2013-06-11
> **gigenieks said:**
> 
Were you worried you will have just "live environment" without install capabilities? Or am still missing something?

Because normally if you're running an OS you can't write over it with what it would see as "another" OS, right?
So you're saying I can just put all kinds of stuff on my USB drive AND have a couple copies of Bootable(i.e. installable) Ubuntu on it as well and when I boot to the USB the computer will let me pick which one I'd like to install or what?
 That'd be really cool if that'd be the case.  Can I just use the Startup Disk Creator in Ubuntu to save bootable copies to the USB or will I need to run a special program, like was listed above, in order to do this? 
 I'm pretty new to Ubuntu(or Linux for that matter) and was living fat, dumb and happy with my iMac and OS X 10.3.9 for close to 11 years so a lot of this stuff is out of my knowlege base.  
I really do want to go back to school and learn about Linux and maybe even get a job doing this kind of stuff. Don't care if I am 52, it's never too late to learn something new. ;-)

---

### Post by TNFrank on 2013-06-11
Oh, an not to change the subject(well, maybe a little bit) ya'll have got me curious about making a "Live" USB to boot to in order to try out different "flavours" of Linux without having to replace my (now) beloved Ubuntu 12.04.  That way I can see what Linux Mint is like or other versions of Linux from the USB and not mess with my op system. Especially since my USB drive has 32GB on it, more then a lot of hard drives use to have,LOL.  I can run the entire OS form the USB then shut down, unplug and start back up into Ubuntu which would be VERY COOL. :D
So, how would one go about pulling off such a thing?  Baby steps please, remember I'm a "noob" at Linux so be gentle.8-[

---

### Post by gigenieks on 2013-06-11
I'm going to sleep soon.. Will try to give detailed answer tomorrow. Patience. Good luck. ;-)

---

### Post by TNFrank on 2013-06-11
> **gigenieks said:**
> I'm going to sleep soon.. Will try to give detailed answer tomorrow. Patience. Good luck. ;-)

Wow, Latvia, very cool.  My grandpa on my mother's side of the family was Czech or Yugoslavian(jury is still out) but I've got half Slavic blood in my veins. Anyway, sleep well pard and hopefully we can get this figured out, I'd still like to try Linux Mint 13 without messing up my Ubuntu 12.04.  Talk to ya' later. ):P

---

### Post by C.S.Cameron on 2013-06-11
> **TNFrank said:**
> Because normally if you're running an OS you can't write over it with what it would see as "another" OS, right?
So you're saying I can just put all kinds of stuff on my USB drive AND have a couple copies of Bootable(i.e. installable) Ubuntu on it as well and when I boot to the USB the computer will let me pick which one I'd like to install or what?
 That'd be really cool if that'd be the case.  Can I just use the Startup Disk Creator in Ubuntu to save bootable copies to the USB or will I need to run a special program, like was listed above, in order to do this? 
 I'm pretty new to Ubuntu(or Linux for that matter) and was living fat, dumb and happy with my iMac and OS X 10.3.9 for close to 11 years so a lot of this stuff is out of my knowlege base.  
I really do want to go back to school and learn about Linux and maybe even get a job doing this kind of stuff. Don't care if I am 52, it's never too late to learn something new. ;-)

Once you have created a multiboot drive with MultiBootUSB, you can, in most cases, just drop an iso of a new version of an O/S onto the USB and revise the grub.cfg file.

When you boot the drive you get a menu listing options of what iso to boot.
Once you have booted the iso you generally have the option to try or install.

I still learn stuff occasionally and I am 63.

---

### Post by Rebelli0us on 2013-06-11
> **TNFrank said:**
> I'm not trying to create a "Live" USB Drive to boot to, I'm trying to store each op system on something so if I need to install it onto a computer I'll have it to boot to for a complete install.  Seems like if I had two differen Op Systems on a single USB the computer wouldn't know which one to boot to.  Or does it open up and give me the option of installing the 32 bit op sys or the 64 bit op sys??

Let me try and explain it this way. I'm not trying to create a USB disk to boot to for the purpose of running an op system, I'm just trying to store an os so I can install it on either my computer if something happens to it or on other computers in place of the current op system. 
 Yes, I understand I can boot to and run another os from a USB but that's not what I'm wanting to do. I want something akin to an install disk to install an os on a computer.

You can install as many distros as you want on a USB flash drive. Install each on a different partition, they are all bootable from the Grub menu and they can all share the same swap partion. 

You can also have Desktop CD on USB flash too, 4 GB flash drives are very inexpensive.

---

### Post by oldfred on 2013-06-11
I have several flash drives. My 4GB drives have just grub installed and I have to manually create a grub.cfg file to boot the ISO. I fit as many ISO as I can on that 4GB. Some like gparted, Boot-Repair, Supergrub are smaller and all fit with a couple of Ubuntu versions, so I have an installer and repair flash drive.

On my larger 16GB flash  drive drive I have a 8GB partition with a full install of Ubuntu and 8GB for data. I this copy a couple of ISOs into the data partition to boot those.

Using unetbootin normally reformats entire flash drive for one ISO. It was back when we normally had 1 to 4GB flash drives and only had one install per flash drive.

       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition if grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)
Reported to have a few typos? But shows process on one page
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

---

### Post by C.S.Cameron on 2013-06-11
> **oldfred said:**
> 
Using unetbootin normally reformats entire flash drive for one ISO.



My experience is that UNetbootin, (Win version at least), installs to the first partition on a flash drive, ie using gparted you can format the drive with first partition FAT32 and the next partition ext2, (labeled casper-rw), to make an USB with persistent partition.

I have not found a way to make a multiboot USB with it or with usb-creator.

Edit:
Windows and applications depending on it can only see the first partition on a flash drive.

---

### Post by TNFrank on 2013-06-11
I watched one of the Hak5 shows today on Revision3 and they went through the steps to make a multi-boot USB and wow, was it totally over my head.  If I have any chance of doing this I need a step by step, spelled out in reasonable detail of what to do, what to install when and how, basically it'd be a PITA for someone but if there's someone who'd know how to explain it I'd really appreciate it.
 I picked up an 8GB SanDisk today at Wally World to play with.  I only see FAT format on Ubuntu 12.04, didn't see FAT32. From what they said on Hak5 if you go FAT you can only access 2GB, I'd need FAT32 to access all of the USB drive. 
I guess we'll get it worked out eventually so that I can put Linux Mint 13 and maybe a couple other distros onto the drive to boot to so I can check them out without messing with Ubuntu on my hard drive.

---

### Post by TNFrank on 2013-06-12
Ok according to Disk Utility when I look at my formatted 8GB USB drive that I did in "FAT" it says it FAT 32bit, is that the same as FAT32? I know, that's a stupid question and I could probably get my A+ Cert. book out and look it up but it's late here and I'm too tired right now.
 So, anyway, I downloaded an .iso copy of Linux Mint 13 Xfce that I'd like to put on the 8GB USB drive and make it bootable so I can check it out without doing a total install on my hard drive. 
What are the steps, software, ect that I need to do now? Thanks.

---

### Post by sudodus on 2013-06-12
There are several ways to make a multi-boot USB drive. I think you need to decide, if you want to understand the basics and make it yourself or get it more or less ready, so that you only follow the instructions like a cook-book. Maybe the cook-book approach is good to get something that works quickly, but then you see the limits, and you need to know more to get all the features you want.

*Edit*: It may be simpler to have several small and cheap USB pendrives and have one system on each of them, because some iso files are hard or impossible to boot from grub 2 or from other multiboot USB drives.

Anyway, I have recently edited the Ubuntu wiki page and an Ubuntu Forum tutorial about this subject. I think the method to use grub2 and iso files are good for your purpose.

[Ubuntu Wiki - FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

[URL="http://ubuntuforums.org/showthread.php?t=1958073"]Ubuntu Forums tutorial "Howto make USB boot drives" 
[/URL]

---

### Post by TNFrank on 2013-06-12
> **sudodus said:**
> There are several ways to make a multi-boot USB drive. I think you need to decide, if you want to understand the basics and make it yourself or get it more or less ready, so that you only follow the instructions like a cook-book. Maybe the cook-book approach is good to get something that works quickly, but then you see the limits, and you need to know more to get all the features you want.

*Edit*: It may be simpler to have several small and cheap USB pendrives and have one system on each of them, because some iso files are hard or impossible to boot from grub 2 or from other multiboot USB drives.

Anyway, I have recently edited the Ubuntu wiki page and an Ubuntu Forum tutorial about this subject. I think the method to use grub2 and iso files are good for your purpose.

[Ubuntu Wiki - FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

[URL="http://ubuntuforums.org/showthread.php?t=1958073"]Ubuntu Forums tutorial "Howto make USB boot drives" 
[/URL]

The second tutorial "How to make  USB boot drives" was interesting. I'm using Terminal to clean the 32GB USB drive as I type this.  Once it's done do I need to format it just FAT or do I need to put a Master Boot Record on it too? 
Also, would Startup Disk Creator in Ubuntu 12.04 work in creating a "Live" USB to boot to in order to run say, Linux Mint or is SDC only used to make install copies?

P.S. 
Does it normally take a while to do the "sudo dd if=/dev/zero of=/dev/sdg bs=4096" operation?

---

### Post by TNFrank on 2013-06-12
Ok, so I've had "sudo dd if=/dev/zero of=/dev/sdg bs=4096" running on my 32GB USB for almost an hour. How the heck long does this command take?

---

### Post by C.S.Cameron on 2013-06-12
I was about to recommend Grub-n-iso to you myself
You will be able to drop the Mint iso on it and edit the second menuentry in grub.cfg.

Yes dd can take a very long time to run.

You can install Grub-n-iso to usb using Imagewriter, (both Windows and Linux versions).
It is a GUI and seems faster than dd.

---

### Post by oldfred on 2013-06-12
dd is slow, but I am not sure it should take that long. But you really did not have to use dd to zero drive. Just reformatting and repartitioning should be enough.

Partitioning is separate from formatting of each partition. If you are using with Windows and want to be able to copy data to Windows you need the first partition to be Windows compatible, FAT32 or NTFS. Then all the rest of the partitions can be Linux formatted. Windows only sees the first partition on flash drives, and Windows does not see Linux formatted partitions anyway.

My 32GB drive will not be used with Windows so I did not make its first partition Windows compatible. And I expect to build a new UEFI compatible system soon, so I partitioned my new 32GB flash with gpt not MBR(msdos) so I could make the first partition efi per UEFI standards. I then had to include a bios_grub partition to allow grub to install correctly with my current BIOS boot system. I then just installed grub to MBR.

---

### Post by sudodus on 2013-06-13
> **TNFrank said:**
> Ok, so I've had "sudo dd if=/dev/zero of=/dev/sdg bs=4096" running on my 32GB USB for almost an hour. How the heck long does this command take?

dd asks no questions and says nothing until it is finished unless you 'kick on it', send the USR1 signal to it with the kill command. See ```
man dd
```

```
       Sending a USR1 signal to a running `dd' process makes it print I/O statistics to standard error
       and then resume copying.

              $ dd if=/dev/zero of=/dev/null& pid=$!
              $ kill -USR1 $pid; sleep 1; kill $pid

              18335302+0  records  in 18335302+0 records out 9387674624 bytes (9.4 GB) copied, 34.6279
              seconds, 271 MB/s

```

So when you are curious or lose patience, you can get a progress report including the average write speed.

I would not kick on it every second as the example, maybe once every minute, so I'd use **[FONT=courier new]sleep 60[/FONT]** instead. And the write speed to a USB 2 drive might be between 5 and 30 MB/s.

---

