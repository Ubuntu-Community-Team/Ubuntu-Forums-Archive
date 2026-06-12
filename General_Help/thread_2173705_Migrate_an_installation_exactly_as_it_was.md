---
title: "Migrate an installation exactly as it was"
date: 2013-09-10
forum: General Help
---

### Post by josephellengar2 on 2013-09-10
I have a ~3 yr old computer with 12.04 installed and am getting a new one next week, which I plan to also install 12.04 on (64 bit). They are similar computers (laptops, both have Nvidia graphics, both HP brand so presumably similar chipsets, both i7 processors, etc) but not identical.

What is the best way to migrate my current installation to the new computer identically, without messing up the hardware/drivers? For example, I want to take advantage of the SSD alignment and other optimization in 12.04 and have the correct drivers for my new setup (eg, my new computer will have a touchscreen) but I don't want to have to spend 8 hours tweaking the new computer.

I have everything modified, from the backdrop on the bootloader and the login screen to the sources, fstab, hosts file, etc. I also spend a very large amount of time making Gnome 3 feel like Gnome 2.

Is there any way to at least keep a good portion of this when I migrate?

Thanks!

---

### Post by oldfred on 2013-09-11
New system will be UEFI, where old system was BIOS. And partitioning has changed from MBR to gpt. So you cannot easily do any image type copies.
But most of your configuration is in /home and you should just be able to do a new install and copy everything in /home to new system. I would manually partition in advance, copy /home data into new /home partition and then install including the mount but not reformat of /home. Then most of your configuration will be saved.
Some of the new systems have such new hardware that the 13.04 or even the beta of 13.10 works better as kernel & drivers are updated to work with the very new hardware. We do not suggest 13.10 unless you are will to suffer crashes and are willing to report bugs.

UEFI is a lot more complex most since Windows implemented secure boot. See links in my signature but it is a lot of change to use UEFI.

---

### Post by sudodus on 2013-09-11
Welcome to the Ubuntu Forums :-)

I want to add two questions before going deeply into the complicated problems:

- Do you intend to dual boot with Windows 8 or install only Ubuntu (or some other flavour in the Ubuntu family)?

- If only Ubuntu, can you check if it is possible to switch off UEFI (somewhere in the BIOS menu system)?

Because if only Ubuntu (flavour) and possible to switch off UEFI, you can probably port your present system to the new computer. The new computer might run better with 13.04 or 13.10 depending on the hardware, but it would be worth trying with your present 12.04 LTS :-)

---

### Post by josephellengar2 on 2013-09-11
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

I want to add two questions before going deeply into the complicated problems:

- Do you intend to dual boot with Windows 8 or install only Ubuntu (or some other flavour in the Ubuntu family)?

- If only Ubuntu, can you check if it is possible to switch off UEFI (somewhere in the BIOS menu system)?

Because if only Ubuntu (flavour) and possible to switch off UEFI, you can probably port your present system to the new computer. The new computer might run better with 13.04 or 13.10 depending on the hardware, but it would be worth trying with your present 12.04 LTS :-)

Thank you. Actually I'm not new, but the forums seem to have reset my beans and changed my name when I merged with the open ID login.

I intend to single boot Ubuntu (no flavor).

I am able to turn off UEFI on the new laptop. Specs (listed below) are all almost identical to my old computer, except newer stuff. The only real difference is that this one has a touchscreen but I don't care about that anyway.

·  4th generation Intel(R) Core(TM) i7-4900MQ Processor
·  NVIDIA GeForce GT 740M Graphics with 2048MB of dedicated video memory
·  17.3-inch diagonal HD+ BrightView LED-backlit Display (1600 x 900)
·  12GB DDR3 System Memory (2 Dimm)
·  1.5TB 5400 rpm Dual Hard Drive
·  Blu-ray player & SuperMulti DVD burner
·  Backlit Keyboard
·  Webcam and Microphone
·  802.11b/g/n WLAN and Bluetooth(R)***Replacement Product Order Confirmation CPL # 7502804015

---

### Post by oldfred on 2013-09-11
Some of the very new systems seem to work better with the very new not released 13.10. But it is about at beta so may have issues and if you have issues you need to report as bugs.

