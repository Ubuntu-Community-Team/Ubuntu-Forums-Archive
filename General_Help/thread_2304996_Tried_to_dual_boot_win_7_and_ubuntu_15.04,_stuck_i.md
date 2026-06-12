---
title: "Tried to dual boot win 7 and ubuntu 15.04, stuck in lilo neither system works"
date: 2015-12-01
forum: General Help
---

### Post by silas3 on 2015-12-01
Ok to cut a long story short I tried to install ubutnu 15.04 on a win 7 using the ftp net installer because my usb storage sucks :p anyway I got through the install fine until I go to installing grub, nothing worked so I decided to go for lilo, and after the install lilo gave me an error message and dropped to shell, I can't boot into anything. Is there any hope at all?

---

### Post by yancek on 2015-12-01
"Nothing works" won't get much help.  What exactly happened after you installed Grub to the MBR of the primary partition?  Or did you install it somewhere else?  Probably you would have been better off posting while you still had Grub since Ubuntu has been using Grub2 for 6 years and Ubuntu users are more familiar with it.  Posting more info such as the output from boot repair would be helpful if you can download it to another machine and create a bootable CD/flash drive.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by silas3 on 2015-12-01
Ok sorry about being unclear, when I tried installing grub on MBR it said it couldn't install on /dev/sba and that it was a fatal error so I tried other /def/sb's that help forums suggested might help, but it always gave me the same message, so I went with Lilo because it appeared as a different bootloader. Now it's giving me that error message and drops me to shell. I can still access everything bios, so i can use a less than 1 gig flash drive (told you it sucked), and using the net installer to check the partitions, everything is intact. Will boot repair take up more than 1 gig? If not I'll have to just go with a cd, which will be incovienent but not (I hope) Impossible. And no, buying a new flash drive is not practical for me. I will look into boot repair right now.

---

### Post by efflandt on 2015-12-01
I don't know if that is a typo or if you really did try to put grub on /dev/sba (which does not exist). Your first hard drive or similar is /dev/sda (d as in disk or disc or drive?). Your second drive if you have one would be /dev/sdb.

---

### Post by silas3 on 2015-12-02
Ok yes typo :p anyway can you use boot repair without a live version of linux? Anyway by next morning I hope to have "burned" the iso file for boot repair on my usb, and hopefully it will work. I'll tell you what happens and give you the log if needed.

---

### Post by Geoffrey_Arndt on 2015-12-02
Silas3, to actually get any useful help, the full specs of your PC should be posted.   It makes a huge difference on what to install, how to install it, and so on.

>  cpu type 
>  ram amount
>  type of gpu or graphics chip/card (for example, intel integrated, nVidia GeForce, ATI, etc.)
>  what disk partition/setup (using one drive, two, what file format (ext3, 4, reiser, etc.))
>  if running UEFI or standard BIOS system
>  if running Ubuntu as only OS or if running a dual-boot (Ubuntu & Win 7?)

Lilo is fine for a bootloader if you decide to run Slackware . . . . not so good on Ubuntu.

---

### Post by silas3 on 2015-12-02
Ok I'll do my best to give you the specs, but it will be a bit hard since I can't use a program to check them.

