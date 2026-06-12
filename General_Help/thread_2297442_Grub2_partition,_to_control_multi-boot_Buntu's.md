---
title: "Grub2 partition, to control multi-boot *Buntu's"
date: 2015-10-03
forum: General Help
---

### Post by mikodo on 2015-10-03
Hello, everyone.

To multi-boot instances of *Buntu's with Grub2, is this reasonable to follow?


1. Start fresh, with no OS installed, (next install).

 2.  Create a tiny 1 or 2MB unformatted partition with the bios_grub flag with gparted first. (Thanks oldfred).

3.  Install the *Buntu's  root partitions, in pre-formatted partitions of each.  (I use a data partition now, to symlink to).

4.  Run  "sudo update grub"  in *all installs, to keep grub menus updated.

5. Install or remove *Buntu's as I want. 


*Thing is, I don't know if just *one install should upgrade grub menu or, if *all should.


Thank you.

---

### Post by grahammechanical on 2015-10-03
A lot will depend on whether the motherboard has a BIOS or UEFI boot system. I can tell you two things.

1) The last Linux installed will take over the boot menu and it can get very confusing keeping track of which Buntu is controlling the boot menu.
2) Select an installation to be the main installation. And update all the other installations first and the main installation last. If there is a kernel update then each installation will have its Grub configuration rewritten and will take over control of the boot menu. By upgrading the main installation last it will keep the selected main installation in control.

The Software Centre has a set of splash images for the Grub boot menu. I install a diiferent image in each installation and then when the boot menu background image changes I know that my main OS has lost control of the boot menu.

Search for grub2-splashimages. They install in /usr/share/images/grub/. Copy one into /boot/grub/. Run

```
sudo update-grub
```

And when you next restart there will be a background image to the wallpaper. To put a specific installation in control of the boot loader menu load into the particular installation and run

```
sudo grub-install /dev/sda
sudo update-grub
```

That is if you only have one hard disk. This is my method for keeping my favourite OS as the default timeout OS to load.

Regards.

---

### Post by mikodo on 2015-10-03
> **grahammechanical said:**
> -Snip-

1) The last Linux installed will take over the boot menu and it can get very confusing keeping track of which Buntu is controlling the boot menu.
2) Select an installation to be the main installation. And update all the other installations first and the main installation last. If there is a kernel update then each installation will have its Grub configuration rewritten and will take over control of the boot menu. By upgrading the main installation last it will keep the selected main installation in control.
All that you said is *really good information. I am actually making a personal how to file on everything you mentioned, including  my personal details such as, one computer, no UEFI and using GPT with Grub2 with customizations, (there's good Ubuntu Community Wiki's on that)..

On 1 and 2:

 That is similar to how I have done it since, I messed up by deleting the install that controlled the boot menu. In actuality, I was only updating grub in the Main install.

*I will do it as you suggest.

Thank you, Graham.

---

### Post by yancek on 2015-10-03
> The last Linux installed will take over the boot menu and it can get  very confusing keeping track of which Buntu is controlling the boot  menu.

That might be the case with one of the "auto-install" methods such as Install Alongside but I've never installed a Linux system using a Manual/Expert type install, referred to now as "Something Else" in Ubuntu.which did not give me the option of where to install the bootloader.  The default will be the MBR of the first drive but the drive partitions including the / filesystem partition will also be options.  Running update-grub on a system which is not in the MBR will not change that or install any code to the MBR.

---

### Post by oldfred on 2015-10-03
With UEFI, it just installs to sda's ESP - efi system partition, no matter what.
I have installed to sdb several times and full install to flash drive in UEFI mode and every time it overwrites my /EFI/ubuntu folder. It turns out only real change is the tiny grub.cfg in /EFI/ubuntu that is a configfile to call to the full grub.cfg in install.

First time I thought I might not have changed from sda to sdb. But second time, I was sure and even noted that during install it said installing grub to sdb. But it overwrote my main working install's efi partition again. Or oldfred backs up ESP.

---

### Post by mikodo on 2015-10-03
> **yancek said:**
> That might be the case with one of the "auto-install" methods such as Install Alongside but I've never installed a Linux system using a Manual/Expert type install, referred to now as "Something Else" in Ubuntu.which did not give me the option of where to install the bootloader.  The default will be the MBR of the first drive but the drive partitions including the / filesystem partition will also be options.  Running update-grub on a system which is not in the MBR will not change that or install any code to the MBR.

Thank you.

With a small 1 - 2 MB unformatted partition for with the bios_grub flag, do you recommend for subsequent installs to my current Main install, that I tell the installer to not install the bootloader, in effect leaving it with my Main install or, telling it to install in that same small partition, which would be the same as not installing it. Then, just update-grub with the Main install only?

I'm confused now.

Some of my reasons for doing the multi-boots, is to install Ubuntu-next AND to install the next version that will be my Main install, to prepare it so I can delete the old Main install and use the new Main install. What do I do then? Just run update-grub in the new Main install before, I delete the old Main install? That sounds risky for me, as I have stung myself a couple of time with deleting installs. One I could repair with boot-repair, the second time I couldn't. I think to be sure, I am going to do it like Graham suggests.

---

### Post by Dennis N on 2015-10-03
> do you recommend for subsequent installs to my current Main install, that I tell the installer to not install the bootloader, in effect leaving it with my Main install or, telling it to install in that same small partition, which would be the same as not installing it

