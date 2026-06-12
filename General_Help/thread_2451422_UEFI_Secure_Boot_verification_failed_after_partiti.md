---
title: "UEFI Secure Boot verification failed after partition restore"
date: 2020-10-04
forum: General Help
---

### Post by jg1 on 2020-10-04
I have a Dell XPS13 with 2 Xubuntu partitions, a live system and a reserve system in case I screw up the live one. Recently upgraded both from 18.04 (Bionic) to 20.04 (Focal) using the standard LTS upgrader.  The new systems ran OK except for several issues which arise from what appear to be bugs/shortcomings in the new release.  The show stopper was the apparent confusion between Power Manager and Screensaver.  This had the effect of occasionally freezing the keyboard and screen and the LightDM lock screen appears several seconds after the lid is lifted from Suspend. So decided to revert to 18.04.

Used "dd" to restore the reserve partition from a previously running reserve partition image
[INDENT]jg@jg-XPS13:~$ sudo dd if=/media/jg/Wdrive/nvme0n1p5.img of=/dev/nvme0n1p5 status=progress
[sudo] password for jg: 
12506001920 bytes (13 GB, 12 GiB) copied, 109 s, 115 MB/s
24576000+0 records in
24576000+0 records out
12582912000 bytes (13 GB, 12 GiB) copied, 112.465 s, 112 MB/s
jg@jg-XPS13:~$ [/INDENT]
and then reinstalled grub in the restored partition.
[INDENT]sudo mount /dev/nvme0n1p5 /mnt
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/nvme0n1
update-grub[/INDENT]
[Ctl]+[d]		to return root to Live partition
[INDENT]sudo reboot[/INDENT]

So far so good.

When I now try to boot, I am prevented from so doing by what I assume is the Secure Boot function.  When I did the upgrade I had to enter a password on first boot which I assume provided a key for the bootloader.  I have read this post

