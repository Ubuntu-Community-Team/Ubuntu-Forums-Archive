---
title: "Installing grub on boot device failed, continue?"
date: 2013-01-07
forum: General Help
---

### Post by Col-1023 on 2013-01-07
I'm running ubuntu 12.04 lts amd64, and when I ran software updater today there were recommended updates, some of which which were for grub and grub 2.0.

I installed the updates and up came a menue where I had to choose which drives to install grub on, I checked help and it suggested checking all drives.

The drives listed [I'm sure this is the whole list] were,

/dev/sda  [750,000m]
/dev/sda1 \boot  [103m]
/dev/sda2 \
/dev/sdb
/dev/sdc

[note] - I hope I have the slashes around the right way, but I probably don't since I rarely use the command line.

sda, ia the drive where my os [ubuntu only] and home partitions are, sbb and sdc are 2 other 750 gb data drives.

I chose to install grub on the first 3 items, sda, sda1 and sda2, and got the error "installing grub on boot device failed, continue", and I had to check this error to continue the installation.

The rest of the updates finished fine.

Is this a problem, and if it is how, and if I need to fix it, how.

Thaks in advance.

---

### Post by sudodus on 2013-01-07
Normally install grub to the head of the first drive, /dev/sda. Don't install grub to partitions, unless you have to install it somewhere else because you don't want to change the existing boot sector on /dev/sda.

In your case, if you have no problems, then don't worry, only remember (or check this thread again) what to do next time :-)

---

### Post by Col-1023 on 2013-01-07
Thanks Sudodus for your quick reply.

So It wasn't really an error or a failure, the message was just telling me that grub would not be installed to partions sda1 and sda2?

I've checked filesystem\boot\grub and alot of files were modified today, so I hope it all went well.

---

### Post by sudodus on 2013-01-07
> **Col-1023 said:**
> Thanks Sudodus for your quick reply.

So It wasn't really an error or a failure, the message was just telling me that grub would not be installed to partions sda1 and sda2?

I've checked filesystem\boot\grub and alot of files were modified today, so I hope it all went well.
Well, you will probably find out next time you reboot.

---

### Post by Col-1023 on 2013-01-07
Well, I'm in a bit of a panic, I've had at my menu.lst file, and for the grub 2 chainload it needs the fire /grub/core.img.

I've looked through my grub folder and can't find the core.img file, I'm wondering what other files I'm missing after the problem above, and how I can correct this before rebooting.

I don't want the system to just hang obviously, but I have the horrible feeling it will if I reboot now, so any help appreciated, thanks.

---

### Post by oldfred on 2013-01-07
So are you still using grub legacy to chainload to grub2? That was the case for a short while to let you see that grub2 worked and then convert. Not sure if the auto conversion they suggested then still works. 

You can just uninstall both grub & grub2 and reinstall grub2. You can use Boot-Repair or manually. Best to run the BootInfo report first just to document currrent install. And of course have good backups.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       # kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
# HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Col-1023 on 2013-01-07
I've found a tool called BOOT REPAIR GUI, it claims to easily fix moxt grub problems.

When the guide to boot repair talks about installing it, it assumes the system has already failed, and you are using an ubuntu cd or usb stick.

Since I haven't rebooted my system yet, as I'm sure it will fail with no core.imp file, can I download and use boot repair gui on my CURRENTLY RUNNING SYSTEM.

My os is running on the sda drive and that's the one boot repair will have to re-install grub 2 on.

Thanks in advance

---

### Post by Col-1023 on 2013-01-07
Thanks Oldfred, I was typing my post as yours came in.

Yes I am running GRUB 2, but I had problems with the last update.

I will look at the boot-info tool, I assume this can be run on my running system as well?

---

### Post by oldfred on 2013-01-07
You can run it just about anywhere, your current system, a liveCD/DVD/Flash or download as a full repair ISO or a full install ISO with it included.
Boot-Repair runs bootinfoscript, but adds some more useful info, which is just a bash script that we used before Boot-Repair to analyze boot issues. I still run script as part of my rsync backup, just to document system.

---

### Post by Col-1023 on 2013-01-07
Thanks Oldfred, here is the bootinfo url.


[http://paste.ubuntu.com/1508195/](http://paste.ubuntu.com/1508195/)

---

### Post by Col-1023 on 2013-01-07
I looked at the info from the url, and didn't understand alot of it, but I noticed that maany of my sda partitions, sda1, sda2, sda5 were flagged as raid, or linux-raid.

I don't have a raid system, so don't know how this could happen, my system has worked fine for the last 4 years with these partitions.

Hope this helps in solving my problem.

---

### Post by oldfred on 2013-01-08
I do not know RAID and usually try to avoid most of the RAID type installs, but occasionally get involved.

Other than the partition table entries, it does not look like a RAID install, but there are multiple types of RAID which can add to the confusion. Software RAID often has /mapper/xxxxx as mount points not devices like /dev/sda. True hardware RAID will not show second drive and it looks like a standard system.

It is showing 3 750GB drives, is that correct and are they really separate? If system had hardware RAID and we attempt to remove something it may cause huge issues.

You normally just install grub to the MBR of the same drive as your install. I have different installs in different drives and do then have different grubs in each drive, but primarily boot only sdd, now. The new grub2 is larger than old grub legacy and does not really install to partitions. With grub legacy we could easily install to partitions and chainload from another grub. Grub2 lets us direct boot another install so chain loading is not required.

Separately it may be time to house clean out old kernels, you seem to have a few. I like to keep current and past current just to have another that works.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# List kernels 
dpkg --list | grep linux-image
# or
cd /boot
ls vmlinuz* 
    
       In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by Col-1023 on 2013-01-08
Thanks Oldfred, sorry for the late reply, I just woke up and got back on the pc.

Yes there are 3 X 750 GB drives and they are separate.

sda has multiple partitions for boot, root, home and swap whereas sdb and sdc just have one partition for the whole drive.

Ubuntu the only operating system on this pc is on sda.

---

### Post by oldfred on 2013-01-08
I would backup partition table and see if Disk Utility will just let me change the partition type to 83.

       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

    
Do not reformat in Disk Utility but just choose edit partition and change type type to 83. If required also ext3 as that seems to be the format your have.

If disk utility will not change it, then we can edit PTsda.txt and read it back in.

---

### Post by Col-1023 on 2013-01-08
Thanks Oldfred, I've still got jobs running on this pc, and I'll have to backup alot of data before I do anything first, and that will take awhile.

Just wondering about the partition type, this has never been a problem before, It was the upgrading of grub and my wrong choice in the menue that caused all this.

I'm worried that by mucking around with partition types this could completely currupt the sda drive.

---

### Post by oldfred on 2013-01-09
Have not seen your specific issue with RAID and I do not know if that is related to the grub install for sure. But grub2 keeps adding new capabilities and then finds something that was not quite right and stops working. Grub legacy did not directly boot LVM nor RAID and had to have a separate /boot partition for the kernel to load the RAID drivers. Grub2 has many more drivers available as add in modules.

We have changed partition type on NTFS partitions and used it for some other repairs, but of  course good backups are required. 

The only time I have seen RAID partition type is with RAID. Almost all the boot scripts I look at have the type 83 for standard Linux.

---

### Post by Col-1023 on 2013-01-14
I've backed up all the data I want to keep, and have done some more research.

About removing the old kernels, synaptics offers 2 options, removal, or COMPLETE removal, which option should I choose to remove my old kernels?


It seems that linux doesn't take any notice of the raid flag, the raid driver is the main consideration.

Also looking at tthe bottom of the boot-repair report, it suggests it will do this,


=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda (750GB) disc!

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix legacy files) and reinstall the grub2 of sda2 into the MBRs of all disks (except USB without OS), using the following options:        sda1/boot,
The boot flag would be placed on sdb1.
Additional repair would be performed: unhide-bootmenu-10s



I'm hoping this, being a fairly simple solution will work, otherwise I have a usb stick with 12.04 lts on it, to beet back into.

---

### Post by Col-1023 on 2013-01-14
I've just been reading this,

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

It says that when you delete linux images via synaptic, the grub.cfg file it updated.

Since my grub is borked, I should do the boot-repair before the kernel cleanupups.

Would grub2 have a problem with the large number of kernels I have on my install?

---

### Post by sudodus on 2013-01-14
> **Col-1023 said:**
> ...
Would grub2 have a problem with the large number of kernels I have on my install?

There should be no problem to manage several old kernels.

---

### Post by Col-1023 on 2013-01-14
Boot-repair said the repair was successful, hopefully its right, here is the url.


[http://paste.ubuntu.com/1530858](http://paste.ubuntu.com/1530858)

---

### Post by Col-1023 on 2013-01-14
I thought I'd look around before I rebooted, and I've noticed that all the linux images and the grub directory have gone from /boot,in fact the /boot directory is completely empty.

Any idea where these files have been moved, and where grub is installed now?

---

### Post by oldfred on 2013-01-14
Did you not tick the option of separate /boot?

Script shows /boot, fstab shows /boot in sda1, but it looks like grub update ran from sda2 which if a full reinstall of grub2 would reinstall as if you did not have a separate /boot. If just an update I am not sure. Either do a full reinstall of grub or rerun with separate /boot checked off.

You may want to houseclean the old kernels, you have a lot. I like to keep current and previous just to have another in case issues on current one occur.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# all kernels 
dpkg --list | grep linux-image

 In synaptic or software center search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by Col-1023 on 2013-01-14
I pressed the space bar for the sda option because you said to tick drives, not partitions, and the /boot partition is sda1, while the root partion / is sda2.

In a terminal I ran,

grub-install -v
grub-install (GRUB) 1.99-21ubuntu3.7

This seems to show that grub2 is installed according to what I read.

I just want to know where all the files are?

---

### Post by Col-1023 on 2013-01-14
I ran boot-info again to see if the boot need repair, here's the url.

[http://paste.ubuntu.com/1531086/](http://paste.ubuntu.com/1531086/)

---

### Post by oldfred on 2013-01-14
I am almost sure the boot repair will say separate /boot used to make repair. 

See grub location under advanced options. There is a box for separate /boot, You must check that and rerun it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Col-1023 on 2013-01-14
Ok, I'll go into the advanced settings tick the separate boot option, rerun the boot-repair, and see what happens, thanks.

---

### Post by Col-1023 on 2013-01-14
Interesting, boot-repair had the separate boot option already ticked as sda1 [which is correct], it is also greyed out.

the interesting thing is that boot repair and the grub install command says grub2 is installed, and it found all my old linux images, so they must be on my system somewhere.

---

### Post by Col-1023 on 2013-01-14
Ok, I found al the files, they've been moved to,

/mnt/boot-sav/sda1/

the repair might have worked.

---

### Post by Col-1023 on 2013-01-14
Now when I look in that directory, it is empty, this is odd.

typing dpkg --list | grep linux-image

in a terminal still gets me all my linux images, so there out there somewhere.

---

### Post by Col-1023 on 2013-01-14
My separate /boot partition is only 103 md, is this too small for the number of kernels I have, 

I Used synaptic to remove the old linux-image files marked green, and according to synaptic, they are gone, however when I do,

dpkg --list | grep linux-image

in a terminal, it shows all my old kernels still there.

---

### Post by Col-1023 on 2013-01-14
I used the mark for removal option in synaptic, when it seems I should have used mark for COMPLETE removal.

is this a problem, and if so how can I fix it.

[http://paste.ubuntu.com/1533208/](http://paste.ubuntu.com/1533208/)

I've noticed this from line 605,

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.656596661 = 0.705015296    grub/core.img                                  1
   0.726611614 = 0.780193280    grub/grub.cfg                                  1
   0.137710094 = 0.147865088    initrd.img-2.6.27-11-generic                   5
   0.008903027 = 0.009559552    initrd.img-2.6.28-17-generic                   3
   0.083297253 = 0.089439744    initrd.img-2.6.31-16-generic                   4
   0.097083569 = 0.104242688    initrd.img-2.6.31-17-generic                   4
   0.069877148 = 0.075030016    initrd.img-2.6.31-19-generic                   3
   0.062293530 = 0.066887168    initrd.img-2.6.31-20-generic                   3
   0.110843182 = 0.119016960    initrd.img-2.6.31-21-generic                   5
   0.148406506 = 0.159350272    initrd.img-2.6.31-22-generic                   5
   0.584254742 = 0.627338752    initrd.img-2.6.32-42-generic                   9
   0.603141308 = 0.647618048    initrd.img-3.2.0-30-generic                   12
   0.137244701 = 0.147365376    initrd.img-3.2.0-31-generic                   12
   0.484157085 = 0.519859712    initrd.img-3.2.0-32-generic                    6
   0.449126720 = 0.482246144    initrd.img-3.2.0-33-generic                    6
   0.518432140 = 0.556662272    initrd.img-3.2.0-34-generic                    9
   0.536864758 = 0.576454144    initrd.img-3.2.0-35-generic                   13
   0.026149273 = 0.028077568    vmlinuz-2.6.27-11-generic                      2
   0.076301098 = 0.081927680    vmlinuz-2.6.28-17-generic                      2
   0.013225079 = 0.014200320    vmlinuz-2.6.31-16-generic                      2
   0.086974621 = 0.093388288    vmlinuz-2.6.31-17-generic                      2
   0.043185711 = 0.046370304    vmlinuz-2.6.31-19-generic                      2
   0.121127605 = 0.130059776    vmlinuz-2.6.31-20-generic                      2
   0.019595623 = 0.021040640    vmlinuz-2.6.31-21-generic                      2
   0.112407207 = 0.120696320    vmlinuz-2.6.31-22-generic                      5
   0.577964306 = 0.620584448    vmlinuz-2.6.32-42-generic                      2
   0.583255291 = 0.626265600    vmlinuz-3.2.0-30-generic                      10
   0.115108013 = 0.123596288    vmlinuz-3.2.0-31-generic                       4
   0.052680492 = 0.056565248    vmlinuz-3.2.0-32-generic                       3
   0.492370129 = 0.528678400    vmlinuz-3.2.0-33-generic                       3
   0.493361950 = 0.529743360    vmlinuz-3.2.0-34-generic                       4
   0.453765392 = 0.487226880    vmlinuz-3.2.0-35-generic                       3

this from line 780,

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.239258766 = 15.289287680   boot/grub/grub.cfg                             1

and this in line 808,

=================== No kernel in /boot:
grub


/boot detected in the fstab of sda2: UUID=f161f9cb-e2c7-4a05-9bb8-4f4b51025df1  (sda1)

I did use synaptic to "mark for removal" all the linux-images up to 3.2.0.32, and yet they still appear in this boot-info report.

From what the report is saying, boot repair is trying to install these files in sda1, my separate boot partition, the report seems to say there are actually no kernels installed in this partition, just grub.cfg and core.img.

---

### Post by Col-1023 on 2013-01-15
I ran boot repair again after marking for removal all those kernels,

[http://paste.ubuntu.com/1533384/](http://paste.ubuntu.com/1533384/)

I can't untick the separate boot partition option in advanced settings, it is greyed out as ticked, with the location being sda1.

/boot/grub/ now has 207 items in it, which I assume are most of those needed for grub, however the linux-image files, etc are missing.

Using synaptic however, and searching for linux-image, finds the latest 3 kernels still installed, here is what is says about linux-image-3.2.0.33

/.
/boot
/boot/System.map-3.2.0-33-generic
/boot/abi-3.2.0-33-generic
/boot/config-3.2.0-33-generic
/boot/vmlinuz-3.2.0-33-generic

Synaptic also says the package uses 149 mb of space, but I don't know where.

Doing a search of my file system for linux-image reveals only 1 linux-image deb file there, namely linux-image-3.2.0.25.55, which is my latest kernel, however it is located at /var/cache/apt/archives, so it's likely just the backup deb package.

In line 879 of the last pastbin above, it still says "no kernel in /boot"

The boot-info output still shows the kernels I deleted as being there, so should I tick the option on advanced of boot repair to purge all kerenls except the latest?

TIA.

---

### Post by oldfred on 2013-01-15
Yes you should be able to delete all the old boot files. The boot files are both vmlinuz and initrd.  
But, it looks like you may be missing the current initrd?

But you need to be sure you have the newest kernel correct installed. This will reinstall if not current. (from my chroot procedure which does not have sudo on every line, so use the sudi -i first).

       #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

---

### Post by Col-1023 on 2013-01-15
Thanks very much for your help Fred, I've looked at the bootinfo output and it looks like the current kernel is not installed in /boot.

So you are saying I should use these commands in this order,

sudo -i
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get dist-upgrade
sudo apt-get -f install
dpkg --configure -a


1 - Do I need sudo on each line, since I noticed you have sudo apt-get -f install?

2 - Do I run these commands one after the other in the above order?

3 - Installing or re-installing the latest kernel will mean a reboot, but will I be able to check that it is going to be usable before I reboot?

Is there any danger these commands might break something, or are they fairly safe?

Thanks alot for your help.

---

### Post by sudodus on 2013-01-15
> **oldfred said:**
> ... This will reinstall if not current. (from my chroot procedure which does not have sudo on every line, so use the sudi -i first).

       #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
Thanks for sharing :-)

---

### Post by oldfred on 2013-01-15
You can do sudo -i to allow you to run multiple commands without sudo on each line. See man sudo. Best to close terminal afterwards so you are still not in sudo.

All the commands do is update system.  The dist-upgrade should make sure you have at least the most current kernel installed. If you have the separate /boot partition in fstab then grub & kernels should be in the partition, otherwise in the folder /boot that is inside / (root).

---

### Post by Col-1023 on 2013-01-15
Thanks Fred, I'll give this a try and see what happens.

---

### Post by Col-1023 on 2013-01-15
Here is the bootinfo report after running those commands.


[http://paste.ubuntu.com/1536246/](http://paste.ubuntu.com/1536246/)

Here is the output from terminal after running the commands,

```


david@liberator:~$ sudo -i
[sudo] password for david: 
root@liberator:~# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del flashplugin-installer 11.2.202.258ubuntu0.12.04.1 [8,012 B]
root@liberator:~# apt-get clean
root@liberator:~# apt-get update
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise InRelease
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates InRelease                          
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security InRelease                         
Ign [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports InRelease                        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise Release.gpg                                
Get:1 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates Release.gpg [198 B]              
Get:2 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security Release.gpg [198 B]             
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports Release.gpg                      
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise Release                                    
Get:3 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates Release [49.6 kB]                
Get:4 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security Release [49.6 kB]               
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports Release                          
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/main Sources                               
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/restricted Sources                         
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/universe Sources                           
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/multiverse Sources                         
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/main amd64 Packages                        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/restricted amd64 Packages                  
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/universe amd64 Packages                    
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/multiverse amd64 Packages                  
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/main i386 Packages                         
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/restricted i386 Packages                   
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/universe i386 Packages                     
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/multiverse i386 Packages                   
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/main TranslationIndex                      
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid InRelease                            
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/multiverse TranslationIndex                
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/restricted TranslationIndex                
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/universe TranslationIndex                  
Get:5 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/main Sources [200 kB]            
Get:6 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/restricted Sources [4,743 B]     
Get:7 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/universe Sources [69.8 kB]       
Get:8 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/multiverse Sources [4,240 B]     
Get:9 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/main amd64 Packages [452 kB]     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Get:10 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/restricted amd64 Packages [8,943 B]
Get:11 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/universe amd64 Packages [167 kB]
Get:12 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/multiverse amd64 Packages [8,654 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:13 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/main i386 Packages [460 kB]     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner amd64 Packages               
Get:14 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/restricted i386 Packages [8,999 B]
Get:15 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/universe i386 Packages [169 kB] 
Get:16 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/multiverse i386 Packages [9,678 B]
Get:17 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/main TranslationIndex [3,564 B] 
Get:18 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/multiverse TranslationIndex [2,605 B]
Get:19 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/restricted TranslationIndex [2,461 B]
Get:20 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/universe TranslationIndex [2,850 B]
Get:21 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/main Sources [60.4 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:22 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/restricted Sources [1,950 B]   
Get:23 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/universe Sources [19.3 kB]     
Get:24 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/multiverse Sources [1,379 B]   
Get:25 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/main amd64 Packages [215 kB]   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner i386 Packages                
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner TranslationIndex             
Get:26 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/restricted amd64 Packages [3,969 B]
Get:27 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/universe amd64 Packages [60.8 kB]
Get:28 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/multiverse amd64 Packages [2,184 B]
Get:29 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/main i386 Packages [222 kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:30 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/restricted i386 Packages [3,968 B]
Get:31 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/universe i386 Packages [61.8 kB]
Get:32 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/multiverse i386 Packages [2,366 B]
Get:33 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/main TranslationIndex [74 B]   
Get:34 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/multiverse TranslationIndex [71 B]
Get:35 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/restricted TranslationIndex [71 B]
Get:36 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/universe TranslationIndex [73 B]
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/restricted amd64 Packages        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/main amd64 Packages              
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/multiverse amd64 Packages        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/universe amd64 Packages          
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/restricted i386 Packages         
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/main i386 Packages               
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/multiverse i386 Packages         
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/universe i386 Packages           
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/main TranslationIndex            
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/multiverse TranslationIndex      
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/restricted TranslationIndex      
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/universe TranslationIndex        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/main Translation-en_AU                     
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/main Translation-en                        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/multiverse Translation-en_AU               
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/multiverse Translation-en                  
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/restricted Translation-en_AU               
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/restricted Translation-en                  
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise/universe Translation-en                    
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/main Translation-en_AU             
Get:37 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/main Translation-en [222 kB]    
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/multiverse Translation-en_AU       
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/multiverse Translation-en          
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/restricted Translation-en_AU       
Get:38 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/restricted Translation-en [2,193 B]
Get:39 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-updates/universe Translation-en [99.9 kB]
Get:40 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/main Translation-en [105 kB]   
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/multiverse Translation-en         
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/restricted Translation-en         
Get:41 [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-security/universe Translation-en [37.4 kB]
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/main Translation-en              
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/multiverse Translation-en        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/restricted Translation-en        
Hit [http://ftp.iinet.net.au](http://ftp.iinet.net.au) precise-backports/universe Translation-en          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_AU            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                    
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Get:42 [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg [198 B]
Get:43 [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release [6,851 B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_AU               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_AU
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 2,803 kB in 42s (66.4 kB/s)
Reading package lists... Done
root@liberator:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  activity-log-manager-common activity-log-manager-control-center dpkg
  libfreetype6 libnm-glib-vpn1 libnm-glib4 libnm-util2 libnspr4 libnspr4-0d
  libnss3 libnss3-1d libvlc5 libvlccore5 network-manager vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse x11-common xbase-clients xorg
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all
25 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.7 MB of archives.
After this operation, 976 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main dpkg amd64 1.16.1.2ubuntu7.1 [1,830 kB]
Get:2 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main libfreetype6 amd64 2.4.8-1ubuntu2.1 [343 kB]
Get:3 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe libnspr4-0d amd64 4.9.4-0ubuntu0.12.04.1 [11.3 kB]
Get:4 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main libnspr4 amd64 4.9.4-0ubuntu0.12.04.1 [141 kB]
Get:5 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main libnss3-1d amd64 3.14.1-0ckbi1.93ubuntu.0.12.04.1 [13.4 kB]
Get:6 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main libnss3 amd64 3.14.1-0ckbi1.93ubuntu.0.12.04.1 [1,189 kB]
Get:7 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main libnm-util2 amd64 0.9.4.0-0ubuntu4.2 [136 kB]
Get:8 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main libnm-glib4 amd64 0.9.4.0-0ubuntu4.2 [84.6 kB]
Get:9 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main network-manager amd64 0.9.4.0-0ubuntu4.2 [531 kB]
Get:10 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main activity-log-manager-control-center amd64 0.9.4-0ubuntu3.2 [87.2 kB]
Get:11 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main activity-log-manager-common all 0.9.4-0ubuntu3.2 [19.3 kB]
Get:12 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main libnm-glib-vpn1 amd64 0.9.4.0-0ubuntu4.2 [14.4 kB]
Get:13 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe vlc-plugin-notify amd64 2.0.5-0ubuntu0.12.04.1 [6,148 B]
Get:14 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe vlc-plugin-pulse amd64 2.0.5-0ubuntu0.12.04.1 [22.1 kB]
Get:15 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe vlc amd64 2.0.5-0ubuntu0.12.04.1 [1,373 kB]
Get:16 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe libvlccore5 amd64 2.0.5-0ubuntu0.12.04.1 [418 kB]
Get:17 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe vlc-data all 2.0.5-0ubuntu0.12.04.1 [9,466 kB]
Get:18 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe vlc-nox amd64 2.0.5-0ubuntu0.12.04.1 [2,817 kB]
Get:19 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/universe libvlc5 amd64 2.0.5-0ubuntu0.12.04.1 [45.5 kB]
Get:20 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main x11-common all 1:7.6+12ubuntu2 [52.0 kB]
Get:21 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main xbase-clients all 1:7.6+12ubuntu2 [2,322 B]
Get:22 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main xserver-xorg-video-all amd64 1:7.6+12ubuntu2 [5,026 B]
Get:23 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main xserver-xorg-input-all amd64 1:7.6+12ubuntu2 [4,928 B]
Get:24 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main xserver-xorg amd64 1:7.6+12ubuntu2 [77.0 kB]
Get:25 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) precise-updates/main xorg amd64 1:7.6+12ubuntu2 [2,718 B]
Fetched 18.7 MB in 14s (1,280 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 445888 files and directories currently installed.)
Preparing to replace dpkg 1.16.1.2ubuntu7 (using .../dpkg_1.16.1.2ubuntu7.1_amd64.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
Setting up dpkg (1.16.1.2ubuntu7.1) ...
(Reading database ... 445889 files and directories currently installed.)
Preparing to replace libfreetype6 2.4.8-1ubuntu2 (using .../libfreetype6_2.4.8-1ubuntu2.1_amd64.deb) ...
Unpacking replacement libfreetype6 ...
Preparing to replace libnspr4-0d 4.8.9-1ubuntu2.3 (using .../libnspr4-0d_4.9.4-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libnspr4-0d ...
Preparing to replace libnspr4 4.8.9-1ubuntu2.3 (using .../libnspr4_4.9.4-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libnspr4 ...
Preparing to replace libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu6.1 (using .../libnss3-1d_3.14.1-0ckbi1.93ubuntu.0.12.04.1_amd64.deb) ...
Unpacking replacement libnss3-1d ...
Preparing to replace libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1 (using .../libnss3_3.14.1-0ckbi1.93ubuntu.0.12.04.1_amd64.deb) ...
Unpacking replacement libnss3 ...
Preparing to replace libnm-util2 0.9.4.0-0ubuntu4.1 (using .../libnm-util2_0.9.4.0-0ubuntu4.2_amd64.deb) ...
Unpacking replacement libnm-util2 ...
Preparing to replace libnm-glib4 0.9.4.0-0ubuntu4.1 (using .../libnm-glib4_0.9.4.0-0ubuntu4.2_amd64.deb) ...
Unpacking replacement libnm-glib4 ...
Preparing to replace network-manager 0.9.4.0-0ubuntu4.1 (using .../network-manager_0.9.4.0-0ubuntu4.2_amd64.deb) ...
Unpacking replacement network-manager ...
Preparing to replace activity-log-manager-control-center 0.9.4-0ubuntu3.1 (using .../activity-log-manager-control-center_0.9.4-0ubuntu3.2_amd64.deb) ...
Unpacking replacement activity-log-manager-control-center ...
Preparing to replace activity-log-manager-common 0.9.4-0ubuntu3.1 (using .../activity-log-manager-common_0.9.4-0ubuntu3.2_all.deb) ...
Unpacking replacement activity-log-manager-common ...
Preparing to replace libnm-glib-vpn1 0.9.4.0-0ubuntu4.1 (using .../libnm-glib-vpn1_0.9.4.0-0ubuntu4.2_amd64.deb) ...
Unpacking replacement libnm-glib-vpn1 ...
Preparing to replace vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1 (using .../vlc-plugin-notify_2.0.5-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement vlc-plugin-notify ...
Preparing to replace vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1 (using .../vlc-plugin-pulse_2.0.5-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement vlc-plugin-pulse ...
Preparing to replace vlc 2.0.3-0ubuntu0.12.04.1 (using .../vlc_2.0.5-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement vlc ...
Preparing to replace libvlccore5 2.0.3-0ubuntu0.12.04.1 (using .../libvlccore5_2.0.5-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libvlccore5 ...
Preparing to replace vlc-data 2.0.3-0ubuntu0.12.04.1 (using .../vlc-data_2.0.5-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement vlc-data ...
Preparing to replace vlc-nox 2.0.3-0ubuntu0.12.04.1 (using .../vlc-nox_2.0.5-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement vlc-nox ...
Preparing to replace libvlc5 2.0.3-0ubuntu0.12.04.1 (using .../libvlc5_2.0.5-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libvlc5 ...
Preparing to replace x11-common 1:7.6+12ubuntu1 (using .../x11-common_1%3a7.6+12ubuntu2_all.deb) ...
Unpacking replacement x11-common ...
Preparing to replace xbase-clients 1:7.6+12ubuntu1 (using .../xbase-clients_1%3a7.6+12ubuntu2_all.deb) ...
Unpacking replacement xbase-clients ...
Preparing to replace xserver-xorg-video-all 1:7.6+12ubuntu1 (using .../xserver-xorg-video-all_1%3a7.6+12ubuntu2_amd64.deb) ...
Unpacking replacement xserver-xorg-video-all ...
Preparing to replace xserver-xorg-input-all 1:7.6+12ubuntu1 (using .../xserver-xorg-input-all_1%3a7.6+12ubuntu2_amd64.deb) ...
Unpacking replacement xserver-xorg-input-all ...
Preparing to replace xserver-xorg 1:7.6+12ubuntu1 (using .../xserver-xorg_1%3a7.6+12ubuntu2_amd64.deb) ...
Unpacking replacement xserver-xorg ...
Preparing to replace xorg 1:7.6+12ubuntu1 (using .../xorg_1%3a7.6+12ubuntu2_amd64.deb) ...
Unpacking replacement xorg ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Setting up libfreetype6 (2.4.8-1ubuntu2.1) ...
Setting up libnspr4 (4.9.4-0ubuntu0.12.04.1) ...
Setting up libnspr4-0d (4.9.4-0ubuntu0.12.04.1) ...
Setting up libnss3 (3.14.1-0ckbi1.93ubuntu.0.12.04.1) ...
Setting up libnss3-1d (3.14.1-0ckbi1.93ubuntu.0.12.04.1) ...
Setting up libnm-util2 (0.9.4.0-0ubuntu4.2) ...
Setting up libnm-glib4 (0.9.4.0-0ubuntu4.2) ...
Setting up network-manager (0.9.4.0-0ubuntu4.2) ...
Setting up activity-log-manager-common (0.9.4-0ubuntu3.2) ...
Setting up activity-log-manager-control-center (0.9.4-0ubuntu3.2) ...
Setting up libnm-glib-vpn1 (0.9.4.0-0ubuntu4.2) ...
Setting up vlc-data (2.0.5-0ubuntu0.12.04.1) ...
Setting up libvlccore5 (2.0.5-0ubuntu0.12.04.1) ...
Setting up libvlc5 (2.0.5-0ubuntu0.12.04.1) ...
Setting up vlc-nox (2.0.5-0ubuntu0.12.04.1) ...
Setting up vlc-plugin-notify (2.0.5-0ubuntu0.12.04.1) ...
Setting up vlc-plugin-pulse (2.0.5-0ubuntu0.12.04.1) ...
Setting up vlc (2.0.5-0ubuntu0.12.04.1) ...
Setting up x11-common (1:7.6+12ubuntu2) ...
Setting up xbase-clients (1:7.6+12ubuntu2) ...
Setting up xserver-xorg-video-all (1:7.6+12ubuntu2) ...
Setting up xserver-xorg-input-all (1:7.6+12ubuntu2) ...
Setting up xserver-xorg (1:7.6+12ubuntu2) ...
Setting up xorg (1:7.6+12ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
root@liberator:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@liberator:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fgfs-base libproj0 linux-headers-3.2.0-30 mplayer-nogui libutouch-evemu1
  libutouch-geis1 libutouch-frame1 fgfs-scenery-base libapr1 libogdi3.2
  libcoin60 libpar2-0 libsvn1 libdap11 libgdal1-1.7.0 libpostproc-extra-51
  libgnome-desktop-2-17 fgfs-aircraft-base libepsilon0 libswscale-extra-0
  libxerces-c28 fgfs-models-base libopenthreads14 libhdf5-serial-1.8.4
  libgeos-c1 proj-data libfreexl1 hddtemp libspatialite3 proj-bin
  libutouch-grail1 libgeos-3.2.2 linux-headers-3.2.0-30-generic libhdf4-0-alt
  libaprutil1 simgear2.4.0 libopenscenegraph80 libdapclient3 libnetcdf6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@liberator:~# dpkg --configure -a
root@liberator:~# 


```

The only odd thing was when I tried to shut down terminal, it said there was a process still running, and did I want to kill it, after I looked at the output from terminal, I thought the process might just be the sudo command, so I shut down terminal.

At the bottom is said to run apt-get autoremove, should I do this?

I've looked for the kernels in my filesystem and can't find them, and boodinfo still says no kernel in /boot.

I used gparted, and it says the separate /boot partition is "Not Mounted".

Gparted has option to mount his partition, and to manage [remove] the flags.

If I remove the raid flag from the /boot partition should I leave the partition unmounted, which it is now.

If I use gparted to mount this partition will this do anything to my system, and the fact the partition has remained unmounted, could this be the cause of my grub problems?


Thanks.

---

### Post by oldfred on 2013-01-16
Did you post old bootinfo? You still have all the old kernels in /boot sda1, grub menu shows them as boot options, fstab has /boot so it should be using it to reinstall or bot. And RAID entries are still on partitions. Or I do not see anything has been accomplished??

---

### Post by Col-1023 on 2013-01-16
The bootinfo I posted was done after I ran all the commands.

I agree it seems little has changed.

As I said in my last post, I used gparted and noticed the separate boot partiton on drive sda which is unmounted, all the other partitions in my system are mounted or active.

Is ii normal for a separate /boot partition to remain unmounted while the system is running, if not, then is it ok for me to re-mount it and see what happens?

---

### Post by Col-1023 on 2013-01-16
I just read this thread,


[http://ubuntuforums.org/showthread.php?t=1541294](http://ubuntuforums.org/showthread.php?t=1541294)


If my separate /boot partition has not been mounted while trying all those commands, then according to that thread, the commands won't have any effect.

---

### Post by oldfred on 2013-01-16
If not mounted I am sure that is an issue.

run this 
sudo mount -a

If you get no error messages that is good and since fstab still has /boot it should mount it.

---

### Post by Col-1023 on 2013-01-16
There were no errors, and it changed things.

I looked in my boot folder in file system and all the kernel images etc magically appeared

Here is a new bootinfo,


[http://paste.ubuntu.com/1539763/](http://paste.ubuntu.com/1539763/)

---

### Post by oldfred on 2013-01-16
Do not unmount with gparted or Disk Utility. 

It may be time to go back thru the process. House clean kernels, I believe the image removes both kernel & init files.

---

### Post by Col-1023 on 2013-01-16
Are you suggesting I run these commands again,


sudo -i

apt-get autoclean

apt-get clean

apt-get update

apt-get upgrade

apt-get dist-upgrade

apt-get -f install

dpkg --configure -a


Then do another bootinfo?

---

### Post by Col-1023 on 2013-01-17
The /boot partition is still mounted and accessible in filesystem.

I ran the above commands, here is the terminal output.


```


david@liberator:~$ sudo -i
[sudo] password for david: 
root@liberator:~# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@liberator:~# apt-get clean
root@liberator:~# apt-get update
Ign http://ftp.iinet.net.au precise InRelease
Ign http://ftp.iinet.net.au precise-updates InRelease                          
Ign http://ftp.iinet.net.au precise-security InRelease                         
Ign http://ftp.iinet.net.au precise-backports InRelease                        
Hit http://ftp.iinet.net.au precise Release.gpg                                
Hit http://ftp.iinet.net.au precise-updates Release.gpg                        
Hit http://ftp.iinet.net.au precise-security Release.gpg                       
Hit http://ftp.iinet.net.au precise-backports Release.gpg                      
Hit http://ftp.iinet.net.au precise Release                                    
Hit http://ftp.iinet.net.au precise-updates Release                            
Hit http://ftp.iinet.net.au precise-security Release                           
Hit http://ftp.iinet.net.au precise-backports Release                          
Hit http://ftp.iinet.net.au precise/main Sources                               
Hit http://ftp.iinet.net.au precise/restricted Sources                         
Hit http://ftp.iinet.net.au precise/universe Sources                           
Hit http://ftp.iinet.net.au precise/multiverse Sources                         
Hit http://ftp.iinet.net.au precise/main amd64 Packages                        
Hit http://ftp.iinet.net.au precise/restricted amd64 Packages                  
Hit http://ftp.iinet.net.au precise/universe amd64 Packages                    
Hit http://ftp.iinet.net.au precise/multiverse amd64 Packages                  
Hit http://ftp.iinet.net.au precise/main i386 Packages                         
Hit http://ftp.iinet.net.au precise/restricted i386 Packages                   
Hit http://ftp.iinet.net.au precise/universe i386 Packages                     
Hit http://ftp.iinet.net.au precise/multiverse i386 Packages                   
Hit http://ftp.iinet.net.au precise/main TranslationIndex                      
Hit http://ftp.iinet.net.au precise/multiverse TranslationIndex                
Hit http://ftp.iinet.net.au precise/restricted TranslationIndex                
Hit http://ftp.iinet.net.au precise/universe TranslationIndex                  
Hit http://ftp.iinet.net.au precise-updates/main Sources                       
Ign http://archive.canonical.com intrepid InRelease                            
Hit http://packages.medibuntu.org precise InRelease                            
Hit http://ftp.iinet.net.au precise-updates/restricted Sources                 
Hit http://ftp.iinet.net.au precise-updates/universe Sources                   
Hit http://ftp.iinet.net.au precise-updates/multiverse Sources                 
Hit http://ftp.iinet.net.au precise-updates/main amd64 Packages                
Hit http://ftp.iinet.net.au precise-updates/restricted amd64 Packages          
Hit http://ftp.iinet.net.au precise-updates/universe amd64 Packages            
Hit http://ftp.iinet.net.au precise-updates/multiverse amd64 Packages          
Hit http://ftp.iinet.net.au precise-updates/main i386 Packages                 
Hit http://ftp.iinet.net.au precise-updates/restricted i386 Packages           
Hit http://ftp.iinet.net.au precise-updates/universe i386 Packages             
Hit http://ftp.iinet.net.au precise-updates/multiverse i386 Packages           
Hit http://ftp.iinet.net.au precise-updates/main TranslationIndex              
Hit http://ftp.iinet.net.au precise-updates/multiverse TranslationIndex        
Hit http://ftp.iinet.net.au precise-updates/restricted TranslationIndex        
Hit http://ftp.iinet.net.au precise-updates/universe TranslationIndex          
Hit http://ftp.iinet.net.au precise-security/main Sources                      
Hit http://ftp.iinet.net.au precise-security/restricted Sources                
Hit http://ftp.iinet.net.au precise-security/universe Sources                  
Hit http://ftp.iinet.net.au precise-security/multiverse Sources                
Hit http://ftp.iinet.net.au precise-security/main amd64 Packages               
Hit http://ftp.iinet.net.au precise-security/restricted amd64 Packages         
Hit http://ftp.iinet.net.au precise-security/universe amd64 Packages           
Hit http://ftp.iinet.net.au precise-security/multiverse amd64 Packages         
Hit http://ftp.iinet.net.au precise-security/main i386 Packages                
Hit http://ftp.iinet.net.au precise-security/restricted i386 Packages          
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ftp.iinet.net.au precise-security/universe i386 Packages            
Hit http://ftp.iinet.net.au precise-security/multiverse i386 Packages          
Hit http://ftp.iinet.net.au precise-security/main TranslationIndex             
Hit http://archive.canonical.com intrepid Release.gpg                          
Hit http://ftp.iinet.net.au precise-security/multiverse TranslationIndex       
Hit http://ftp.iinet.net.au precise-security/restricted TranslationIndex       
Hit http://ftp.iinet.net.au precise-security/universe TranslationIndex         
Hit http://ftp.iinet.net.au precise-backports/restricted amd64 Packages        
Hit http://ftp.iinet.net.au precise-backports/main amd64 Packages              
Hit http://ftp.iinet.net.au precise-backports/multiverse amd64 Packages        
Hit http://ftp.iinet.net.au precise-backports/universe amd64 Packages          
Hit http://ftp.iinet.net.au precise-backports/restricted i386 Packages         
Hit http://ftp.iinet.net.au precise-backports/main i386 Packages               
Hit http://ftp.iinet.net.au precise-backports/multiverse i386 Packages         
Hit http://ftp.iinet.net.au precise-backports/universe i386 Packages           
Hit http://ftp.iinet.net.au precise-backports/main TranslationIndex            
Hit http://ftp.iinet.net.au precise-backports/multiverse TranslationIndex      
Hit http://ftp.iinet.net.au precise-backports/restricted TranslationIndex      
Hit http://ftp.iinet.net.au precise-backports/universe TranslationIndex        
Get:1 http://ftp.iinet.net.au precise/main Translation-en_AU [4,434 B]         
Hit http://ftp.iinet.net.au precise/main Translation-en                        
Get:2 http://ftp.iinet.net.au precise/multiverse Translation-en_AU [94.4 kB]   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com intrepid Release                              
Hit http://ftp.iinet.net.au precise/multiverse Translation-en                  
Get:3 http://ftp.iinet.net.au precise/restricted Translation-en_AU [2,407 B]   
Hit http://ftp.iinet.net.au precise/restricted Translation-en                  
Hit http://ftp.iinet.net.au precise/universe Translation-en                    
Get:4 http://ftp.iinet.net.au precise-updates/main Translation-en_AU [4,434 B] 
Hit http://ftp.iinet.net.au precise-updates/main Translation-en                
Get:5 http://ftp.iinet.net.au precise-updates/multiverse Translation-en_AU [94.4 kB]
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://ftp.iinet.net.au precise-updates/multiverse Translation-en          
Get:6 http://ftp.iinet.net.au precise-updates/restricted Translation-en_AU [2,407 B]
Hit http://ftp.iinet.net.au precise-updates/restricted Translation-en          
Hit http://ftp.iinet.net.au precise-updates/universe Translation-en            
Hit http://ftp.iinet.net.au precise-security/main Translation-en               
Hit http://ftp.iinet.net.au precise-security/multiverse Translation-en         
Hit http://ftp.iinet.net.au precise-security/restricted Translation-en         
Hit http://ftp.iinet.net.au precise-security/universe Translation-en           
Hit http://ftp.iinet.net.au precise-backports/main Translation-en              
Hit http://ftp.iinet.net.au precise-backports/multiverse Translation-en        
Hit http://ftp.iinet.net.au precise-backports/restricted Translation-en        
Hit http://ftp.iinet.net.au precise-backports/universe Translation-en          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com intrepid/partner amd64 Packages               
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://archive.canonical.com intrepid/partner i386 Packages                
Ign http://archive.canonical.com intrepid/partner TranslationIndex    
Hit http://packages.medibuntu.org precise/non-free amd64 Packages     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://packages.medibuntu.org precise/non-free TranslationIndex   
Ign http://archive.canonical.com intrepid/partner Translation-en_AU   
Ign http://archive.canonical.com intrepid/partner Translation-en               
Ign http://ppa.launchpad.net precise/main Translation-en_AU                    
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://packages.medibuntu.org precise/free Translation-en_AU               
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_AU
Ign http://packages.medibuntu.org precise/non-free Translation-en
Fetched 202 kB in 20s (9,658 B/s)
Reading package lists... Done
root@liberator:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@liberator:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@liberator:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fgfs-base libproj0 linux-headers-3.2.0-30 mplayer-nogui libutouch-evemu1
  libutouch-geis1 libutouch-frame1 fgfs-scenery-base libapr1 libogdi3.2
  libcoin60 libpar2-0 libsvn1 libdap11 libgdal1-1.7.0 libpostproc-extra-51
  libgnome-desktop-2-17 fgfs-aircraft-base libepsilon0 libswscale-extra-0
  libxerces-c28 fgfs-models-base libopenthreads14 libhdf5-serial-1.8.4
  libgeos-c1 proj-data libfreexl1 hddtemp libspatialite3 proj-bin
  libutouch-grail1 libgeos-3.2.2 linux-headers-3.2.0-30-generic libhdf4-0-alt
  libaprutil1 simgear2.4.0 libopenscenegraph80 libdapclient3 libnetcdf6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@liberator:~# dpkg --configure -a
root@liberator:~# 


```

After running these commands, all the old kernels are still there.

I ran bootinfo again after all these commands, here is the url.

[http://paste.ubuntu.com/1541405/](http://paste.ubuntu.com/1541405/)


In the /boot folder are all the vmcoreinfo, confic, systen-map, abi, vmlinuz and intrd files.

---

### Post by oldfred on 2013-01-17
I particularly wanted the apt-get disk update after you deleted kernels just in case you accidentally deleted them all. That would reinstall the most current. All the others are just normal maintenance. 

You need to remove kernels.

And you need to edit partition types.

---

### Post by Col-1023 on 2013-01-17
By remove kernels do you mean to use nautilus to go into the /boot folder and manually delete the say 2.6.xxx vmlinuz.initrc, abi, etc files.

When I first removed the old kernels with synaptic, I used 'mark for removal" and not "mark for complete removal".

Since these kernels have dpeendencies, etc won't this cause probleems.?

When you say to change partition types, do you mean I should use gparted flag managment to untick the raid flags on the sda partitions?


I found it interesting that bootrepair put a boot flag on sdb and sdc, and this had no effect on the data on those drives, so maybe removing the raid flags from the sda partitions will have no effect on the data on them.

---

### Post by oldfred on 2013-01-17
Does synaptic still show anything? But yes you want to remove the entire kernel or complete removal.

Use Disk Utility just to change partition type, do not reformat.

this is now older, do not use tweak.

       HOWTO: Remove Older Kernels via GUI (or CLI) Tweak now obsolete
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
[http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/](http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/)

---

### Post by Col-1023 on 2013-01-17
synaptic shows that all the 2.6.xxx kernel-image file are completely gone, they don't show up at all for available packages.

As a test I used disk utility to change the partition type of the /boot partition to linux 83.

[http://paste.ubuntu.com/1543438/](http://paste.ubuntu.com/1543438/)

I checked with nautilus and the data seems ok.

---

### Post by sudodus on 2013-01-18
> **oldfred said:**
> Does synaptic still show anything? But yes you want to remove the entire kernel or complete removal.

Use Disk Utility just to change partition type, do not reformat.

this is now older, do not use tweak.

       HOWTO: Remove Older Kernels via GUI (or CLI) Tweak now obsolete
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
[http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/](http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/)

Please explain what you mean by [COLOR="Red"]Tweak now obsolete[/COLOR]! Is Ubuntu Tweak obsolete? For what versions? What's wrong with it?

Or do you mean something else?

---

### Post by Col-1023 on 2013-01-18
In synaptic the only traces of the 2.6 kernels is alot of linux-headers-2.6.31.xx files.
The tutorial link talks about linux-image files, not linux-headers.

Should I mark these linux-headers files for removal, or mark for complete removal?

If I mark these for "complete removal" with they take any dpendencies that the current kernel uses, I notices they all seem to use coreutils or something?

I've changed the partition type of /boot and /root partitions to linux 83 and that has worked fine with no corruption.

Thanks.

---

### Post by oldfred on 2013-01-18
I have never used tweak but someone posted it was not being updated. 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
 Download Now!0.8.3
* For Ubuntu 11.10 and before: old versions

---

### Post by Col-1023 on 2013-01-18
If I don't delete these linux-headers-2.6.31 files, is it still safe-ok to run the

sudo update-grub

command as suggest in the tutorial you linked to.

---

### Post by sudodus on 2013-01-18
> **oldfred said:**
> I have never used tweak but someone posted it was not being updated. 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
 Download Now!0.8.3
* For Ubuntu 11.10 and before: old versions
I have been installing and maintaining it according to the following link

[[COLOR="Red"]http://ubuntu-tweak.com/downloads/[/COLOR]]("http://ubuntu-tweak.com/downloads/")

'The easy way' from the ***tualatrix*** repo. My version (in 12.04) is 0.8.3, the same as in the link you posted (and it was released 2012-12-21).

---

### Post by oldfred on 2013-01-18
thank sudodus

I will update my notes to be correct. :)

You should be able to run this anytime. It will find all current installed kernels & update menu. Only if it does not report it finds anything then you need to download the most recent kernel before rebooting, but that would only happen if you deleted all your kernels.
sudo update-grub

---

### Post by Col-1023 on 2013-01-18
Thanks fred, Here is the terminal output.


david@liberator:~$ sudo update-grub
[sudo] password for david: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-2.6.32-42-generic
Found initrd image: /boot/initrd.img-2.6.32-42-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.28-17-generic
Found initrd image: /boot/initrd.img-2.6.28-17-generic
Found linux image: /boot/vmlinuz-2.6.27-11-generic
Found initrd image: /boot/initrd.img-2.6.27-11-generic
done
david@liberator:~$ 


Even though the linux-image-2.6.xx files don't appear in synaptic, they are still present in the /boot folder.

Here is the bootinfo url.


[http://paste.ubuntu.com/1546009/](http://paste.ubuntu.com/1546009/)

---

### Post by oldfred on 2013-01-18
If not in synaptic anymore, I would delete all the 2.6 based files.

       HOWTO: Remove Older Kernels via GUI (or CLI) 
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
[http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/](http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/)

It looks like you updated the partition types for sda1 & sda2 to 83, but sda4 & sda5 also should be corrected. sda5 is also 83 as it is /home but sda4 is swap so it should be 82.

---

### Post by Col-1023 on 2013-01-18
in synaptic the only kernel 2.6 files left are the linux-headers-2.6.31.xx files.

If I "mark for complete removal" will they take any dependencies that are used by the current kernel?

Should I use nautilus to go into the /boot folder and delete all kernel 2.6 related files, wheather vmlinuz, abi, initrd, etc?

Will I need to run nautilus as root, I think that is gksudo nautilus, but am not sure?

Thanks.

---

### Post by oldfred on 2013-01-18
I would try synaptic first.

Then if not removed you can use command line, but gksudo nautilus is probably easier. Just be careful in nautilus at root not to change anything else & close it as soon as done.

---

### Post by Col-1023 on 2013-01-18
I used gksudo nautilus and deleted all the linux 2.6.xx files in the /boot folder.

When I closed nautilus, terminal gave this.


david@liberator:~$ gksudo nautilus
Initializing nautilus-gdu extension
Shutting down nautilus-gdu extension

** (nautilus:30518): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

** (nautilus:30518): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

** (nautilus:30518): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

** (nautilus:30518): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist
david@liberator:~$

---

### Post by Col-1023 on 2013-01-18
I ran sudo update-grub, here is the output.

david@liberator:~$ sudo update-grub
[sudo] password for david: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
done
david@liberator:~$ 


Here is the bootinfo url.


[http://paste.ubuntu.com/1546273/](http://paste.ubuntu.com/1546273/)

---

### Post by oldfred on 2013-01-18
Optional. 
If you want you can also houseclean out the older versions -30 thru maybe -33? But keep -34 & -35 as the current.

Sometimes when running from a command line, you see warnings or minor errors that you do not see from gui. If it works I do not worry much, if it does not work then it may be a bug. Sometimes when gui launcher does not work, I use command line to look for errors.

You still can remove the RAID partition entries.

---

### Post by Col-1023 on 2013-01-19
Thanks very much Fred for your help.

I think it might be ok to reboot, but I'll wait until after the weekend when some things I'm doing with this pc have finished before I do that.

The only partitions with raid flags left are the /home and /swap partitions.

---

### Post by Col-1023 on 2013-01-21
The reboot FAILED, I got the error,

"minimal bash-like line editing is supported.....tec"
grub_


There was no blinking cursor, so pressing TAB had no effect.

My bootinfo should be the same as above, since I changed nothing before rebooting other than backing up some new data files.


The only thing i can think of is that in my /sda1 grub.cfg file it says to look  for vmlinuz and initrd files in root, ie /vmlinuz and /initrd, whereas aren't these files really in /boot?


Here is an example of what I mean from my above bootinfo file, this entry is for my latest 3.2.0.35 kernel in the /boot/grub.cfg file.

menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
	linux	/vmlinuz-3.2.0-35-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root f161f9cb-e2c7-4a05-9bb8-4f4b51025df1
	echo	'Loading Linux 3.2.0-35-generic ...'
	linux	/vmlinuz-3.2.0-35-generic root=UUID=1bc7dbda-9973-48d1-9c8e-21133aec5885 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-35-generic
}

Do You think I shoud just copy all these files straight into the /root folder, and if so how?

I'm thinking the system has put the kernel images etc in the /bootpartition, but is looking for them in the /root partition, as the uuid for the location that grub.cfg looks for the vmlinuz files is my /sda2 partition, my /root partition.

Currently my /root partition has only folders, there are no "files" in it.

---

### Post by oldfred on 2013-01-21
Your / (root) normally does not have many files. Often just the links to the current kernels that can be used to manually boot.

If just grub then it cannot find grub.cfg. Or grub in MBR is not correct. Boot-Repair should be able to fix it.

With a separate /boot, your set root and search lines should be the /boot partition and its UUID. And then the linux line should refer to the UUID of the install. Search overrides the set root command just in case the hard coded hd0,1 is not correct, but UUID should be correct.

---

### Post by Col-1023 on 2013-01-21
I was looking through the grub troubleshooting guide and found this section.



What to Look For
	

Where It Should Be (Default Installation)
	

Specific / General Search Example

grub.cfg
	

(hdX,Y)/boot/grub/ or /boot/grub/
	

ls (hdX,Y)/boot/grub/grub.cfg or ls /boot/grub/

vmlinuz
	

(hdX,Y)/ or /
	

ls (hdX,Y)/vmlinuz or ls /vmlinuz or ls /

linux-3.2.0-14*
	

(hdX,Y)/boot/ or /boot/
	

ls (hdX,Y)/boot/vmlinuz-3.2.0-14

initrd
	

(hdX,Y)/ or /
	

ls (hdX,Y)/ or ls /initrd

initrd.img-3.20-14
	

(hdX,Y)/ or /boot/
	

ls (hdX,Y)/boot/initrd.img-3.20-14 or ls (hdX,Y)/boot/



I don't have the vmlinuz and initrd files, these files have no numbers after them, and they must be in my /root partition.

It seems it's ok to have the vmlinuz and initrd files with numbers, ie initrd-3.2.0.35 in the /boot/ partition.

If this is my problem, them how do I go about creating these files.

Thanks.

---

### Post by Col-1023 on 2013-01-21
Thanks Fred.

I installed and ran the bootinfo program on the usb stick.

One difference is that the separate boot partition in advanced setting is not greyed out this time, so I can change it if I need to.

Here is the bootinfo url.


[http://paste.ubuntu.com/1555887/](http://paste.ubuntu.com/1555887/)

---

### Post by Col-1023 on 2013-01-21
I ran the recommended boot-repair, and will reboot to see what happens.

Here is the url boot-repair gave after it finished.


[http://paste.ubuntu.com/1555993/](http://paste.ubuntu.com/1555993/)

---

### Post by oldfred on 2013-01-21
Grub in the MBR now is booting from sda2 without separate /boot. While grub is now in sda2, you have no kernels in sda2 so you have nothing to boot.

If Boot-Repair will not let you add the separate /boot partition to install, you can manually do it.

       Separate /boot on sda1, / on sda2:
grub> set prefix=(hd0,1)/grub
grub> insmod linux
grub> set root=(hd0,2)
grub> linux (hd0,1)/vmlinuz-3.2.0-35-generic  root=/dev/sda2 ro
grub> initrd (hd0,1)/initrd.img-3.2.0-35-generic
grub> boot

    
Or manually reinstall from liveCD with separate /boot:
       #If separate /boot
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

    
Or you can use supergrub to boot and then reinstall from inside your install.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Then once booted:
       
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Col-1023 on 2013-01-21
Thanks alot Fred for your help with this.

After running boot-repair from the usb stick, it seems to have worked.

When I rebooted, there was a menue with very small writing which had the choices between my current kernel, my current kernel recovery mode and previous kernels, it showed for around 10s and then the system continued to boot, do a VERY LONG filesystem check and then i was able to login.

I'm using the system now, and everything seems to be working ok.


I think the important message for me out of this whole thing is that I need to use boot-repair from a usb stick, so I'll be keeping my little friend handy in case another problem like this happens.

---

### Post by Col-1023 on 2013-01-21
Updated the system, now uname -a says I'm running 3.2.0.36 #57, which is the latest kernel.

Again thanks very much Fred for all your help with this, I'm marking this thread is [SOLVED]

---

### Post by oldfred on 2013-01-21
Glad you have it working. 

I have always had several repair tools. I used to burn a set of CDs to have the latest versions of gparted, Supergrub, Knoppix, Parted Magic and maybe others. I now also have Boot-Repair and actually have multiple ISO on one flash drive that I can directly boot with grub's loopmount.

---

