---
title: "Partition and disk usage advice for new installation"
date: 2023-08-30
forum: General Help
---

### Post by benawhile on 2023-08-30
I have a self built system (see below) running Linux Mint Cinnamon successfully since 2019 except that it has been subject to random freezes, shutting down about once per day and requiring the Alt + SysRq REISUB restart.
 
 I would like some guidance about upgrading with the latest Ubuntu version. My usage is general plus a lot of music programs and storage.
 
 Since initial setup I installed the internal HDD below. What is the best way to incorporate it in the system? I have read a suggestion that the swap partition should be on HDD.  
 Existing 2 x 8G RAM x 1.5 would mean 24G for a swap, which I would like to be used for hibernation.
 
 The current installation has a swap file of 1.7G installed in the file system by default.  
 
 If I set up a swap partition, how do I make sure that the new install recognises it?
 
 I understand it is better to install the OS on SSD and use the HDD for data storage.
 
 What file system is best for the HDD storage?  NTFS, Ext4 or FAT?  
 
 The external HDD I currently use for back up is NTFS and I have used NTFS for a shared windows/linux data partition previously, though there may have been limitations I was unaware of.
 I might be networking the Linux desktop with a windows laptop.  
 
 Intended partitions
 HDD :
 swap partition
 Remainder to be split into two partitions, one for a second user
 
 SSD:
 Boot efi
 OS 40GB
 Home folder ?size?
 Alternative OS 40GB

---

### Post by oldfred on 2023-08-30
Moved to Mint sub-forum since not Ubuntu or offical flavor of Ubuntu.

I do not suggest hibernation, if you have SSD, it will probably boot just as fast as recovery from hibernation. And if hibernation on HDD, boot from SSD will be faster. Swap never needs to be larger than RAM. Old rule of 1.5X of RAM was back when RAM was a lot smaller.
Now default is 2GB as swap file. But many suggest a swap partition of just over 4GB. Best on SSD, but with that much RAM, you should not use swap at all. 
How much data? Often best to have everything on SSD and use HDD for backup. Otherwise you need another drive, flash drives, or Internet for backup.

I do multiple installs & have installs on every drive & every larger flash drive. Most are tests or minimal with some repair tools for emergency boot. So I keep /home inside / as it is tiny and have all my data in data partition(s).
Unless you have Windows to make repairs to NTFS partitions, do not use NTFS. It does not support Linux ownership nor permissions and will need chkdsk & defrag that you can only run from Windows. 

Only use gpt partitioning. Ubuntu uses ext4 as standard, not sure about Mint. Some like to experiment with other formats.

---

### Post by benawhile on 2023-08-30
Thanks Fred but it is a Ubuntu question, I want to install Ubuntu and change back from Mint

---

### Post by oldfred on 2023-08-30
Moved back to General Help, since OP installing Ubuntu.

---

### Post by grahammechanical on 2023-08-31
> Home folder ?size?

With Ubuntu the home folder is in the root partition of the OS. Its path is /home/username/.
    Linux Mint must surely follow the same way of doing things. It is the Linux way. Having 40 GB for the OS is fine if you intend to store most of your files and documents on another partition/drive. I do not think that 40 GB will be big enough for two user home partitions.

Some of us create a separate partition for data (Ext4). Files that you want to share with Windows can be put on an NTFS partition. But native Linux file types are better on an Ext4 partition. I do not think it is wise to use a NTFS partition for storage of Linux files unless they are for sharing with Windows.

I have no practical experience of sharing files with MS Windows. I learn from reading advice given on this forum. Remember, use Windows tools to manage Windows file systems and Linux tools to manage Linux files systems.

Regards

---

