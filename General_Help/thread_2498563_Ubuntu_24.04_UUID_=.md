---
title: "Ubuntu 24.04 UUID =/"
date: 2024-06-19
forum: General Help
---

### Post by userubu64 on 2024-06-19
Hello everyone, I bought a new Asus Vivobook E1504GA. I downloaded the Ubuntu 24.04 distribution onto a flash drive, cleaned the disk through the installer and installed Ubuntu. When I try to start my laptop, I get into the BusyBox shell. How can I fix this? The commands don't work in the shell. I can boot into Live mode from a flash drive




[img]https://gekkk.co/storage/v/ac797349cfe73f8c302b3e8015a3da8f.jpeg[/img]


I would like to add that I used Boot Repair to restore the boot, but it did not give the desired result. I received a message that 
> "Locked-NVram detected. Please do not forget to make your UEFI (fimware boot on the Ubuntu 24.04 LTS entry (sdb1/efi/ubuntu/grubx64.efi file)!"
Before running Boot Repair I got this:
[https://paste.ubuntu.com/p/m2rszdY9RB/](https://paste.ubuntu.com/p/m2rszdY9RB/)
After launching, I received this link:
[https://paste.ubuntu.com/p/2HSJn5MM59/](https://paste.ubuntu.com/p/2HSJn5MM59/)
But my problem still wasn't solved.




I'm really tired of messing around with this, so I'm asking for help. If this is necessary, I am ready to reinstall the OS according to your manual

---

### Post by grahammechanical on 2024-06-19
BusyBox is a small form of embedded Linux. It has its own set of commands. Being dropped to a BusyBox shell usually means that something is seriously broken with the installation.

UUID = Universally Unique Identifier. That long number represents either the drive (storage) or a partition on the drive. It could indicate that the partition that Ubuntu was installed in no longer exists.

An install of Ubuntu should have a minimum of two partitions. A EFI System partition formatted as FAT32. That would contain the Linux (Grub) bootloader files. And a Ubuntu partition.

You could try loading the Ubuntu Try session and running the Disks utility and reporting what partitions that utility will show you. The disks utility will also show the UUID number for each partition. That should help identify which partition is being referred two.

It might be simpler to just re-install Ubuntu 24.04 LTS

Regards

---

### Post by userubu64 on 2024-06-19
Now I will reinstall Ubuntu, partition the disk manually during installation and post the results. I tried this, unfortunately it doesn't help me. The UUID is the same as the disk UUID.

---

### Post by userubu64 on 2024-06-19
Now my disk contained 2 partitions: efi in fat32 (sdb1) and a partition with the OS in Ext4 (sdb2)

sdb                                                                                                              
&#9500;&#9472;sdb1 vfat     4B8D-B21B                            41c2445f-cbf1-4867-a37a-208968222ab1                        
&#9492;&#9472;sdb2 ext4     734487d2-5cfa-479e-900c-8af8ecf3ff2f 86cd840b-b35f-422f-a4a2-c8903cf691d1

---

### Post by userubu64 on 2024-06-19
[IMG]https://gekkk.co/i/6dbb2c61ea05f38ee5047129bcd8105b[/IMG]Here are the images from Gparted

[img]https://gekkk.co/storage/v/52e620b409fffd8dde113e3da9820dd2.jpeg[/img]
[img] https://gekkk.co/storage/v/afc9997c397849986f5ffd5bfc8e993b.jpeg[/img]
[img] https://gekkk.co/storage/v/9c52041840ce91ba0161adba7de412e1.jpeg[/img]
[IMG]https://gekkk.co/i/6dbb2c61ea05f38ee5047129bcd8105b[/IMG][IMG]https://gekkk.co/i/6dbb2c61ea05f38ee5047129bcd8105b[/IMG]

---

### Post by oldfred on 2024-06-19
As with many systems, your  UEFI promotes flash drive to hd0 or sda.
But when flash drive removed your internal drive becomes hd0.
Entry in sdb's ESP shows hd1,gpt2.
I bet if you change to hd0 it will work.

Ignore modprobe error.
Its trying to mount efivars in wrong place.
If chrooting again add this line.
mount -t efivarfs efivarfs /sys/firmware/efi/efivars
mount shows:
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)

---

### Post by userubu64 on 2024-06-19
How can I change the drive letter? O:)

