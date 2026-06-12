---
title: "Ubuntu and Windows 10 sharing a data drive?  Server a better idea?"
date: 2020-09-23
forum: General Help
---

### Post by random turnip on 2020-09-23
I'm currently contemplating building a new PC.  It would primarily be for gaming, so I'm planning on having Windows 10 in one way or another.  My ideal scenario would be a dual boot system with Win10 and Ubuntu on an SSD and most of the larger bulk of data on a seperate HDD, my questions is how well would that work?  Do they share drives well?  Alternatively I will have an old desktop not doing much, would it be worth turning this into a server?  Though to be honest I'm not sure if that would really be worth it other than backing up.

I also wondered, is it worth having both Ubuntu and Win10 on seperate SSDs, or is this just throwing money away for no good reason?  My main reasoning behind this would be to keep it simple, so I can mess around with things on Ubuntu without risking killing my Win10 install because I'm paranoid and haven't been using Ubuntu too much for some time now.

---

### Post by HermanAB on 2020-09-23
A Raspberry Pi with a 1 TB USB memory stick makes a very nice server.

---

### Post by TheFu on 2020-09-23
When you are new to Linux, being paranoid is good.  People often make mistakes that accidentally wipe MS-Windows. Having 2 separate SSDs isn't needed and will add to confusion, unless you understand drives, partitions, and booting pretty well from the perspective of both OSes.

As always, anything you can't afford to lose should be backed up in a way that you 100% know how to restore and have tested the restore a few times.  If you can't/won't do this, use a different system or just run One of the OSes inside a virtual machine.  Any gaming computer will easily run virtual machines too.

I'm not a gamer, so I have Windows inside VMs on Linux hosts.  Running right now:
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 1     spam3                          running
 2     blog44-1604                    running
 3     zcs45-16.04                    running
 4     vpn09-1604                     running
 5     xen41-1604                     running
 6     regulus                        running
```
Oops, I don't have the Windows VM running. Give me a few seconds:
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 1     spam3                          running
 2     blog44-1604                    running
 3     zcs45-16.04                    running
 4     vpn09-1604                     running
 5     xen41-1604                     running
 6     regulus                        running
** 13    WinUlt                         running**
```

There - Windows is running now.

I use KVM as the hypervisor, which is the most stable, most flexible, and fastest hypervisor today. KVM is what IBM, Amazon, and all the biggest VPS providers use, except ... cough ... Microsoft and VMware.  Everyone else uses KVM.

KVM doesn't run on Windows hosts. Sorry.

---

### Post by TheFu on 2020-09-23
> **HermanAB said:**
> A Raspberry Pi with a 1 TB USB memory stick makes a very nice server.

Or any SSD in a USB3 enclosure. An **externally powered**, cheap, USB3 HDD is fine too. Avoid using USB-powered storage. Just be certain to get a r-pi v4 or later so USB3 and GigE networking have the bus throughput needed. 

Raspberry Pi v2 systems can't do amazing things provided no GUI is needed.  
My projector system plays media using a raspberry pi v3. 
The TV-room uses a r-pi v2 for the smaller screen and music from a central mpd server.
Not bad for 5V@2A systems.  A r-pi v4 is in a completely different class than the prior models. It is the first that I'd consider ready to be a backup server. They finally solved the bus limitations so true GigE and USB3 bandwidth can be used.  The main issue today in choose a r-pi v4 is that many Windows people think they need much more RAM than they do.  If you don't plan to use the r-pi as a desktop, 2G of RAM is absolutely fine.  Running nextcloud, email, calendaring, and a few other network servivces on the same device in addition to backups (just use different storage) can all be accomplished.  The 4G RAM and more models are too expensive for what they do. Better off using an old Chromebook which will have 50x the performance of these ARM systems. I didn't look up how much greater performance Intel provides, but it is a huge difference almost always.

For data backups, I suppose it depends on the amount of data that needs to be backed up daily.  I use a 2010 Core i5 system w/ GigE NICs, a USB3 "dock" and a 2TB HDD. This is only for non-media (no video or audio files) backups.  I treat photos the same as email, word processor and spreadsheet files. They get daily, automatic, versioned, backups.

---

### Post by Autodave on 2020-09-23
For what it is worth:

I have Win10 on one SSD and Xubuntu 20.04 on another SSD.  I then have a 1T spinner to keep data on: music, pics, docs, etc.  When I boot the machine, I use the command for which hard drive to use.  No grub to worry about, no worry of a Win10 update deleting my Xubuntu.  Both SSDs are 120G and can be had for less than $30 US.

---

### Post by mastablasta on 2020-09-23
> **random turnip said:**
> Do they share drives well? 
yes, but fastboot has to be off or any hibernation in windows should be avoided. use NTFS and you will need windows to protect the drive and do any fixes. other than that they work just fine. 