### Post by Tikhon03 on 2023-08-31
A long time ago, I posted a question on the ubuntu forums about partitioning with multi-boot setups. Someone responded with a link to this article by Carla Schroder [https://www.linuxtoday.com/infrastru...-boot-setup-2/](https://www.linuxtoday.com/infrastru...-boot-setup-2/). I wasn't able to find a link to the full article just now, so I will recount the steps. The idea is that you have one big partition for all of your data. When you mount that partition you do not mount it as home, because, there are many system specific settings that can be put in home. So if you wanted to dual boot ubuntu and mint or ubtuntu and something else, they are not in conflict with each other. Also if you have to reinstall the operating system, you never have to worry about copying your data or accidentally overwriting your data, your data is just waiting for you. It was some of the best advice I ever got, and I have been using this strategy ever since.


My partition structure goes like this


256 MB EFI partition
128 GB root for linux distro 1 (format: ext4)
128 GB root for linux distro 2 (format: ext4)
swap (following the guidelines previously mentioned by oldfred)
mydata remaining space, or separate drive (format: ext4)


you could also have a separate backup drive for that matter, but the EFI and root partitions should definitely be on an SSD in my opinion. Why 128GB for root? I have a lot of programs and libraries, so my ubuntu partition has over 50GB right now and my arch linux partition has even more. That may be overkill for some people. Just look at how much space you already are using except for the contents of your folders. But you should include the hidden folders of home.


During the graphical installation you set one of the root partitions to mount as /, and you set swap to swap. For safety, I do not mount the partition with my data during the install process.
Once the system is installed, and booted for the first time, I create a new folder and mount the partition with my data.
```

mkdir mydata

```
I determine the correct partition to mount by the fact that it is the biggest
```

sudo lsblk

```
It could be something like sda5 or nvme0n1p5 I then mount it.
```

sudo mount /dev/nvme0n2p5 /home/username/mydata

```
Next, as root, I have to grant myself ownership of my own data. For most linux distros I have seen, the correct command for this is
```

sudo chown -R usernam:username /home/username/mydata

```
The only exception that I know of is opensuse. Finally, to make it persistent on boot, a line needs to be added to the fstab file. So, first it is necessary to look up the UUID
```

/dev/nvme0n1p5: UUID="..."

```
Carla gave instructions for launching a graphical editor with sudo, using dbus-launch, but things have changed since then. You can still copy and paste into a command line editor though. Highlight the UUID (without quotes) in the terminal window and select copy with your mouse. After it is copied,
then open the fstab file with sudo:
```

sudo nano /etc/fstab

```
Paste the UUID on a new line with your mouse, then complete the line as follows
```

UUID=...      /home/username/mydata      ext4    user,defaults      0     1

```
Save it by Ctrl+O, and close by Ctrl+X. After rebooting, the partition should now be mounted automatically.


I have my own folders for Downloads and Documents on the partition mounted to mydata. However, Downloads will not go there automatically unless you go into your browser settings. You can also go into the settings of libreoffice and other programs to set the default folder for user files.

---

### Post by guiverc on 2023-08-31
> **benawhile said:**
> I have a self built system (see below) running Linux Mint Cinnamon successfully since 2019 except that it has been subject to random freezes, shutting down about once per day and requiring the Alt + SysRq REISUB restart.
 

I'm late to the party sorry, but I didn't note any mention of the *freezes*.

Maybe as a consequence of me using mostly old hardware, any random *freezes* are something I always explore, ie. why?   If you ignore the warning signs (*it maybe you thinking Linux Mint is at fault, but maybe its not!*), you risk that problem continuing and/or getting worse (*which is the norm*).

- I'd check PSU or power supply; is it providing correct voltages (*this maybe easy if you've got and are somewhat familiar with multimeter usage, but even good components will behave poorly if fed bad power*)

- I'd do RAM tests (fully cycle; cache disabled if you can); easy to do, just takes time, let these run overnight etc

- check motherboard for dust etc preventing good airflow for heat escape purposes, and most importantly perform a 'cap check' (ie. look for any swollen capacitors - these show as a frozen system, and issue will worsen over time)

However you do mention restarting using REISUB; *freezes* due to hardware are usually permanent (ie. system halts), thus REISUB won't do anything, so if you're always able to REISUB the hardware check is less important, but it's something I do on most unexpected problems actually (*but I use old hardware often*).

---

### Post by benawhile on 2023-09-01
> **grahammechanical said:**
> With Ubuntu the home folder is in the root partition of the OS. Its path is /home/username/.
    Linux Mint must surely follow the same way of doing things. It is the Linux way. Having 40 GB for the OS is fine if you intend to store most of your files and documents on another partition/drive. I do not think that 40 GB will be big enough for two user home partitions.

Thank you. Currently I have a large separate partition for home, although as you surmise correctly it was not the default when I installed. I intend use the 1TB HDD for storage.

---

### Post by benawhile on 2023-09-01
> **guiverc said:**
> I so if you're always able to REISUB the hardware check is less important, .

Thanks for that tip!

---

### Post by benawhile on 2023-09-01
Thikon03
Thank you. I will revise my plan.
I will still have two separate partitions,one for an alternative OS, but will allocate 80GB and using the default installation the home folder will be in the same partition. So any alternative instllation wil also have room for its own home folder. The data will go on the internal HDD. I periodically backup on to an external HDD. Fortunately I have never had to use this in 20 years. But I will do a preinstall backup and hopefully mount the HDD during the install.

I envisage some kind of tech problem with a quick access shortcut to the HDD stored data. This arose before when I had separate data partition and I needed to use symlinks. Having said that, at that time I had a dual boot and the data partition was shared with windows using NTFS, and it seemed to work well for my simple requirements. But this time I will use FAT.