---

### Post by deadflowr on 2024-06-19
If you're lucky you can re-order the devices in the BIOS/UEFI.

---

### Post by userubu64 on 2024-06-19
My BIOS does not have such a function. I can only disable or enable the disk and change the boot order of the devices.
I can't do this by booting through a USB flash drive?
mknod /dev/sda b 8 16; mknod /dev/sdb b 8 0
Can't help me?

---

### Post by oldfred on 2024-06-19
Its not the drive like sda once booted. It is the enumeration of the drive by UEFI/BIOS which grub has to use as drives are not yet mounted. Or hd0 or hd1.

From live installer you should be able to manually mount the ESP and edit grub.

You may be able to manually boot.
Can you get grub menu by pressing escape key just after UEFI/BIOS screen? Can be quick, so sometimes have to try again. And if UEFI fast boot on, it will be too quick. Do full power shutdown & "cold" boot to get UEFI/BIOS to rescan system and give just enought time to press escape key.
Then can you boot recovery mode?
Or manually edit grub entry with e key.

---

### Post by userubu64 on 2024-06-19
> Can you get grub menu by pressing escape key just after UEFI/BIOS screen? 
Yes I can do this
> And if UEFI fast boot on, it will be too quick.
Fast boot is disabled in uefi
> Do full power shutdown & "cold" boot to get UEFI/BIOS to rescan system and give just enought time to press escape key.
I waited 2 hours and tried to download again using the boot menu (escape). It did not help
> Then can you boot recovery mode?
Yes, I can boot into recovery mode, but this also does not give any results, I fall into the busibox shell again with the same error
> [COLOR=#000000]Or manually edit grub entry with e key.[/COLOR]
If you don't mind, could you tell me how I can do this? Based on your advice earlier, I have already changed some parameters grub.cfg. Therefore, now during startup, when I press the e button, I see that there are hd0 and ahchi0 everywhere. I can also attach a photo of my changes.Maybe this is a stupid question, but should I have changed gpt2 to gpt1?)
I want to clarify that I changed exactly grub.cfg which is located in the sbd2 section
Made changes using **sudo nano**

---

### Post by oldfred on 2024-06-19
Have you tried typing "exit" (no quotes) at busybox?

See post #4 busybox exit & boot - blue screen;s post
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
busybox See quixote post 2010
[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)

---

### Post by userubu64 on 2024-06-20
Yes, I tried to enter the output in the first screenshot. Thanks to this method, I learned that during boot the system cannot include the partition with the system enabled (sdb2)

The problem also persists on any Linux distribution. (I tried Mint, Fedora, Kali, Debian)
But the error is changing. Now I can&#8217;t really name any other errors.

---

### Post by Topsiho on 2024-06-20
Hi,

What do you mean with that you downloaded Ubuntu onto a flash drive?
You should have downloaded Ubuntu onto your hdd or so  and from that  created a bootable usb (flash?) drive.

Greetz, Topsiho

---

### Post by userubu64 on 2024-06-20
Welcome)) I'm glad to see you here!)
> [COLOR=#000000]What do you mean with that you downloaded Ubuntu onto a flash drive?[/COLOR]
[COLOR=#000000]You should have downloaded Ubuntu onto your hdd or so and from that created a bootable usb (flash?) drive.[/COLOR]
I mean I created a bootable USB flash drive.

---

### Post by userubu64 on 2024-06-21
Friends, what do you think the problem could be?
I reinstalled Ubuntu and I see this error again, but with a different uuid
O Great Oldfred, come to my branch
> **oldfred said:**
> Have you tried typing "exit" (no quotes) at busybox?

See post #4 busybox exit & boot - blue screen;s post
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
busybox See quixote post 2010
[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)
I can post the command results again if needed.

@oldfred

---

### Post by userubu64 on 2024-06-21
Can this statement be true?
> I suspect either /boot/initrd.img is missing drivers to access the drive.
And how can you fix this? I'm ready to help =)

---

### Post by Topsiho on 2024-06-21
Hi,

Reading your original post I knew you would encounter difficulties, for you can't boot from a flash drive onto which you downloaded Ubuntu, or whatever distribution, directly. What you downloaded is a so-called image, which you should use to  put it onto a flash drive using a special program, for Windows or for Linux, the name of which you should find for your self.
On the site of Ubuntu you can find info for installing Ubuntu which you can use.

Greetz, Topsiho

---

### Post by userubu64 on 2024-06-21
> **Topsiho said:**
> Hi,

Reading your original post I knew you would encounter difficulties, for you can't boot from a flash drive onto which you downloaded Ubuntu, or whatever distribution, directly. What you downloaded is a so-called image, which you should use to  put it onto a flash drive using a special program, for Windows or for Linux, the name of which you should find for your self.
On the site of Ubuntu you can find info for installing Ubuntu which you can use.

Greetz, Topsiho
Hello,
I followed this instruction:
[Install Ubuntu desktop | Ubuntu]("https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview")
What else can I use? =)

---

### Post by oldfred on 2024-06-21
Are you doing LVM/encrypted install?
Since reinstalling try just ESP & / (root) as ext4.
If it does not boot, then run Boot-Repair and post link to summary report.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yancek on 2024-06-21
You indicate that when you boot you see the grub menu.  Have you followed the suggestion above when seeing that menu to hit the e key on your keyboard.  This will change the screen and you should see the entry and there should be a line beginning with the work search and on that line it will show the root UUID.  Make note of this and then boot the Ubuntu installer and use the Try option and when you get to a Desktop, open a terminal and enter the command blkid, hit the enter key and check the output and compare the UUID you wrote down earlier to the one on the drive which you installed Ubuntu to.  From your posts above, it showed as sdb2.  How many drives do you have and what are the sizes? 

You indicate that you have reinstalled Ubuntu at least once.  You do understand that the UUID for these partitions will change on each install, correct?

I noticed in post 5 your gparted output showed it was unable to read the vfat EFI partition.  Do you still see this error when using gparted?  Is the error you continue to get the same, the ALERT UUID ?? not found?

---

### Post by userubu64 on 2024-06-22
> [COLOR=#000000]You indicate that when you boot you see the grub menu. Have you followed the suggestion above when seeing that menu to hit the e key on your keyboard. This will change the screen and you should see the entry and there should be a line beginning with the work search and on that line it will show the root UUID. Make note of this and then boot the Ubuntu installer and use the Try option and when you get to a Desktop, open a terminal and enter the command blkid, hit the enter key and check the output and compare the UUID you wrote down earlier to the one on the drive which you installed Ubuntu to. From your posts above, it showed as sdb2. How many drives do you have and what are the sizes?[/COLOR]

Yes, the system cannot detect the UUID of the sdb2 disk. Everything is identical, this can be seen in the screenshots on the 1st page. 
In total, I have 2 flash drives for loading in live mode and installing the OS, as well as my internal M.2 SSD.
What do you mean when you ask how many disks do I have? I hope I answered this question.

> You indicate that you have reinstalled Ubuntu at least once. You do understand that the UUID for these partitions will change on each install, correct?
Sure. I understand what a unique ID is, what it is needed for and that it is not static when reinstalling the system

> I noticed in post 5 your gparted output showed it was unable to read the vfat EFI partition. Do you still see this error when using gparted? Is the error you continue to get the same, the ALERT UUID ?? not found?
The answer to all questions: Yes, it is.

---

### Post by userubu64 on 2024-06-22
> **oldfred said:**
> Are you doing LVM/encrypted install?
Since reinstalling try just ESP & / (root) as ext4.
If it does not boot, then run Boot-Repair and post link to summary report.
[I'm using Ubuntu 24.04 LTS for installation.]("https://ubuntu.com/download/desktop")
Root is initially formatted as ext4, but if I change the ESP partition, the system is no longer detected in the BIOS
Link to the report: [https://paste.ubuntu.com/p/ktkNjXM7k9/](https://paste.ubuntu.com/p/ktkNjXM7k9/)
(Remember that I reinstalled the system again and changed the ESP partition to ext4)
Bug fix has not run at this time

> Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

It&#8217;s also interesting that the keyboard didn&#8217;t work on this laptop before, on UNIX systems
I know this because I first wanted to install Debian, which has an older kernel,
but I couldn't write a anything using the keyboard.
Now after updating Ubuntu 24.04 the keyboard works and I can write again =)
I think this suggests that the problem lies in the drivers for working with the SSD drive.

---

### Post by tea for one on 2024-06-22
> **userubu64 said:**
> Root is initially formatted as ext4, but if I change the ESP partition, the system is no longer detected in the BIOS
Link to the report: [https://paste.ubuntu.com/p/ktkNjXM7k9/](https://paste.ubuntu.com/p/ktkNjXM7k9/)
(Remember that I reinstalled the system again and changed the ESP partition to ext4)
Bug fix has not run at this time
I think that you have misinterpreted oldfred's suggestion from post 20.
The suggestion was to allow the installer to create the essential partitions.
i.e. ESP which has to be FAT32 and system root ext 4.

It is no surprise that there were problems after changing the ESP to ext4.

I suggest that you re-install using only two partitions (ESP = FAT32 and root = ext4)
After installation, remove all USB devices.
If the PC doesn't boot successfully, then boot into a live session and run boot-repair again and post the link.

---

### Post by userubu64 on 2024-06-22
> **tea for one said:**
> I think that you have misinterpreted oldfred's suggestion from post 20.
The suggestion was to allow the installer to create the essential partitions.
i.e. ESP which has to be FAT32 and system root ext 4.

It is no surprise that you had problems after changing the ESP to ext4.

I suggest that you re-install using only two partitions (ESP = FAT32 and root = ext4)
After installation, remove all USB devices.
If the PC doesn't boot successfully, then boot into a live session and run boot-repair again and post the link.

I do this every time I install an operating system. I have 2 partitions after installing sdb1(ESP == FAT32) and sdb2(root == ext4)

[I]Remarque:
[/I]*I tried manual disk partitioning, at this time 3 partitions ESP, MBR, EXT4 are created.*
*But this also does not give any results (Which is not surprising, because nothing changes for me, because I boot via EFI)*

---

### Post by oldfred on 2024-06-22
The Boot-Repair report says this:
> Grub-efi would not be selected by default because no ESP detected.

It does look like you now have FAT32 on sda, your flash drive, but none on sdb.

All your UEFI entries show booting from GUID or partUUID that does not exist.
You can see partuuid on line 59 in report or by this:
sudo efibootmgr -v
and then partitions with the partuuids:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

Minimum requirement for UEFI install is ESP - efi system partition and / (root). Root must be a Linux format, Ubuntu's default is ext4.
The ESP must be FAT32 with boot,esp flags if using gparted.
It can be small 50 to 100MB if planning only one instal wit grub on smaller drives, but for larger drives and potential future use or other boot loaders, 500 to 600MB is suggested.

You should eventually delete all the invalid UEFI entries. Years ago having too many entries caused issues. But no reason to have entries that will never work.
to see entries:
sudo efibootmgr -v
to delete entry where XXXX is number from above.
sudo efibootmgr -b XXXX -B
See also 
man efibootmgr

---

### Post by userubu64 on 2024-06-22
This issue has been resolved by other community members. If you want, I can insert a link to the solution.

---

### Post by sidylaye on 2024-07-22
Gg

---

### Post by supertomk1 on 2024-09-12
Hopefully, I get out of this never ending craziness, also. 
24.04 LTS
LTS because they know they have to work on too many issues. Anyway, installing 24.04.01 triggered some problems here and there for me. I quickly decided to go back to a plain 22.04 installation which now I know it's not so plain. I also fell into the UUID hell with many storage devices and USB drives including plugging into a different port generating new UUID's. It has been really crazy. A good things is that I know something like this can happen. Solving this mess was not very easy on me until now. EFI partitions including ones on the USB sticks, and EFI's have been living in our system setting module (let's just call it BIOS). I also tried zeroing HDDs. However, somehow, those UUID's managed to survive full-formatting, dismembering controllers and HDDs, totally being disconnected from any power source. I felt like someone is making a sick joke on me. 

I am still insane after working on this issue for days, now always a week, and I feel that I am very close to the end. Right now, it's like my break time because I finally got to the point all the UUID's are clean and matching but getting the exact same error!

---

### Post by supertomk1 on 2024-09-12
[https://forums.linuxmint.com/viewtopic.php?t=418455](https://forums.linuxmint.com/viewtopic.php?t=418455)

---

### Post by supertomk1 on 2024-09-12
Now, I really got it. 
Yes, UUIDs mix up was the real cause sometimes. However, its root problem was not UUIDs at all. The exact error messages as enters (initramfs) prompt after several minutes of silent waiting period while booting, is not really something totally new. Now, I finally got all the pieces together, and I realize how narrow-sighted I was. 

When googled with the error message, I found the exact thing happened in the past. I was so caught up with EFI and UUIDs that I've been totally blinded.

Anyhow, the problem was caused by "missing module," meaning missing drivers, needed with the whatever kernel released during the problems were spotted here and there. Those solution posts mentioning SATA controller setting, were quick fix solutions with the particular kernel released. I guess there can be multiple drivers causing the same symptoms sometimes. One driver I read about was Realtek r8168 being the cause as well. This time, it was caused with kernel 6.8.0-40 release for 22.04 as well as 24.04.

Why and how it was missed, I don't know, but [SIZE=4]**now, I really know! **[/SIZE]



> **supertomk1 said:**
> Hopefully, I get out of this never ending craziness, also. 
24.04 LTS
LTS because they know they have to work on too many issues. Anyway, installing 24.04.01 triggered some problems here and there for me. I quickly decided to go back to a plain 22.04 installation which now I know it's not so plain. I also fell into the UUID hell with many storage devices and USB drives including plugging into a different port generating new UUID's. It has been really crazy. A good things is that I know something like this can happen. Solving this mess was not very easy on me until now. EFI partitions including ones on the USB sticks, and EFI's have been living in our system setting module (let's just call it BIOS). I also tried zeroing HDDs. However, somehow, those UUID's managed to survive full-formatting, dismembering controllers and HDDs, totally being disconnected from any power source. I felt like someone is making a sick joke on me. 

I am still insane after working on this issue for days, now always a week, and I feel that I am very close to the end. Right now, it's like my break time because I finally got to the point all the UUID's are clean and matching but getting the exact same error!

> **supertomk1 said:**
> [https://forums.linuxmint.com/viewtopic.php?t=418455](https://forums.linuxmint.com/viewtopic.php?t=418455)
[COLOR=#000000]4 Hours Ago
supertomk1[/COLOR]
[COLOR=#000000][INDENT]**Re: Ubuntu 24.04 UUID =/**
[https://forums.linuxmint.com/viewtopic.php?t=418455](https://forums.linuxmint.com/viewtopic.php?t=418455)[/INDENT][/COLOR]

---