[https://www.dell.com/community/XPS/XPS-13-9370-boot-with-USB-or-SD-card-AND-secure-boot/m-p/7425584?](https://www.dell.com/community/XPS/XPS-13-9370-boot-with-USB-or-SD-card-AND-secure-boot/m-p/7425584?)...

which relates to Windows but I'm not much the wiser.  I believe there's a way out using a program called "shim" which loads a Microsoft compatible key but I have so far been unable to find any helpful information.  I don't want to have to revert to legacy boot mode.  Can anybody help and/or point me to a way to overcome this issue, pls?

Tks in anticipation

jg

---

### Post by CelticWarrior on 2020-10-04
The option is not to revert to legacy, never.
The alternative meanwhile is to simply disable Secure Boot. Then later you may try reinstalling Grub and re-enabling Secure Boot although I can't understand why you would want that.

---

### Post by oldfred on 2020-10-04
With UEFI & gpt partitions dd is not the tool to use.
With gpt you have partition GUID that is also in primary partition table & backup partition table. If the GUIDs get out of sync you have issues. And dd does an image copy & if not restored to same partition with same GUID then an issue.

Usually easier to do new install & restore /home, list of installed apps and maybe some settings from /etc, if you changed any system settings (I edit some grub files, but copy those into /home for backup). 

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

To see if gpt structure is ok.
sudo gdisk -l /dev/nvme0n1
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by jg1 on 2020-10-04
Tks Oldfred  I was coming to the same conclusion.  Looking at the Wiki ([https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)) there is plenty of advice on installing foreign drivers and homespun kernels but nothing about getting restored partitions to work again!  It's just that a fresh install takes forever and I was hoping that my backups would come in handy.  Tant pis!
I could simply disable Secure Boot (which is what I meant when I said lagacy boot) but I was hoping there might be a simple way of renewing or retrieving the certificates that had been used at the time I did the backups.  I did backups of the efi partition and the Dell utilities partition at the same time and could restore these or particular files from them if needed.
Any ideas would be much appreciated otherwise it's a case of a fresh install.
I'll not mark the thread solved just yet in case someone comes up with a modus operandi for using partition backups.
Meanwhile, down to work  ...
Cheers !
jg

---

### Post by CelticWarrior on 2020-10-04
> [COLOR=#000000]which is what I meant when I said lagacy boot[/COLOR]

Please use correct terminology.
UEFI mode with or without Secure Boot is still UEFI mode.
Legacy, CSM or "BIOS" mode is the same, an emulation of the old BIOS mode.

---

### Post by jg1 on 2020-10-04
BTW
gpt is not on the 20.04 installation media that I have and SecureBoot won't let me boot systemrescuecd as recommended by Rod Smith
jg

---

### Post by CelticWarrior on 2020-10-04
GPT is a partitioning type/mode. It's not a "thing" in itself. Installation media usually isn't and doesn't need to be GPT.

---

### Post by oldfred on 2020-10-04
Normally UEFI Secure Boot also prevents boot of USB flash drives. That is also not Secure. Not sure how you are then supposed to repair a fully Secure System when it breaks.

There usually is another setting in UEFI, that is allow USB boot or full USB support.

Partitioning of USB flash drive should not matter. But I started conversion to gpt in 2010, including larger flash drives. 

Not sure why you think new install is so slow.
I just installed 20.10 in about 12 minutes to HDD. My installs to SSD from RAM are about 10 minutes. But full install to USB3 flash drive is over 40 minutes & adding software very slow.

Since I like to install every new version, often more than once, but keep latest LTS as main working install.
I have all data in separate data partition and run a script to create mount & mount data partition and create links to data folders. Another script to install my more popular apps. Only if LTS install will I install everything I have in exported list of all installed apps.  Often do not restore /home as I may want to experiment with settings, but have just copied /home to new install. It usually is less than 1GB (when no data).

Or typically I can have a new install fully working in about an hour.

---

### Post by jg1 on 2020-10-04
Hi, OldFred
Tks for your note.  Any support is good when one's battling against the odds.
A bit of background ...
I've been using Ubuntu and then Xubuntu when Ubuntu started getting fat for about 15 years now (Gutsy was my first fully commited install) yet I still feel like a newbie.
It seems that the Dell EFI boot allows Secure Boot or simply UEFI.  That's no Pb but as a senior I try to keep pace with the march of technology so would try to move to secure boot as this offers some protection against unauthorised Load&Go invaders.
A fresh install takes me the best part of a day.  The initial install takes 15-20 mins but then I need to remove 50-60 pgms and install 50-60 more.  Then I need to set up panels and launchers and while much of it can be copied from another PC there are differences between desktop and laptop settings. And finally I need to set up the encryption algorithms to access the data repositories and back the whole thing up.  I then test this before cloning to the live partition, changing the UUID and reinstalling grub to make the whole thing automatic.  It's not bad doing something I've done before, provided I documented the terminal comands at the time but if I have to reinvent from scratch ... you get the picture.
I stick to LTS releases but I have some very capable hardware stuck at 16.04 because of IDE/SATA issues.  I try to look at new releases as they appear and did a trial install of 20.04 Beta back in March and thought it looked OK and so waited for the upgrader issues to be fixed before doing it for real.  I tried it in a VM first but that failed (I assume because of the VirtualBox kernel mods) so went for one of my laptops - the XPS13.  Everything looked OK until I started using it for real when all sorts of worms started appearing from the woodwork - mainly around suspend and power manager.  There were also issues like the lack of pkexec in the new distro.  Hence the wish to revert to 18.04 as that's the system installed on most of the other PCs on my network.
I know how to redo the install and I have all the config files on the dd image I took before the upgrade but I just thought it might be easier to restore the partition and reinstall grub.  How wrong can one be !!
After this learning experience I will certainly look at other ways of safeguarding/ backing up earlier installations so they can be readily recreated in the hour of need.  Still, it's late here on this side of the pond and I'll pick this up in the morning.
Tks again for your advice and support.  Both much appreciated
vbw
jg

---

### Post by oldfred on 2020-10-04
I used to manually configure system.

But because I was doing so many installs and redoing the same thing over and over, I finally said isn't  the computer that is supposed to do the automation?

So I started to look for terminal commands to do changes I was doing with gui. And found some easily and over time more & more. Still only about 80 to 90% in scripts, but lot easier that using gui every time. 

Then in my Zim file I use to document the suggestions I post, I added a another file "NewInstall", just to document all the manual steps I still do and some of the commands I use to check configuration.

---

### Post by jg1 on 2020-10-05
I agree.  I do a lot more through the CLI than I used to.  I've a library of commands that I regularly use but I haven't really got into scripting.  I shudder to think how I used to pull IBM mainframe operating systems apart 50 years ago -  and then all the commands had to go in via punched cards.  Still, the mods will say we're off topic so I'll draw stumps at that and mark the thread as solved in that I now know the answer rather than problem fixed.
Many tks for the help and advice.
vbw
jg

---