Well here goes, if it all goes base over apex I will get back via the laptop. My eyes are getting bad and laptops are a pain now. Waiting for cataract operation.

---

### Post by oldfred on 2023-09-01
Do not use FAT32.
It is really only for smaller partitions. It has no journal like NTFS or ext4. And FAT32 cannot store any file over 4GB. Years ago I was backing up an image to FAT32 and did not fully understand why as I had more data, the image was never over 4GB. Fortunately I did not ever need that backup.
I now prefer backups that store files in a way I can access each file if needed.

When I used XP years ago I had both NTFS & ext4 data partitions. Now just ext4 with multiple Ubuntu installs.
Mount to /d - TheFu
[https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243](https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243)
Similar discussions:
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by benawhile on 2023-09-02
OK thanks. What is the importance of a journal? My current installation program is only offering ext 2,3,4, FAT 16,32, I had read that exfat was better but surprisingly it's not offered. Nor is NTFS.
Presumably with recent ubuntu I won't be ablt to reformat drives with ntfs exfat after install either? 
But will the new install read and write to my backup external HDD, which is ntfs?
My current use doesn't involve anything like 4GB file size.
For now I can use Ext4 throughout

---

### Post by oldfred on 2023-09-02
You only have the choice of Linux formats for the install. Your / (root) and other system partitions, if separate partitions must be Linux format.
FAT32 is also offered for the ESP - efi system partition which is required for UEFI boot.
NTFS driver is normally included with the install.
But I think you have to add an exFAT driver after install.

But if you use Windows formats like NTFS, you must have Windows or at least a Windows repair flash drive. NTFS requires chkdsk & defrag that you only can run from Windows.

---

### Post by benawhile on 2023-09-02
Nearly ready to install, last step is the storage HDD. I have partitioned it with a swap partition and ext partition for storage but what should I do about a mount point? the options in the install program are /  /boot, /home (already used) /tmp /usr usr/local etcetera

---

### Post by oldfred on 2023-09-02
Only the normal system partitions are available during install.
You create mount point, mount drive & set ownership & permissions after install for any data partitions.
If NTFS which does not support ownership & permissions, the mount either in fstab or manually determine default permissions. Ownership is root.

---

### Post by benawhile on 2023-09-02
New system up and running, a few issues but they can go in another post, I have the essentials and it looks good. Definitely a little slower, old Linux Mint Cinnamon system was 24 sec from boot to desktop and this is 35s, but that old system was 4 years ago and an update to current release might have been just as slow. I have an extra partition now to try out that theory. Many thanks for your advice.

---

### Post by benawhile on 2023-09-02
That extra 10 sec is in system load time. Login screen to desktop is still only 4 sec

---

### Post by oldfred on 2023-09-02
Some settings to review on Slow Boot. May or may not apply.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

Are you fully booting from SSD?

New NVMe drive in my 2016 build.
[FONT=monospace]```
[COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.781s (kernel) + 5.812s (userspace) = 10.594s  
graphical.target reached after 5.806s in userspace 
[COLOR=#54ff54]**
```**[/COLOR]

[/FONT]

---

### Post by benawhile on 2023-09-02
This is what I have on the SSD. The swap is on the HDD, it is shown as active. I realise not all perfect yet. For example OS can see the HDD in "Disks" and I can see it in "Files" but can't write to it, even though it shows as mounted.
```
ben@ben-B450-AORUS-M:~$ lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME FSTYPE   SIZE FSUSED LABEL PARTLABEL MOUNTPOINT UUID                                 PARTUUID
sda         232.9G                                                                        
&#9500;&#9472;sda1
&#9474;               1M                                                                        e6d8c113-c9f2-4d2f-a884-c361cf445550
&#9500;&#9472;sda2
&#9474;    vfat     977M   6.1M                 /boot/efi  CBAA-01DA                            74183706-6d06-4160-9983-8568582f96de
&#9500;&#9472;sda3
&#9474;    ext4    37.3G   2.6G                 /home      8f9dc558-e5b2-4bd9-8f6a-1e779601ed33 e411ffe9-87c3-4974-ae4c-e449cd830fd3
&#9500;&#9472;sda4
&#9474;    ext4    55.9G  11.5G                 /          f23334cd-afd7-4113-bbc8-8391d4b198a5 476f4d99-3996-4dbf-9962-ea812577e01b
&#9500;&#9472;sda5
&#9474;            55.9G                                                                        fd80b6b6-9ba0-4e5c-af1f-373b171973c0
&#9492;&#9472;sda6
     vfat    55.9G                                   CBA6-1E41                            20500568-e0a9-435f-aacd-133d44758875
sdb         931.5G                                                                        
&#9500;&#9472;sdb1
&#9474;    swap    23.4G                        [SWAP]     73a571c1-2685-4fe8-b57e-3415d7a39a90 15bb67b3-8448-4d6b-afc2-441420d8484f
&#9500;&#9472;sdb2
&#9474;    ext4   372.5G                                   1e6fca0e-41f4-421d-b27c-2a906ca89c4d 84bfd689-a369-405c-aa78-395e291968cb
&#9492;&#9472;sdb3
     ext4   372.5G                                   d122247d-6473-46be-b3d1-d5abf1dd91e8 ac9e7930-51b7-4641-8809-3344fed5148a

```

