---
title: "Recovering Journal...../dev/nvme0n1/p6  clean, n/n files, n/n blocks"
date: 2023-01-24
forum: General Help
---

### Post by gusgf on 2023-01-24
I'm new to Ubuntu in that though I've installed it before I never actually used it. I'm currently doing The Odin Project which mandates the use of Ubuntu. So I've got a dual boot setup with Win10 and have barely used Windows in the last 2 weeks so hoping this will be the momentum needed to go fully over to Linux. There is a lot to learn and at times it's very frustrating. I'm on the latest version of Ubuntu as of 2 weeks ago and decided to try and install Onedrive using the instructions on [makeuseof.com]("https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/") 

I got as far as running the following:
```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt-get autoremove -y
sudo apt-get autoclean -y

```

PLEASE NOTE IMAGES APPEAR CLIPPED BUT YOU NEED TO CLICK ON THEM TO SEE THEM PROPERLY

and then rebooted as was instructed then this happened. I got a black screen after selecting Ubuntu from the grub menu with a message saying [recovering journal]("https://www.amazon.co.uk/photos/share/rksoCwKussRXU3O7R3gQ8qL4Cr62IGEqFNYn4OUhfq8"). 

I've tried to run fsck through the [recovery menu]("https://www.amazon.co.uk/photos/share/dne8CR9zhOLEZpQojf8Z309J6pFF2luv659n2aqFVKo") after rebooting
But keep getting a "Cannot continue message", [see here]("https://www.amazon.co.uk/photos/share/D9ik4j23R1U6cKLUeGYCGE4J5kjasknBCS0aaifP6Zm")
A [message]("https://www.amazon.co.uk/photos/share/LrCETXTt0Xoh1Kcqh5YuLgLoXSV7BG06CYja2d7jIDo") then appears telling me to reboot as the filesystem needs to be in read-only mode, so I end up going around in circles!! Whats the point in telling me to do this if when I do it keeps on telling me the filesystem isn't in read-only mode! I've not mounted it, all I've done is gone into recovery mode.

I'm accessing recovery mode by selecting the following grub menu [option]("https://www.amazon.co.uk/photos/share/qLhiYe44JJGoix7bBleHIX0CheQecx4n2SZ3B28Gfqi") and selecting the [second line]("https://www.amazon.co.uk/photos/share/OnSs7nlZl8Ki9jXnkm7wWEUAccbieAavecXxDXyKGwB")

[This]("https://www.amazon.co.uk/photos/share/5VR158tWDjuTYg8xSoTFuP6VTmmq1D3dvOdgf22YCMH") is what I'm seeing when I run gparted

When I boot off of a USB Ubuntu stick and run fsck via a console I get this [output]("https://www.amazon.co.uk/photos/share/B7IDkRWiOTdWDYEwDDpglFTZxCycIVugYZw52ESKCKs")


I really want to know what I've done wrong and learn from this. Can someone please help

---

### Post by TheFu on 2023-01-25
> **gusgf said:**
> I'm new to Ubuntu in that though I've installed it before I never actually used it. I'm currently doing The Odin Project which mandates the use of Ubuntu. So I've got a dual boot setup with Win10 and have barely used Windows in the last 2 weeks so hoping this will be the momentum needed to go fully over to Linux. There is a lot to learn and at times it's very frustrating. I'm on the latest version of Ubuntu as of 2 weeks ago and decided to try and install Onedrive using the instructions on [makeuseof.com]("https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/") 

It took you years to learn that other OS.  It will take years to learn Linux, especially since things that appear similar on the surface really aren't. You'll need to unlearn some things.  Beware.  the MSFT way isn't the only or every the correct way.

> **gusgf said:**
> I got as far as running the following:
```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
sudo apt-get autoremove -y
sudo apt-get autoclean -y

```

PLEASE NOTE IMAGES APPEAR CLIPPED BUT YOU NEED TO CLICK ON THEM TO SEE THEM PROPERLY

Those shouldn't be too harmful.  For weekly maintenance, I wrote an article: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) that lifehacker.com republished years ago. Maybe it will be helpful.

I don't click on external image links. Security. Sorry.