cpu: according to the sticker is an intel celeron (don't know which)
ram: from memory it is 4 gb (3.75 usable)
gpu: An old EOL nvidia nforce I think 6200 but I couldn't swear by it.
disk partitions: I have several disk partitions set for both windows and ubuntu, one over 100 gig partition for windows plus the small system reserved partition and the "homemade" 10 gig partition for linux root, an about 6 gig partition for linux home and then a way inferior 1.1 gig partition for linux swap, which I was planning to increase. The windows is ntfs and ubuntu is ext4.
UEFI/BIOS: I do not know but it is an older emachine computer, and I think it's bios, but I'm not sure.
OS: I had working windows 7 and was intending to dual boot that and ubuntu 15.04 when the above mentioned problem happened. I know this is less than satisfactory, but I do not know how to check my specs when I only have access to usb, busybox from lilo and what I think is BIOS. I have the boot repair ISO and I will be burning it on usb soon, so I should have more info soon!

---

### Post by silas3 on 2015-12-02
And stupid question, what would happen if I installed grub over lilo? I have access to the install, and I have everything installed there except grub. Or is the problem deeper than grub/lilo?

---

### Post by yancek on 2015-12-02
The purpose of running the boot repair is to gather detailed information on your drives/partitions, boot files and other information and it would be best if you just used the Create BootInfo Summary option to post here rather than trying to repair.  You should get some advice from people who are more familiar with Ubuntu/Grub.  Boot repair will fit on a CD as it is under 700MB.

---

### Post by silas3 on 2015-12-02
Well darn I got overexicted and went straight for repair. Hopefully repair won't break anything? And as you can tell, it booted fine. And the repairs just finished, and it gave me the url, should I post it here or is there sensitive info? And thanks for the help so far. Edit: By booted I mean the repair, I have no idea if the normal OS's work or not (yet)

---

### Post by silas3 on 2015-12-02
Ok I am very anxious and excited and nervous at the same time because grub is loading now and I chose ubuntu. It's not doing anything? My screen is blank. Should I wait or hard reboot?

---

### Post by oldfred on 2015-12-02
Never hard reboot. That often corrupts file system. Then you have to use live installer from DVD or flash drive to make sure all partitions are unmounted to run fsck to repair it.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

At grub menu you need nomodeset becuase of your nVidia card.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you do not get grub menu, hold shift key from BIOS screen until menu appears.

You then need to install correct nVidia driver. With older nVidia cards there are several legacy drivers. After a while they freeze a driver for older cards. The new features in new driver only work with new cards and may actually interfere with older card.

Do not download from nVidia, but use system settings, software updates, and drivers tab to find & install correct driver from Ubuntu repository. It has the older drivers. Only with a very new card may you need to add another repository (ppa) that has even newer drivers.
       
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by silas3 on 2015-12-02
Hello there! I am pleased to say that although ubuntu crashes, I can tell it "works" because I clicked ctrl alt delte and it rebooted, which I don't believe to be a bios feature, so I'm hoping linux is doing it. Anyway grub installed properly and I can boot to windows! I have to take a break from this for a bit, crashing and repairing your whole computer is a wee bit stressful apparently, but I have a quick question. I can handle changing the grub settings, but what does getting a different nvidia driver do?

---

### Post by oldfred on 2015-12-02
Default boot is with open source driver for video, which may or may not work reasonably well. 

With 14.04 and my nVidia 620gt I do not see much difference. With my older 9600GT, I only got black screen, but system was still booting. I then added nomodeset to boot into low quality graphics and installed nVidia driver.

Do not use control, alt Delete. Use R-E-I-S-U-B as posted above.

---

### Post by silas3 on 2015-12-02
Ok yes I will do that from now on, but I have a problem. I changed the grub setting to ...."nomodeset quiet splash" but the screen is still blank, albeit there is some almost invisible improvement. My power button on my monitor used to blink going through linux boot, now it doesn't. Other than that there is no improvement, so I still cannot change the driver even with nomodeset. Could the problem be something else?

---

### Post by oldfred on 2015-12-02
Some systems need additional boot parameters. 
If you remove quiet splash and just keep nomodeset, do you see the boot process?
At least one laptop just needs whatever function key that controls screen brightness pressed to make screen visible.

Is this a specific brand/model system on what brand motherboard?

---

### Post by silas3 on 2015-12-02
Removing quite splash does not do anything differently. And according to windows, my system manufacturer is emachines and the system model is et1831. Glad to have windows working at least :)

---