---

### Post by oldfred on 2023-09-02
Please do not post screen shots in line, just attach them. Not everyone has high speed Internet and it can bog their system down.
Better to post this in code tags (# in Forum's Go Advanced editor):
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

you do not need both bios_grub used for BIOS boot on gpt drives and the ESP - efi system partition. 
(I did add both when first converting from BIOS to UEFI, but now only have ESP)

---

### Post by benawhile on 2023-09-04
Thanks for your help so far. Hope I rectified the in line images OK

On previous Linux Mint Cinnamon installs, I used to get an option to boot previous kernels, even then overall load time was faster. I don't see that now, just the motherboard logo until login screen. Is that because there aren't yet any older kernels as it's a new system? Eventually I will need low latency kernel.
Haven't had any freezes>crashes yet at least!

```
ben@ben-B450-AORUS-M:~$ systemd-analyze
Startup finished in 8.190s (firmware) + 2.673s (loader) + 3.145s (kernel) + 7.349s (userspace) = 21.358s 
graphical.target reached after 7.343s in userspace

```
```
graphical.target @7.343s
&#9492;&#9472;multi-user.target @7.343s
  &#9492;&#9472;kerneloops.service @7.332s +10ms
    &#9492;&#9472;network-online.target @7.314s
      &#9492;&#9472;NetworkManager-wait-online.service @3.300s +4.013s
        &#9492;&#9472;NetworkManager.service @3.172s +126ms
          &#9492;&#9472;dbus.service @3.170s
            &#9492;&#9472;basic.target @3.159s
              &#9492;&#9472;sockets.target @3.159s
                &#9492;&#9472;cups.socket @3.450s
                  &#9492;&#9472;sysinit.target @3.127s
                    &#9492;&#9472;snapd.apparmor.service @1.049s +234ms
                      &#9492;&#9472;apparmor.service @870ms +117ms
                        &#9492;&#9472;local-fs.target @852ms
                          &#9492;&#9472;run-snapd-ns-snapd\x2ddesktop\x2dintegration.mnt.mount @4.847s
                            &#9492;&#9472;run-snapd-ns.mount @4.683s
                              &#9492;&#9472;swap.target @1.066s
                                &#9492;&#9472;dev-disk-by\x2duuid-73a571c1\x2d2685\x2d4fe8\x2db57e\x2d3415d7a39a90.swap @1.031s +27ms
                                  &#9492;&#9472;dev-disk-by\x2duuid-73a571c1\x2d2685\x2d4fe8\x2db57e\x2d3415d7a39a90.device @1.015s

```
```
19.267s apt-daily.service
 5.760s fstrim.service
 4.426s apt-daily-upgrade.service
 4.013s NetworkManager-wait-online.service
 2.937s plymouth-quit-wait.service
 1.928s modprobe@chromeos_pstore.service
 1.152s snapd.service
  587ms dev-loop3.device
  587ms dev-loop6.device
  577ms dev-loop5.device
  575ms dev-loop7.device
  572ms dev-loop2.device
  571ms dev-loop0.device
  570ms dev-loop4.device
  499ms networkd-dispatcher.service
  485ms dev-loop1.device
  410ms logrotate.service
  388ms dev-sda4.device
  377ms udisks2.service
  329ms e2scrub_reap.service
  265ms dev-loop15.device
  234ms snapd.apparmor.service
  214ms dev-loop14.device
  206ms systemd-logind.service
  193ms accounts-daemon.service
  190ms ModemManager.service
  187ms ua-timer.service
  179ms user@1000.service
  179ms snapd.seeded.service
  172ms systemd-modules-load.service
  172ms dev-loop8.device
  169ms dev-loop9.device
  165ms dev-loop11.device
  164ms power-profiles-daemon.service
  160ms dev-loop13.device
  158ms dev-loop12.device
  157ms dev-loop10.device
  151ms systemd-resolved.service
  148ms cups.service
  141ms systemd-journald.service
  135ms systemd-timesyncd.service

```
I followed those links.
I see I have the apt-daily.service issue but otherwise I don't have the knowledge to interpret any of this, but with some guidance I am willing to have a go at removing snap, updating UEFI, disabling secure boot, splash vs plymouth turn off network manager if any of that is indicated.

---