> **gusgf said:**
> and then rebooted as was instructed then this happened. I got a black screen after selecting Ubuntu from the grub menu with a message saying [recovering journal]("https://www.amazon.co.uk/photos/share/rksoCwKussRXU3O7R3gQ8qL4Cr62IGEqFNYn4OUhfq8"). 

So, most modern file systems are journaled. This is a good thing.  If it successfully did recover the journal, then all is fine.  Don't just unplug the computer anymore. Always cleanly shutdown any Unix computer. This can take 10 seconds or 5 minutes to happen. Depends on all sorts of things.  There can be bugs in the shutdown process too, though I haven't seen any personally in about 10 yrs.


> **gusgf said:**
> I've tried to run fsck through the [recovery menu]("https://www.amazon.co.uk/photos/share/dne8CR9zhOLEZpQojf8Z309J6pFF2luv659n2aqFVKo") after rebooting
But keep getting a "Cannot continue message", [see here]("https://www.amazon.co.uk/photos/share/D9ik4j23R1U6cKLUeGYCGE4J5kjasknBCS0aaifP6Zm")
A [message]("https://www.amazon.co.uk/photos/share/LrCETXTt0Xoh1Kcqh5YuLgLoXSV7BG06CYja2d7jIDo") then appears telling me to reboot as the filesystem needs to be in read-only mode, so I end up going around in circles!! Whats the point in telling me to do this if when I do it keeps on telling me the filesystem isn't in read-only mode! I've not mounted it, all I've done is gone into recovery mode.


So, fsck is the correct tool to use, but it cannot be run on active/mounted file systems.  That's sorta a problem.  Before systemd took over in 2016, we had a trivial way to get fsck run at reboot, before any file systems got mounted, but the systemd team decided to make it complex and removed that clear, easy, clean, method.  We are stuck with 2 methods to run fsck on the file systems that are part of the OS.  

a) Boot from the install media into the "Try Ubuntu" environment, then look up the device names (they can change at every boot), and run sudo fsck /dev/sdXY ... this needs to be run on the file system, not the whole disk.  the device name can be nvme-something or sd-something and depending on all sorts of things, it might not directly relate to a partition.  This is the easier method.

b) Edit the grub boot parameters to run fsck on the specific device.  In /etc/defaults/grub, there's a line with "GRUB_CMDLINE_LINUX_DEFAULT=" in it.  Edit that line so it includes: "fsck.mode=force fsck.repair=yes", then run 'sudo update-grub' and reboot.  That will force fcsk to be run at boot always.  Most of the time, it is better to force an fsck to run monthly.  That can be setup in the file system parameters, but that's kinda advanced for someone new to Linux.

Whenever editing system files, use the 'sudoedit' command.  If you see any how-to guides saying 'sudo gedit /etc/xyz', then those people are don't know better and are trying to break your system.  You can use any editor you like, including gedit with sudoedit.  I think by default it used nano (yuck!).
  
> **gusgf said:**
> 
I'm accessing recovery mode by selecting the following grub menu [option]("https://www.amazon.co.uk/photos/share/qLhiYe44JJGoix7bBleHIX0CheQecx4n2SZ3B28Gfqi") and selecting the [second line]("https://www.amazon.co.uk/photos/share/OnSs7nlZl8Ki9jXnkm7wWEUAccbieAavecXxDXyKGwB")

[This]("https://www.amazon.co.uk/photos/share/5VR158tWDjuTYg8xSoTFuP6VTmmq1D3dvOdgf22YCMH") is what I'm seeing when I run gparted

When I boot off of a USB Ubuntu stick and run fsck via a console I get this [output]("https://www.amazon.co.uk/photos/share/B7IDkRWiOTdWDYEwDDpglFTZxCycIVugYZw52ESKCKs")


I really want to know what I've done wrong and learn from this. Can someone please help

So, in linux forums, we prefer text output. This allows people trying to help you to copy/paste sections to highlight specific things.  Also, text is what we're used to, not the GUI stuff.  There are a few exceptions and gparted is one.  That tool is very helpful.  These forums support image uploads and attaching them to a message.  It is more complex than it should be, but they will run the image through software to remove any badness it may have - so it is just the image, nothing else.  Security stuff.

