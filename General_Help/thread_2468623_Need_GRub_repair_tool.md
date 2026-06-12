---
title: "Need GRub repair tool"
date: 2021-11-05
forum: General Help
---

### Post by jgwphd on 2021-11-05
I have a dual boot machine and my Grub wasn't booting into Ubuntu. After creating an external USB drive with Ubuntu 21.10 running, my troubles started with a lot of weird booting problems, sometimes my machine a Dell XPS desktop would boot and hang going to windows (circulating dots frozen) other times it would boot and hang going to Ubuntu (circulating symbol frozen).The symptoms kept changing until I replaced the cmos battery... now I can boot reliably if grub is pointing to the right spot. There is no boot-repair for 21.10 that I can find .... so I used "Grub Customizer" and found Grub had Ubuntu pointing into "sdb" and change it to point into "nvmeon1p7". Windows is on P1 and Ubuntu on P7 on that SSD. After the changes I now I can boot into Ubuntu but not windows. I did sudo update-grub. I can now get to windows and ubuntu but there are a lot of dead entries and duplicates. I have two dead ubuntu entries and two duplicate windows entries. Does anyone know where there is a tool that I can run to get things straightened out. Many Thanks!

---

### Post by oldfred on 2021-11-05
There is not really a grub repair tool. You just reinstall grub.
A full reinstall of grub will replace all changes you made with grub-customizer as it replaces most of grub with its own "proxy" files.

Do not run any suggested repair until someone has reviewed the report.

Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jgwphd on 2021-11-05
Hi oldfred, as I mentioned in my initial post. There is no boot-repair for 21.10 that I can find .... so I used "Grub Customizer" At the first link you supplied, I tried again to get to a version of Boot-Repair for 21.10 and I got following (BTW, the second link you provided points back to the first link): 

jgw@jgw-XPS-8930:~/Desktop$ sudo add-apt-repository ppa:yannubuntu/boot-repair
[sudo] password for jgw: 
Repository: 'deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) impish main'
Description:
Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Found existing deb entry in /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-impish.list
Adding deb entry to /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-impish.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-impish.list
Adding key to /etc/apt/trusted.gpg.d/yannubuntu-ubuntu-boot-repair.gpg with fingerprint 3C48D16124B50277AF10D27F32B18A1260D8DA0B
Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish InRelease                                                     
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hirsute InRelease                        
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates InRelease
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-backports InRelease
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-security InRelease
Hit:7 [http://ppa.launchpad.net/unit193/encryption/ubuntu](http://ppa.launchpad.net/unit193/encryption/ubuntu) hirsute InRelease
Ign:8 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) impish InRelease
Err:9 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) impish Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu impish Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
jgw@jgw-XPS-8930:~/Desktop$ sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates InRelease                                                                  
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-backports InRelease                                                                
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hirsute InRelease                                  
Hit:5 [http://ppa.launchpad.net/unit193/encryption/ubuntu](http://ppa.launchpad.net/unit193/encryption/ubuntu) hirsute InRelease
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                   
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-security InRelease                            
Ign:8 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) impish InRelease
Err:9 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) impish Release
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu impish Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
jgw@jgw-XPS-8930:~/Desktop$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package boot-repair
jgw@jgw-XPS-8930:~/Desktop$

Advise please. What next. Thanks1

---

### Post by oldfred on 2021-11-05
Your hit 3, then 4 is showing hirsute, but everything else is impish. 
You need to have all as impish.
sudo nano /etc/apt/sources.list


I did not realize Boot-Repair did not yet have a 21.10 version.
I normally suggest ppa as that often is slightly newer than the ISO.
But you can download the ISO which is a Lubuntu based bootable system.

LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
But you can download the Boot-Repair ISO and create a bootable version.
[https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

---

### Post by jgwphd on 2021-11-06
Hi Oldfred, I used "Iso2Usb" tool that I downloaded to windows to create a bootable "boot-repair" USB drive with my windows system. I then booted my machine with the newly created "boot-repair" USB drive.  Boot-repair updated itself to the latest boot-repair software!** I DID NOT FIX ANYTHING on my machine. **Next, I clicked on "Create a Bootinfo Summary" which resulted in a report at 

[https://pastebin.ubuntu.com/p/bB3b2sd4ZM/](https://pastebin.ubuntu.com/p/bB3b2sd4ZM/) 

You simply click on login and it takes you directly to the report! What next?

BTW, You mentioned and I got rid of hit 3 ([http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hirsute) in my Software and Updates by removing it (I just got rid of it by clicking on "remove" in the "Other Software" screen). Hit 4 was for some encryption stuff which seemed removed from my problem. So I left it so I could look at it more and remove it later. I am not sure why this would have any impact on my boot issue?

---

### Post by oldfred on 2021-11-06
I do not know zfs, and you have a nvme0n1p7/etc/grub.d/11_linux_zfs Grub script.
Do not know if from grub-customizer or where? I do not see any zfs partitions.

I do not see anything else.
I then suggest a total re-install of grub using advanced mode and check install latest kernel.

I see you mounted a data partition using UUID with UUID as mount point. 
I prefer to mount by label, and create my own mount point with a more useful description.
Is sda an internal or external drive?

---

### Post by jgwphd on 2021-11-06
I was creating an Ubuntu 21.10 system on a USB drive that I could plug into any computer then boot and run Ubuntu 21.10 from the USB drive in the future, when this all started. Apparently I had a hardware problem with the cmos battery causing me issues (unknown and not apparent at the time - I am guessing). After numerous (intermittent successful) reboots and I finally figured out I had a battery issue. Once I replaced the battery, I could get things to boot reliably when pointing to the right partition. What I wound up with is what you see in the boot-repair report. Rather than make things worse I decided to post to the forum and see if anyone had a "quick fix" for my grub issues. So,
 
1) I have no idea what "zfs" is?  ...looks like something new in Ubuntu ( [https://ubuntu.com/blog/zfs-focus-on-ubuntu-20-04-lts-whats-new](https://ubuntu.com/blog/zfs-focus-on-ubuntu-20-04-lts-whats-new) ) or maybe part of Grub ...[https://unix.stackexchange.com/questions/447960/how-to-create-a-zfs-zpool-that-grub-can-read](https://unix.stackexchange.com/questions/447960/how-to-create-a-zfs-zpool-that-grub-can-read) 
2) sda is an internal hard drive 1TB
3) nvme0n1 is a 256GB SSD (internal drive) 

History: Machine came with an 256 GB SSD with windows on it and internal 1TB HD. I made some space on the SSD and dual booted Ubuntu

I am new playing around with grub and boot so please be specific in your suggestions. I "assume" you want me to boot "boot-repair" go into advanced mode and check "install latest kernel". And let boot-repair do its thing! Is that true? ...and will boot-repair find the windows partition(s) and repair the duplicate windows manager lines in grub and straighten out the dead grub ubuntu entries  etc. Many thanks for your continued assistance.   :-)

---

### Post by oldfred on 2021-11-06
Reinstall of grub will not clean up UEFI boot entries.
You typically have two in UEFI, one for shimx64.efi and one for grubx64.efi.
Boot-repair will not fix Windows issues, it typically just updates grub menu or re-installs grub as those are most boot issues before grub menu.
appears.
Other boot issues then are after grub and often a driver issue, UUID issue or some configuration issue. 

If installing grub to any second or external drive see this now very old bug. Multiple work arounds posted. You must gpt partition in advance.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by jgwphd on 2021-11-07
Bug 1396379 is exactly what I got and my initial symptom was my boot set-up was "replaced with grub configuration that can **only boot with the USB inserted**". There seems to be resistance to fixing the bug because it is called "inconvenient", WoW!. But this is really annoying and anything that leaves your machine unbotable is a bit more than inconvenient. I was simply trying to build an external (on a USB drive) Ubuntu system that I can use to boot other systems in Ubuntu without changing those systems. The result is I have a severely crippled machine where I created the USB drive - I am glad it was my machine and not a friends while telling them how wonderful Ubuntu is  :-) . So if I further screw around with all this, I may lobotomize my system. Since I have it working fine once booted in windows or Ubuntu (allbeit with a messy Grub menu) I'll just consider my self lucky that my system boots at all and leave the system alone until Ubuntu 22.04 shows up then I'll clear out everything and l reinstall windows and Ubuntu again. This seems the safest and easiest way to go, unless there is something that will cause me further problems that I haven't discovered yet. Is there?  Thanks again for all your assistance!!

---

### Post by oldfred on 2021-11-07
Once we found work arounds for the bug, I have had no issues installing to sdb or external drives. 
I want to keep normal boot of my current LTS version and then from that boot any other install on sdb. And I want flash drive to be bootable on its own, so always partition in advance with an ESP and install/reinstall grub to it.

Grub installs to any drive. I experimented with several other installs just to see how grub works. They all installed to the drive I selected during install. Its just Ubuntu's Ubiquity installer.

With 22.04 LTS they are planning a new installer to replace Ubiquity. I hope to be able to test that and see if they fix the issue in a new installer.

---

### Post by jgwphd on 2021-11-07
Many thanks for your assistance. The problem with "a work around" is that you have to get **bitten** by the bug first before you realize you need a work around and go looking for one. One that leaves you with a un-bootable system is a pretty hard lesson for the first **bite** :-)   In any case, the main reason for asking the forum for help was to understand what I did wrong so I don't do it again. Now I know what the story is and I have a workaround. Best Regards  John

---