### Post by oldfred on 2015-12-02
In addition to nomodeset in place of quiet splash try each of these:
acpi=off
all_generic_ide
All the way back to 2008 emachines seemed to have issues:
[http://ubuntuforums.org/showthread.php?t=1025842&highlight=emachines+hates+linux](http://ubuntuforums.org/showthread.php?t=1025842&highlight=emachines+hates+linux)

Does live installer work ok?

---

### Post by silas3 on 2015-12-02
Ok, but should I try them all at once, or seperately? Also about live cd, I have some limitations in the sense that my two flash drives won't work for it. One is two small (less than 1 gig) and the other won't run on boot no matter what I try. As we speak, I am downloading the live iso to try to burn to disk, I wanted to try this last because I'll need to download a disk burner, and find some spare disks somewhere in my house (I should have plenty). And as far as I can tell, linux is installed, so would running the live version without installing it be fine? I just don't want to mess anything up anymore :p.

---

### Post by silas3 on 2015-12-02
Ok, I managed to boot from live cd, although it was a bit slow and at the start a saw some keyboard looking icon at the bottom of the screen that I remember hearing was important.  I'll try the splash alternitives now. EDIT: I deleted the part with quiet splash and put in the other things, still no change.

---

### Post by oldfred on 2015-12-02
With BIOS boot you press any key while icons are at bottom of screen and then f6 to get to the boot parameters on the live installer.
You also need nomodeset with your nVidia card. But again not sure what other parameters may be needed.

I would include nomodeset with one of the other parameters.
Some others but now we are just experimenting. But I did not find many emachines and solutions. The link above was one of the few.

       Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by silas3 on 2015-12-03
Ok. Just my luck I tried on an emachine. Also, off topic, When I was installing linux, every single guide said that no matter how you want to partition the disks, you should never use the defaults. Why? What could happen? And don't worry, I did the advanced option and prepartitioned the thing in windows beforehand. And also, is the ftp net installer inferior to the live version in any way, besides the fact you can't check the OS before you install, and minimal (litterly none I suppose) graphics? I have no access to that pc for a day or so, so I figure I'll ask enough questions that I'll know what to do when I can :)

---

### Post by oldfred on 2015-12-03
I have never used the network install, so know nothing about it.

There was a major bug in the installer where re-installing using any of the auto install options erased entire drive. Now fixed. And then it was only save to use Something Else on choose the same partition as / was previously installed into.

With new installs and Windows 8 or later it has fast start up which really is just hibernation. But the Linux NTFS driver will not mount hibernated nor NTFS needing chkdsk to prevent damage. So if Windows 8 the installer may not see the Windows partitions, since it cannot mount it and then just erased it. With Windows 8 or later then fast start up must be off, but still safer to use manual partitioning. 

I always preferred to partition in advance anyway as I so not want some auto install selecting my sizes for me.

---

### Post by Geoffrey_Arndt on 2015-12-04
Silas,

It might be worth your while to check into installing Xubuntu versus Ubuntu.    You would have a much better chance of success, and not need the nomodeset parameters, and might not even need to install the nvidia drivers at all.

Just an option, but you'd still have a distro based on Ubuntu, using the same repositories, and have a functioning dual-boot.   Your choice though, thought I'd just advise of that option.

---

### Post by silas3 on 2015-12-04
Ok I will look into it, it sounds promising! But what will I do with the ubuntu I already have installed? Should I uninstall it, or shrink it's partitions, or what? Anyway thanks for the tip!

---

### Post by Geoffrey_Arndt on 2015-12-04
Just install Xubuntu "over" Ubuntu . . . . in other words, on the same partition.    Just be sure you know what partition that is (what it's labelled).    Do you know how to find that out?    (there is no "uninstalling" an OS . . . . just overwriting it will delete it and replace it).

---

### Post by silas3 on 2015-12-05
THANK YOU installing xubuntu has worked wondefully, it is properly installed and is booting up! Thanks again! P.S I take it ubuntu is not nearly this hard to install on most pcs that are not emachines?

---