Whenever having issues with commands, post the full, exact command and the full, exact output (usually less than 10 lines).  No images please.  Also, some commands and output need to be placed into forum code tags, so everything lines up. The advanced editor here has a '#' button which is used just like the quote or bold or italic tags.  Please use it.

A handy command for disk stuff is:
```
lsblk -e 7 -o name,size,type,fstype,uuid,label,mountpoint
```
That's what a code blog/code-tag looks like.
I have that as an alias, so I don't have to type it all the time.

A good beginning Linux book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Free, no-hassle, download.

---

### Post by gusgf on 2023-01-25
> **TheFu said:**
> For weekly maintenance, I wrote an article: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) that lifehacker.com republished years ago. Maybe it will be helpful.

I've taken a quick look at this and will certainly revisit it later, it looks like there is some valuable nuggets of wisdom to be had :)

> **TheFu said:**
> I don't click on external image links. Security. Sorry.

I thought this might be an issue but I couldn't see another way at the time. On boot I selected 'Advanced options for Ubuntu' from the grub menu and from the recovery menu I selected 'fsck' and so I've attached a screenshot of the output in the command line. 

 

> **TheFu said:**
> So, fsck is the correct tool to use, but it cannot be run on active/mounted file systems.  That's sorta a problem.  Before systemd took over in 2016, we had a trivial way to get fsck run at reboot, before any file systems got mounted, but the systemd team decided to make it complex and removed that clear, easy, clean, method.  We are stuck with 2 methods to run fsck on the file systems that are part of the OS.

a) Boot from the install media into the "Try Ubuntu" environment, then look up the device names (they can change at every boot), and run sudo fsck /dev/sdXY ... this needs to be run on the file system, not the whole disk.  the device name can be nvme-something or sd-something and depending on all sorts of things, it might not directly relate to a partition.  This is the easier method.

I already tried booting off of a live USB and from the command prompt ran 
```
ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p6
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/nvme0n1p6: clean, 267966/1466368 files, 3457320/5859328 blocks

```
but it didn't do anything useful as the problem persists

> **TheFu said:**
> A handy command for disk stuff is:
```
lsblk -e 7 -o name,size,type,fstype,uuid,label,mountpoint
```
I will run this and post the output here.
```
ubuntu@ubuntu:~$ lsblk -e 7 -o name,size,type,fstype,uuid,label,mountpoint
NAME          SIZE TYPE FSTYPE  UUID                                 LABEL                    MOUNTPOINT
sda          58.6G disk iso9660 2022-08-10-16-21-45-00               Ubuntu 22.04.1 LTS amd64 
&#9500;&#9472;sda1        3.6G part iso9660 2022-08-10-16-21-45-00               Ubuntu 22.04.1 LTS amd64 /cdrom
&#9500;&#9472;sda2        4.1M part vfat    8D6C-A9F8                            ESP                      
&#9500;&#9472;sda3        300K part                                                                       
&#9492;&#9472;sda4         55G part                                                                       
sr0          1024M rom                                                                        
nvme0n1     476.9G disk                                                                       
&#9500;&#9472;nvme0n1p1   100M part vfat    DCB4-17A8                                                     
&#9500;&#9472;nvme0n1p2    16M part                                                                       
&#9500;&#9472;nvme0n1p3 145.8G part ntfs    2EA6BE5EA6BE266D                                              
&#9500;&#9472;nvme0n1p4   537M part ntfs    B06C69FD6C69BEAA                                              
&#9500;&#9472;nvme0n1p5  14.9G part swap    3db28b87-5967-4695-a782-bf2c37deb0fa                          
&#9500;&#9472;nvme0n1p6  22.4G part ext4    ea9636db-e641-4b93-94db-47409da6c117                          
&#9492;&#9472;nvme0n1p7  93.1G part ext4    6940fc7a-76ba-4daf-bffa-bcc624eb0899 
```

I should point out I hadn't realised SDA was still attached as I'd had a previous failed attempt at installing Ubuntu having relied upon the automatic install as opposed to managing the partitions myself. I'm pretty sure my current Ubuntu install is the one that is totally on the NVME. I'm going to disconnect it for now. 