i have Openelec/Kodi on RPi with external NTFS drive.

i also have a few NTFS drives in main PC they still have winxp on it. no issues there. just keep in mind that any scans on drives should be done form windows and with windows tools.

---

### Post by HermanAB on 2020-09-24
As mentioned above, a problem with Win10 is that by default it doesn't shut down completely, it hibernates/suspends.  Therefore the filesystem on a shared drive may be in a weird state and then get messed up by Linux.  

You will have better performance and less hassle if you use a networked server.  Since a file server does mostly nothing, a small embedded computer such as a Raspberry Pi or a Beaglebone works pretty good as a SOHO server and costs very little.

---

### Post by SeijiSensei on 2020-09-24
> **HermanAB said:**
> You will have better performance and less hassle if you use a networked server.
I heartily endorse Herman's observation. I have a Linux server that exports some directories using both Samba and NFS. I can access the files from both Linux and Windows and don't have to worry about filesystem incompatibilities. All the files are stored on the server in ext4 filesystems.

---

### Post by BFG on 2020-10-13
> **random turnip said:**
> I'm paranoid
This is a good place to start. 

First, you're right that having your precious data on a PC you will use for productivity is always a weak position. Data servers exist to address this. 
Have a secondary backup of course, no matter what.

Second, USB is a toy. No serious data retention architecture ever used USB. Avoid it like the plague for anything you can't bear to lose. It's fine for secondary backups.  

> **random turnip said:**
> I'm currently contemplating building a new PC.  It would primarily be for gaming, so I'm planning on having Windows 10 in one way or another.  My ideal scenario would be a dual boot system with Win10 and Ubuntu on an SSD and most of the larger bulk of data on a seperate HDD, my questions is how well would that work?  Do they share drives well?  

Windows and Linux can access the same data on the same drive with absolutely no problems. We've been doing this (for business) since Ubuntu 9.04 and Windows XP, and right now Windows 10 and Ubuntu 20.04 and it's absolutely flawless. 

Same goes for using a separate data drive in the same PC. It'll work flawlessly, even if windows 10 goes into sleep mode.


> **random turnip said:**
> Alternatively I will have an old desktop not doing much, would it be worth turning this into a server?  Though to be honest I'm not sure if that would really be worth it other than backing up.
I'd invest in a NAS device, but maybe the desktop would work. Though servers usually use RAID and have more durable components. Add a UPS and a backup USB drive is always recommended, and this would go some way to de-risking an old desktop. The thing you'd lose is uptime during any recovery.   For extra paranoia get a cloud backup service too.

> **random turnip said:**
> I also wondered, is it worth having both Ubuntu and Win10 on seperate SSDs, or is this just throwing money away for no good reason? 
This is my preference.  And it's actually not that expensive as you can use smaller drives. Windows 10 needs 120Gb min for MS Office, you'd need more for gaming. Ubuntu will fit in a 20Gb partition so be fine for years on a 80Gb drive.

Make sure to use UEFI/GPT for both installs. 
Not essential, but makes life easier - Pull the cable from the 'other' drive. Install windows first. Power off, pull the cable from the windows drive, connect the other, install Ubuntu 20.04.
Connect both cables and reboot. Then use boot-repair from a liveUSB and it'll sort out grub perfectly for you.  The cable-pulling means no second guessing. Plenty of people will post that it's unnecessary, but sometimes you need a reason to make things absolutely idiot-proof (and in my case it allows me to delegate builds to temps) and it's no hardship.

You then have a system where if you want to make bold changes to either OS, it'll be very robust. You can even pull the other drive to be doubly sure.

If you dual-boot from the same drive, it's also very stable. But a useful tip is to partition your drive with odd sizes, as it makes them easier to identify. E.g. don't give windows and ubuntu both 200Gb boot drives.

---

### Post by ActionParsnip on 2020-10-13
You need to accommodate Windows short comings. A file server will remove any complication for you but if you want the drive local then both systems can read and write NTFS, so have the SSD for your OSes and then the larger drive partitioned and formatted to NTFS will allow file sharing between the OSes

---

### Post by TygerTung on 2020-10-13
Another option for a server instead of a raspberry pi, as they are quite expensive, is to get an old thin client from somewhere, as they can be had for almost nothing and turn that into a server. They are nice as they are completely solid state and don't use much power. I'm using one as a pi-hole server, but it is a bit overkill. The only issue I had is that the one I got had a very small solid state hard drive (1GB), so it was tricky to get  the OS small enough, but if you get one with a 4 or an 8 GB drive, you will find it much easier. I didn't want to spend any more money on another drive, so just used the little one.

---

### Post by mastablasta on 2020-10-14
they are not as cheap as they used to be but on the other hand they are more powerful now. still at 65 EUR for the starter kit - that is not much.

---