You can install in either UEFI or BIOS mode, but I would suggest using gpt. Windows only boots from gpt partitioned drives with UEFI, but Ubuntu will boot from gpt with either UEFI or BIOS. If you format with MBR(msdos) you cannot boot in UEFI mode and could not reinstall Windows.

Even if not planning on using Windows you may want to make a full image copy to restore system. If later you decide to sell, it may need Windows.

Even if you decide to use BIOS to boot, I would still create an efi partition at beginning of drive. It would be difficult to add an efi after partition has lots of data on it. 

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by josephellengar2 on 2013-09-11
> **oldfred said:**
> Some of the very new systems seem to work better with the very new not released 13.10. But it is about at beta so may have issues and if you have issues you need to report as bugs.

You can install in either UEFI or BIOS mode, but I would suggest using gpt. Windows only boots from gpt partitioned drives with UEFI, but Ubuntu will boot from gpt with either UEFI or BIOS. If you format with MBR(msdos) you cannot boot in UEFI mode and could not reinstall Windows.

Even if not planning on using Windows you may want to make a full image copy to restore system. If later you decide to sell, it may need Windows.

[...]

One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Thank you for this extended explanation. What I am doing though, is the laptop comes with a hard drive with Windows 8 preinstalled. I am going to swap out that hard drive for my own SSD, so I don't have to worry about leaving the UEFI partition. I was planning on doing 4gb swap, 50 gb /, and the rest home. If I ever sell the computer I can do it with the old hard drive.

But I didn't understand this part of your post:

> 
You can install in either UEFI or BIOS mode, but I would suggest using  gpt. Windows only boots from gpt partitioned drives with UEFI, but  Ubuntu will boot from gpt with either UEFI or BIOS. If you format with  MBR(msdos) you cannot boot in UEFI mode and could not reinstall Windows.


Are UEFI/BIOS more than just interfaces with the bootloader? Typically what I do when I install is I just put in the live media, partition, and install. I don't even use the alternative media. Do I need to do something special to install on a UEFI computer? Or use a different tool to partition my drive?

---

### Post by oldfred on 2013-09-11
gpt is partitioning that has replaced MBR(msdos). I have used gpt on my old BIOS system since 10.10. And all new drives I partition with gpt with both efi & bios_grub partitions, so I can move drives to a new UEFI system later. 

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

 GPT fdisk Tutorial -srs5694 in forums - gdisk is in repository
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

UEFI uses gpt, BIOS uses MBR(msdos). But Ubuntu will boot with either UEFI or BIOS from a gpt partitioned drive, where Windows only boots from gpt with UEFI. Both systems only boot from MBR with BIOS.

---

### Post by josephellengar2 on 2013-09-11
> **oldfred said:**
> gpt is partitioning that has replaced MBR(msdos). I have used gpt on my old BIOS system since 10.10. And all new drives I partition with gpt with both efi & bios_grub partitions, so I can move drives to a new UEFI system later. 

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

 GPT fdisk Tutorial -srs5694 in forums - gdisk is in repository
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

UEFI uses gpt, BIOS uses MBR(msdos). But Ubuntu will boot with either UEFI or BIOS from a gpt partitioned drive, where Windows only boots from gpt with UEFI. Both systems only boot from MBR with BIOS.

Ok, that makes sense. Now, if I use the 12.04.3 install iso, will that automatically use gpt? Or do I have to download a more recent version of Ubuntu or gparted to get the advantages of gpt?

And then the bigger question is, once I set up the partition table as I describe in the above post, what is the best way to migrate the installation? I really want to migrate everything, including, for example, my login screen setups, my cron jobs, etc, so I can't just copy over the home folder.

I was thinking about using clonezilla and just cloning the home and root partitions on my current computer onto my new SSD, but I'm worried about:
a) the new partition scheme that you describe 
b) the possible hardware issues 
c) not getting the advantages of aligned partitions and whatnot that come with a fresh install
d) Clonezilla doesn't deal well with changes in the size of partitions, even if you go from smaller to bigger.

Note: I am a moderately but not very experienced Linux user. I have no qualms with using command-line or script-based tools to do this.

---