> **TheFu said:**
> A good beginning Linux book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) Free, no-hassle, download.
I actually have this somewhere!

---

### Post by TheFu on 2023-01-25
So, that 1 image says it tried to run fsck, then failed because it was mounted and didn't do anything.  You need to boot into the "Try Ubuntu" environment off an install flash drive.  BTW, keep this setup, since boot issues, seldom as they are, are easiest to fix from booting a "Try Ubuntu" environment.

As an example for what/how to run fsck, here's one of my systems:
```
$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint
NAME                                  SIZE TYPE FSTYPE      LABEL      MOUNTPOINT
nvme0n1                             465.8G disk                        
&#9500;&#9472;nvme0n1p1                            50M part vfat        EFI        /boot/efi
**&#9500;&#9472;nvme0n1p2                           600M part ext4                   /boot**
&#9492;&#9472;nvme0n1p3                           465G part LVM2_member            
  &#9500;&#9472;vg00-swap                         4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                      35G lvm  ext4                   /
  &#9500;&#9472;vg00-var                           35G lvm  ext4                   /var
  &#9500;&#9472;vg00-home                          26G lvm  ext4        home       /home

```
I'm using LVM, so all the stuff on p3 is under LVM control.  We'll ignore it for now.

I can't run fsck on vfat (fat32). It is a foreign file system. exFAT and NTFS would be the same. Don't use Linux tools to fix non-Linux issues, unless that is your last possible resort.

So, that leaves /boot/ which has an ext4 file system directly on the p2 partition.  It is mounted, so I can't run the fsck on it.  I'd need to boot off a Try Ubuntu/ISO flash drive. I have an Ubuntu-Mate ISO on an 8G USB2 flash drive just for emergency use.  So after I boot it, then choose "Try Ubuntu-Mate", a normal Mate desktop is shown.  I open a terminal and run that lsblk command, see the information, just without the MOUNTPOINT column data - they aren't mounted - and I'd run:
```
$ sudo fsck -y /dev/nvme0n1p2
```
That's the device with the ext4 file system.  LVM uses different device files and I don't want to confuse you, unless you actually are using LVM.  The output from the requested lsblk command would tell me exactly what we need to know and I could provide the different fsck commands for each file system (within certain known file systems).  ZFS and btrfs don't use fsck. They have their own tools, so if you elected to install them, I can't help.  I'm an LVM+ext4 guy.

---

### Post by gusgf on 2023-01-25
Okay so you can see sda is my USB stick and my main storage with dual booting Win10 (boots and works fine) and Ubuntu is the NVME.

```
ubuntu@ubuntu:~$ lsblk -e 7 -o name,size,type,fstype,label,mountpoint
NAME          SIZE TYPE FSTYPE  LABEL                    MOUNTPOINT
sda          58.6G disk iso9660 Ubuntu 22.04.1 LTS amd64 
&#9500;&#9472;sda1        3.6G part iso9660 Ubuntu 22.04.1 LTS amd64 /cdrom
&#9500;&#9472;sda2        4.1M part vfat    ESP                      
&#9500;&#9472;sda3        300K part                                  
&#9492;&#9472;sda4         55G part                                  
sr0          1024M rom                                   
nvme0n1     476.9G disk                                  
&#9500;&#9472;nvme0n1p1   100M part vfat                             
&#9500;&#9472;nvme0n1p2    16M part                                  
&#9500;&#9472;nvme0n1p3 145.8G part ntfs                             
&#9500;&#9472;nvme0n1p4   537M part ntfs                             
&#9500;&#9472;nvme0n1p5  14.9G part swap                             
&#9500;&#9472;nvme0n1p6  22.4G part ext4                             
&#9492;&#9472;nvme0n1p7  93.1G part ext4
```

```
ubuntu@ubuntu:~$ sudo fsck -y /dev/nvme0n1p6
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/nvme0n1p6: clean, 267954/1466368 files, 3461877/5859328 blocks
```

```
ubuntu@ubuntu:~$ sudo fsck -y /dev/nvme0n1p7
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/nvme0n1p7: clean, 102869/6111232 files, 6333716/24413952 blocks
```


Root is p6 and home is p7.