With Ubuntu's installer, you are forced to install grub's boot loader someplace - either the disk (sda) or on a partition (sda1). (Some installers (different than Ubuntu's) used by other distros allow you to not install the grub bootloader at all, which is handy for multi-booters.) 

So, to NOT have a new OS install take over production of the grub menu, you can install it's grub bootloader to the OS partition.

---

### Post by Dennis N on 2015-10-03
On the last part, before switching from A to B, you would install grub boot loader to the disk (sda, for example) from B, so that thereafter B generates the boot menu, before removing A if you plan to do that. I would just leave the old OS in place until I need to use the partition for something else.

---

### Post by mikodo on 2015-10-04
> **Dennis N said:**
> What you said ...
**So, to NOT have a new OS install take over production of the grub menu, you can install it's grub bootloader to the OS partition.**


> **Dennis N said:**
> On the last part, before switching from A to B, you would install grub boot loader to the disk (sda, for example) from B, so that thereafter B generates the boot menu, before removing A if you plan to do that. I would just leave the old OS in place until I need to use the partition for something else.
Thanks, Dennis.

Alrighty then. I thought this was going to be a quick thread and how-to for me ... lol


1.  Start fresh, with no OS installed, (next install).

2. Create a tiny 1 or 2MB unformatted partition with the bios_grub flag with gparted first. (Thanks oldfred), on the installers' *drive, i.e. /dev/sd**x**.

3. Have the *Main install's installer, install its' grub bootloader to the installs', *drive, i.e. /dev/sd**x**

4. Install subsequent installs' grub bootloaders on their respective *partitions, i.e. /dev/sd**xy** and so on.

5. When it comes time to move to a new *Main install, change it from a subsequent install to *Main install by:

```
sudo grub-install /dev/sd**x**

sudo update-grub
```

6. Delete, old *Main install when, space is needed for another install or EOL.

Notes.

This will allow, only the *Main install producing/generating the grub menu and, I assume with that, no boot problems should arise.

Stick with one drive being used for installs. (Keep it simple stupid).


Thank you, everyone.

---

### Post by oldfred on 2015-10-04
One possible issue. Grub remembers where it was installed originally. And on a major update it will try to reinstall to that location. And then bootloader copy in MBR may not match system as it would only update copy in partition.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates for BIOS
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)
Not even sure this works for UEFI
dpkg-reconfigure grub-efi-amd64

---

### Post by mikodo on 2015-10-04
Thanks Fred.

Yes, I can see that being a possible issue. I ran through the commands, and saw that grub was installed to /dev/sda1 partition. No surprise there. I've done this since the 2 faux pas's with messing up the boot process with different installs. After that, I always installed the grub bootloader to the partition of the distro that was my *Main install was on, including this install, that *only has the one Xubuntu 14.04 installed. I have only done clean/fresh installs that way. I always now do like Graham and  ran sudo update-grub in that *Main install. I learned that from you Fred.

So for learning, I ran through these commands and used the command to change where the bootloader is installed to change it to the /dev/sda drive: "/dev/sda    sudo dpkg-reconfigure grub-pc", and it ran without any errors. I rebooted and by that command again, I saw that it grub is now flagged for /dev/sda. THEN, I thought that I should have run in the install *first "sudo grub-install /dev/sda". BUT, before I did that I had a look in [http://manpages.ubuntu.com/manpages/precise/en/man8/grub-setup.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/grub-setup.8.html), where it states "you should not normally run this program directly. Use grub-install instead. SO, I had done it bass-ackwards. I then ran "sudo grub-install /dev/sda" + "sudo update-grub" and checked again with  "sudo dpkg-reconfigure grub-pc" and it showed still, that I was using the *drive as boot, and ran it again and it showed no errors.

So, what did I learn here.

1. Next *main install, be sure to install the grub bootloader to the *drive and NOT the *partition. All other installs to have the bootloader installed to their respective *partitions.

2. When it comes to changing to the distro that will be my *Main install, run "sudo grub-install /dev/sd**x"** + "sudo update-grub", to change it with the *drive.

3. Run through the above commands and run "sudo dpkg-reconfigure grub-pc", to be sure that it shows that the new *main install is now showing that grub bootloader is installed to the *drive. Correct it there if I have to but, probably I shouldn't have to.

4. Go into *old Main install, and run "sudo grub-install /dev/sd**xy**" + "sudo grub-update", to now install it to the *partition.

5. Check the *old Main install with "sudo dpkg-reconfigure grub-pc" to be sure it has its' install of the bootloader on the *partition. Change it to the partition if I need there too.

6. I am *always going to run "sudo update-grub" *last, in the *main install, as Graham suggests, to be doubly sure, things are remaining the same.

Notes.

I had to hit the "tab" key once or twice in "sudo dpkg-reconfigure grub-pc" windows to highlight OK, to enter.

Start learning about UEFI and having documentation for it, in New Projects. It will be the default with all mobo's eventually by their dropping CSM - UEFI Compatibility Support Module (CSM). See this thread: [http://ubuntuforums.org/showthread.php?t=2296911&p=13365128#post13365128](http://ubuntuforums.org/showthread.php?t=2296911&p=13365128#post13365128)

Done.

 [URL="http://ubuntuforums.org/showthread.php?t=2296911&p=13365128#post13365128"]
[/URL]

---