### Post by oldfred on 2013-09-11
I think Ubuntu only defaults to gpt with UEFI and drives somewhere over 1TB that are blank. But gpt is only required with drives over 2TB or any size drive with UEFI.
I always partition in advance and use gparted. But you have to select gpt right at the beginning under device settings.

If copying partitions from old drive then MBR may be better, but you still should partition in advance so make sure you have alignment. Older systems did not do what the new one's do for alignment. New versions of gparted and gdisk automatically will create partitions with correct alignment.

You can install and then copy system files you do know you have extra configurations in like your cron jobs. Most system wide setup data is in /etc. But I do not like to copy all of /etc as some things change and newer configuration files are more correct. I often had similar issues with upgrades when it asked to keep my config or use system maintainers and either answer was wrong. I usually would want new settings but with my configuration. So I separately backup any system wide changes I do, mostly grub, fstab and few others and modify those after a clean install.

 I believe now in clean installs and my backups are to recover my configuration after a new clean install.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

    
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

            Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

            More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by josephellengar2 on 2013-09-12
> **oldfred said:**
> I think Ubuntu only defaults to gpt with UEFI and drives somewhere over 1TB that are blank. But gpt is only required with drives over 2TB or any size drive with UEFI.
I always partition in advance and use gparted. But you have to select gpt right at the beginning under device settings.

[...]

            More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Is it possible to just clone the partitions on my computer and moves the clones to the new one? I know that I'll probably have hardware trouble, but I'd imagine that fixing that will be faster and easier than redoing all of my settings. Is there a tool that can do this simply? Of course I would partition first and then move the data (about 10 GB). And then I guess I'd have to reinstall GRUB.

---

### Post by oldfred on 2013-09-12
I would just rsync data over. Any UUIDs would have to be updated like fstab and grub reinstalled from liveCD. But is new system UEFI and old BIOS? Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.

---

### Post by josephellengar2 on 2013-09-12
> **oldfred said:**
> I would just rsync data over. Any UUIDs would have to be updated like fstab and grub reinstalled from liveCD. But is new system UEFI and old BIOS? Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.

Okay, would you mind checking my proposed plan below? Everything here is how I would do it if I were to do it alone. My question is whether this is correct or if I'm really screwing up rsync.

So, suppose that my current installation is on /dev/sdaX and my new hard drive is plugged into my computer as /dev/sdcX

In this example we will assume that sdaX corresponds to sdcX. I normally have one partition for root and one partition for home, I put my swap on a hdd instead of my ssd so I don't need to worry about that. I also normally don't have a separate boot partition (does that matter?).

So first I would have the new /home partition mounted at /home/ross/mount and execute the following with the working director being /home:

```

sudo rsync -r -g -t -W -v -x /home /home/ross/mount

```

The idea here is to transfer everything from /home to new /home
Options:
-r =recursive
-g= preserve group
-t= preserve file modification times
-W= copy files whole
-v = verbose
-x = don't cross filesystem boundaries

Next I would have the new root partition mounted at /home/ross/mount and execute the following with the working directory being /:

```

sudo rsync -r -g -t -W -v -x --exclude /home /home/ross/mount

``` 

All of the options here are the same as above, except for --exclude, which excludes that directory from the transfer

Once those rsync operations are done, I guess I have to update my fstab as follows:

1) Right now I have no UUID's in my fstab (removed it earlier for the sake of flexibility) so all I really have to do is modify the drive/partition numbers to correspond to whatever the new partitions are. 

2) I would also have to partition my second drive to create a swap space and direct the fstab to use that. Do I have to do anything else to get a swap partition to work?

Then I put the hard disk in my new computer and I have to use Boot repair. I insert my 12.04 live cd and run these commands:

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[LEFT][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][/LEFT]
sudo apt-get install -y boot-repair && (boot-repair &)[LEFT][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][/LEFT]
I've never used this tool before so I'm not sure what I would do to convert BIOS to UEFI. It looks like the tool is graphical and doesn't have that specifically. Any suggestions there?

So, what do you think about this plan?

---

### Post by oldfred on 2013-09-12
Your process seems ok to me. But I really do not know rsync. I just copied some setting suggested in this thread.

       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)


 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

My excluded file includes a lot of temporary or cache files that do not have to be copied.
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks


I have not used Boot-Repair to convert from BIOS to UEFI. But many users have and a few the other way, so it cannot be difficult.