Any idea what might the problem be?

---

### Post by TheFu on 2023-01-25
Well, the fsck for p6/p7 worked. No issues.  So, that isn't the issue.

Let me look over the OP. .....

Ok, so you have a black screen after booting.  I don't know anything about that, but it is probably GPU driver related.  There's a black screen troubleshooting guide - google should find it.  "black screen boot ubuntu" is the search I'd use.
This was found for 20.04: [https://ubuntuforums.org/showthread.php?t=2442390](https://ubuntuforums.org/showthread.php?t=2442390)
[https://linuxconfig.org/ubuntu-black-screen-solution](https://linuxconfig.org/ubuntu-black-screen-solution) is another with detailed steps that get you into recovery mode and select safe graphics, whatever that means.  Worth a try.

BTW, I think the recovery mode has a way to run fsck on all connected file systems too.  I'd forgot about that. Sorry.  For a number of reasons I won't get into (KVM switch, video output converter), I never see the grub screen on my systems - takes too long for the GPU to be selected and the default OS is already booting, so I miss the ability to catch the boot at the right point.

---

### Post by gusgf on 2023-01-25
Well no, I get a screen with this output when I boot:

```
/dev/nvme0n1p6: recovering journal
/dev/nvme0n1p6: clean, n/n files, n/n blocks
[     4.986040]
```

---

### Post by TheFu on 2023-01-25
Well, that just says that fsck worked and there weren't any issues fixed.  Ignore it.  Move to the next issue.

---

### Post by gusgf on 2023-01-25
I'm trying to but it's a bit difficult when I can't even boot Ubuntu!!

---

### Post by TheFu on 2023-01-25
> **gusgf said:**
> I'm trying to but it's a bit difficult when I can't even boot Ubuntu!!

When you can't boot, use the installation flash drive, boot into "Try Ubuntu" to fix things.  Keep that in your mind when you can't get passed grub/booting.  Call this general knowledge.

One more "general knowledge" thing.  Whenever you see 'sudo gedit' or 'sudo nano' or sudo joe-bobs-editor, replace that with 'sudoedit'.  It is specifically designed to be safer.

If you are using UEFI, use the efibootmanager to pick which OS to boot.  [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)  I don't use EFI much (and don't reboot more than about once a month, so I don't have direct knowledge to share on this. Sorry. LinuxBabe usually has clear guides, but I haven't used this one.  I do know that she will modify a guide if someone points out issues or a better way, which means they are always improving. That's nice.  In theory, any EFI booting BIOS should have a built-in way to choose which OS to be booted.  

[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132) is a guide for setting kernel boot parameters both forever and for just 1 boot.  Usually, I do the 1 boot method, see it work, then add it permanently as I work for a better solution.  These things should be workarounds only.  Sometimes GPUs, especially nvidia ones, need a little extra help.

If you are using legacy boot, i.e. grub (probably grub2 by now), try reinstalling it and perhaps running grub-update.  There are guides. It isn't as easy as just running those programs. Some setup using chroot and bind mounts are necessary. The guides should have that spelled out.  
[https://askubuntu.com/questions/493612/how-to-reinstall-grub](https://askubuntu.com/questions/493612/how-to-reinstall-grub) is one method.  It mentions using boot-repair.  Boot-repair isn't a bad tool, but there are just so many options these days that it is always behind except for the most simple solutions.  BUT ... boot-repair does have a nice tool that will create a boot-info file/URL so others much smarter than me can review and help.  I'd probably start a new thread with a title like "New 20.04 Install won't boot"  Then post the URL that boot-repair creates in that thread for some new eyes to check out.  

The fsck is solved, unless the storage is dying or someone is yanking the power plug rather than doing a shutdown.

---

### Post by tea for one on 2023-01-26
As your two Ubuntu partitions (nvme0n1p6 and nvme0n1p7) are being reported as clean, I wonder if your ESP (nvme0n1p1) is clean?
Corruption on the ESP can cause boot problems.

Does Windows 10 boot OK?

By the way, OneDrive is built for Windows OS and any workaround for Ubuntu (especially if not present in the official repositories) should be treated cautiously.
The instructions via [https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/](https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/) involve the use of an opensuse repo - not really for new users.

---

### Post by gusgf on 2023-01-26
> **TheFu said:**
> When you can't boot, use the installation flash drive, boot into "Try Ubuntu" to fix things.  Keep that in your mind when you can't get passed grub/booting.  Call this general knowledge.
Well I've been doing this since before I put out a call for help on this forum.

> **TheFu said:**
> If you are using UEFI, use the efibootmanager to pick which OS to boot.  [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples) 
Currently using Grub

> **TheFu said:**
>  If you are using legacy boot, i.e. grub (probably grub2 by now), try reinstalling it and perhaps running grub-update.  There are guides. It isn't as easy as just running those programs. Some setup using chroot and bind mounts are necessary. The guides should have that spelled out.  [https://askubuntu.com/questions/493612/how-to-reinstall-grub](https://askubuntu.com/questions/493612/how-to-reinstall-grub) is one method.  It mentions using boot-repair.  Boot-repair isn't a bad tool, but there are just so many options these days that it is always behind except for the most simple solutions.  BUT ... boot-repair does have a nice tool that will create a boot-info file/URL so others much smarter than me can review and help.  I'd probably start a new thread with a title like "New 20.04 Install won't boot"  Then post the URL that boot-repair creates in that thread for some new eyes to check out.  
Well the Grub menu is coming up and I can successfully boot Windows from this but Ubuntu only gets so far.

> **TheFu said:**
> The fsck is solved, unless the storage is dying or someone is yanking the power plug rather than doing a shutdown.
Well no, I've run fsck on all the partitions and no errors are or were ever reported so if the issue is Grub then that's a different problem. When this failure to boot into Ubuntu happened I tried to resolve it myself by following what [this]("https://dev.to/hasone/error-on-ubuntu-boot-up-recovering-journal-2j49") suggested and again no errors came to light which is why I posted here. So fsck is not solved as it seems it was possibly never the issue!

---

### Post by TheFu on 2023-01-26
Be very careful following random guides on the internet.  You don't know the quality/experience of the author.  For ubuntu issues, stick with web domains that have "ubuntu" in the name ... that's the .com part, not the full URL, until you build up a list of other known, trustworthy, instruction websites.  Sometimes the article was written by someone that doesn't really know what's happening and thinks what they did actually fixed it when it was coincidence.  OTOH, you can't tell that I'm any better at this point either.

I'm not confident in my boot knowledge to provide any more advice. Last night I suggested posting a new thread with the boot-repair generated report URL. You'll get eyes of people who are expert at booting issues that way. I suggested a thread title too.  Good luck!

---

### Post by tea for one on 2023-01-26
Here is the link for the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

May be advisable to start a new thread with a different subject line and include a link to this thread.
Something like:- Grub loads but Ubuntu doesn't boot?

---

### Post by gusgf on 2023-01-26
> **tea for one said:**
> As your two Ubuntu partitions (nvme0n1p6 and nvme0n1p7) are being reported as clean, I wonder if your ESP (nvme0n1p1) is clean?
Corruption on the ESP can cause boot problems.

Does Windows 10 boot OK?

By the way, OneDrive is built for Windows OS and any workaround for Ubuntu (especially if not present in the official repositories) should be treated cautiously.
The instructions via [https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/](https://www.makeuseof.com/how-to-install-microsoft-onedrive-on-ubuntu/) involve the use of an opensuse repo - not really for new users.


Windows boots perfectly.

If there is a problem with the ESP I'm wondering why I don't get an error like *'Efi System Partition (ESP) not usable'* 

Why on every attempt at booting do I see the message about recovering journal when no problem are reported when I check the partition with fsck and furthermore it states P6 is clean?

---

### Post by gusgf on 2023-01-26
Yikes you guys are out-posting me  :)

You've both suggested starting a new thread and that makes sense. I will do this.

---

### Post by gusgf on 2023-01-26
Hey 'TheFu' and 'Tea for One' thanks for trying to help :)

---

### Post by gusgf on 2023-01-26
Okay I posted to pastebin and my new thread is [here]("https://ubuntuforums.org/showthread.php?t=2483319&p=14128016#post14128016")

---