---

### Post by josephellengar2 on 2013-09-17
Hi.

So, I went through the process that we discussed and it worked almost perfectly. The only thing that doesn't work is my graphics driver. I'm stuck in 800x600 resolution and whenever I try to install the nvidia driver I get an error simply saying it failed. 

EDIT: I also have no compositing, problematic.

Jockey log:

```


2013-09-17 15:35:48,452 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319

2013-09-17 15:35:48,452 WARNING: /sys/module/nvidia_319/drivers does not exist, cannot rebind nvidia_319 driver
2013-09-17 15:36:05,937 DEBUG: Shutting down

```

I tried uninstalling nvidia and using nouveau and it wouldn't even start. Then I tried reinstalling nvidia. I have also deleted and remade various configuration files including xconfig and xmonitor.conf. I have no drivers blacklisted. Suggestions?

---

### Post by oldfred on 2013-09-17
What version of Ubuntu. Some have needed headers to get nVidia to install correctly.

       # You may need headers first - meta package for 12.10 version:
# If you can get to command line with nomodeset or recovery mode:

 apt-get update
sudo apt-get install linux-headers-generic


 # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

      
 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 

      
 From  bogan
To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.


 See post #19 by Bogan on nVidia drivers from nVidia.
[http://ubuntuforums.org/showthread.php?t=2075318](http://ubuntuforums.org/showthread.php?t=2075318)

---

### Post by josephellengar2 on 2013-09-18
Thank you very much. You have been very helpful. Unfortunately, I still can't get Nvidia to install correctly. I do have all of the appropriate headers for my kernel installed but the Nvidia driver doesn't like them because they don't have the exact same name as the kernel (since I'm using x64). I'm using 12.04 btw.

> 
 # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


So here's what I've been doing. What I follow the directions that you gave me through step by step, and I install nvidia-current from the repositories, I then do nvidia-xconfig. This screws up everything. I get into the 800x600 resolution and have to uninstall nvidia, delete config files, and restart to get it to work.

> 
 From  bogan
To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a  re-installation even if the currently installed version is the same as  the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check  that 'dkms' is installed and offer the option to register the driver  with dkms, so the kernal module gets updated automatically when a new  kernal is installed. and does not need to be manually re-installed.


THis advice seems to be related to installing the driver manually. I'm willing to do this, even at the expense of having to reinstall manually later, but when I do I get an error saying that it can't find my kernel source for the same reason that I mentioned at the top. I can't quite figure out how to tell dkms where the source is. There is an option --kernelsourcedir= but it doesn't quite work when I enter

```

sudo dkms --kernelsourcedir=/usr/src/linux-headers-3.2.0-53

```

My only thought is that there could be some weird config files sitting around since this *is* an installation that I migrated from another computer. Any advice?

Thanks!

---

### Post by oldfred on 2013-09-18
Old drivers could be an issue. But I thought the commands suggested by Bogan in several threads suggests housecleaning old drivers.

If very new hardware but 12.04.3 you may still need the newest kernel & nVidia that is available with 13.10. I might install both or make just another 10 to 20GB / (root) on drive and try 13.10 to see if it works better. If not then you still have your 12.04 version.

---

### Post by josephellengar2 on 2013-09-18
At this point I"m having an nvidia-specific problem and I don't think this thread is appropriate any longer. I posted my current questions over here if you have any advice:[http://ubuntuforums.org/showthread.php?t=2175372&p=12792983#post12792983](http://ubuntuforums.org/showthread.php?t=2175372&p=12792983#post12792983)

Marked thread as solved. Thanks for all of your help!

---

### Post by josephellengar2 on 2013-09-28
> **oldfred said:**
> Old drivers could be an issue. But I thought the commands suggested by Bogan in several threads suggests housecleaning old drivers.

If very new hardware but 12.04.3 you may still need the newest kernel & nVidia that is available with 13.10. I might install both or make just another 10 to 20GB / (root) on drive and try 13.10 to see if it works better. If not then you still have your 12.04 version.

Hey, I just wanted to let you know that I took your advice and installed 13.10. It's working great and I"ve got it all set up the way I like. Thanks!

---

### Post by oldfred on 2013-09-28
Glad you got it working. :)

---

