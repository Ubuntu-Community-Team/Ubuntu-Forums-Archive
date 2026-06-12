---
title: "Ubuntu 13.04 won't start no matter what I do :("
date: 2013-09-03
forum: General Help
---

### Post by ABD_EL_HAMEED on 2013-09-03
My name is ABD EL HAMEED,I'm an 18 year old guy from Cairo,Egypt and this is my first experience ever with a Linux distro
My problem started when I wanted to install Ubuntu 13.04 on my new PC that I have windows 7 already installed on it,So I used the LiveCD to install it,the installation went well and after it was done it told me restart and so I did but when I boot I simply don't get the option to choose it at all and it boots directly to windows so I installed Ubuntu 12.04 as a test and it booted fine so I tried to reinstall 13.04 it but still the same issue even after about 5 reinstalls,I also tried to partition it manually but still the same problem so I searched for an answer for my problem and I found that it may have something to do with the fact that I have a UEFI BIOS instead of legacy one,So I downloaded boot repair disk and it gave me a window that told me when another window shows asking for confirmation to remove GRUB I should press TAB+ENTER but the confirmation window never appeared so I just created a boot info and I booted into the Ubuntu LiveCD and wrote the GRUB removal command in the terminal and the confirmation window appeared this time and I successfully removed GRUB and I tried reinstalling it again but the opration failed for some reason and I couldn't install GRUB after I chose the device that I want it to be installed on 
I tried all kinds of things to boot into it but still no go,So you guys are my last hope really
My PC specs if it's gonna help you guys
Intel Core i5 3570k
4 GB of RAM 
1 TB HDD
Gigabyte Z77X-D3H
Gigabyte GTX 760
So is there anything I can do to boot into Ubuntu
Thanks in advance :)

---

### Post by r_avital on 2013-09-03
Ahalan, Abd-El-Hameed, and welcome :)

The good news, first, are that your computer has more than enough resources to dual-boot between Windows7 and Ubuntu 13.04, and also, it's a good thing Windows7 was installed first.

Have you tried this guide? [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Make sure you **ignore** the procedures listed under [SIZE=2]"Installing Windows After Ubuntu[/SIZE]" (There is a sub-section there that is the only place that references UEFI, but since this is about installing windows AFTER Ubuntu, it won't apply to you).

I also found an alternate solution, but not very elegant, not sure it will work for you:  When you turn on your computer, BEFORE it begins to boot, can you press Esc. or Del (or the appropriate key on your system) to go into BIOS?  From BIOS, do you get an option to select which partition to boot, Windows or Ubuntu?  That might work, but the best solution is to have GRUB2 offer you a menu of Operating Systems (Windows7 or Ubuntu) to select from.

Let us know.

---

### Post by ABD_EL_HAMEED on 2013-09-03
> **r_avital said:**
> Ahalan, Abd-El-Hameed, and welcome :)

The good news, first, are that your computer has more than enough resources to dual-boot between Windows7 and Ubuntu 13.04, and also, it's a good thing Windows7 was installed first.

Have you tried this guide? [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Make sure you **ignore** the procedures listed under [SIZE=2]"Installing Windows After Ubuntu[/SIZE]" (There is a sub-section there that is the only place that references UEFI, but since this is about installing windows AFTER Ubuntu, it won't apply to you).

I also found an alternate solution, but not very elegant, not sure it will work for you:  When you turn on your computer, BEFORE it begins to boot, can you press Esc. or Del (or the appropriate key on your system) to go into BIOS?  From BIOS, do you get an option to select which partition to boot, Windows or Ubuntu?  That might work, but the best solution is to have GRUB2 offer you a menu of Operating Systems (Windows7 or Ubuntu) to select from.

Let us know.
Thank you or like we say shokran :p
I have read it now and I did the same steps but still the issue I also downloaded EasyBCD but it couldn't see Ubuntu 13.04 :(

---

### Post by dragonfly41 on 2013-09-04
I have no experience in UEFI but did search to find some links which might explain further ...


[URL="http://community.linuxmint.com/tutorial/view/858"]http://community.linuxmint.com/tutorial/view/858
[/URL]

[http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi](http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi)

---

### Post by r_avital on 2013-09-04
Abd-El-Hameed,

Let's take it one step at a time.  At this point, are you able to boot into Windows-7?  I looked at your first post, you said it immediately boots into Windows-7, so I guess you're ok on that part.

Are you able to remove the Ubuntu installation, I mean remove the Ubuntu partition, and then boot into Windows?

If you'd rather not remove the ubuntu partition, that's ok, I understand, you might be concerned that it will impact Windows.

I found a better guide, with better details on how to install on a UEFI system.  I'm sorry I didn't find it earlier for you.  And I'm trying to be very careful, because I don't know anything about UEFI (I think I understand what it does), so I don't want to take a chance and give you the wrong tips or instructions.  Take a look at this guide and see if it helps you.

One thing to remember (if you already know this, sorry for repeating it).  In Linux, specifically in Ubuntu, when you are looking at disk-drives and partitions, there is a naming-convention that will help you identify the different disks and partitions:

The first **device** is sda, the second is sdb, the third is sdc, etc.

The first **partition** on sda is sda1, second partition on sda is sda2, etc.  So, for instance, the second partition on the second disk is sd**b**2.

When you install Ubuntu, you get to a step in the installation that lets you configure the partitions, and on that screen, you will see the different partitions and the disk drives they are on, with those names.  If you are in doubt, the best way to tell which is which is by the sizes of the disk-drives and partitions.

Remember, if you have a partition dedicated to UEFI, it will also show in that screen, it could be sda1.

Here's the guide: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I wish I could help you more, but I don't know enough about UEFI and I don't want to screw-up your system :)

Let us know.

---

### Post by dragonfly41 on 2013-09-04
I'll throw in one further idea which might overcome the UEFI obstacle .. at least to get you started ..

Install VirtualBox on your windows and then install Ubuntu 13.04 as a VM in VirtualBox.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

You can in fact have VirtualBox running in Windows while you later sort out your dual boot configuration.

This will give you some experience in using Ubuntu.

---

### Post by ABD_EL_HAMEED on 2013-09-04
> **dragonfly41 said:**
> I have no experience in UEFI but did search to find some links which might explain further ...


[URL="http://community.linuxmint.com/tutorial/view/858"]http://community.linuxmint.com/tutorial/view/858
[/URL]

[http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi](http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi)

> **r_avital said:**
> Abd-El-Hameed,

Let's take it one step at a time.  At this point, are you able to boot into Windows-7?  I looked at your first post, you said it immediately boots into Windows-7, so I guess you're ok on that part.

Are you able to remove the Ubuntu installation, I mean remove the Ubuntu partition, and then boot into Windows?

If you'd rather not remove the ubuntu partition, that's ok, I understand, you might be concerned that it will impact Windows.

I found a better guide, with better details on how to install on a UEFI system.  I'm sorry I didn't find it earlier for you.  And I'm trying to be very careful, because I don't know anything about UEFI (I think I understand what it does), so I don't want to take a chance and give you the wrong tips or instructions.  Take a look at this guide and see if it helps you.

One thing to remember (if you already know this, sorry for repeating it).  In Linux, specifically in Ubuntu, when you are looking at disk-drives and partitions, there is a naming-convention that will help you identify the different disks and partitions:

The first **device** is sda, the second is sdb, the third is sdc, etc.

The first **partition** on sda is sda1, second partition on sda is sda2, etc.  So, for instance, the second partition on the second disk is sd**b**2.

When you install Ubuntu, you get to a step in the installation that lets you configure the partitions, and on that screen, you will see the different partitions and the disk drives they are on, with those names.  If you are in doubt, the best way to tell which is which is by the sizes of the disk-drives and partitions.

Remember, if you have a partition dedicated to UEFI, it will also show in that screen, it could be sda1.

Here's the guide: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I wish I could help you more, but I don't know enough about UEFI and I don't want to screw-up your system :)

Let us know.

> **dragonfly41 said:**
> I'll throw in one further idea which might overcome the UEFI obstacle .. at least to get you started ..

Install VirtualBox on your windows and then install Ubuntu 13.04 as a VM in VirtualBox.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

You can in fact have VirtualBox running in Windows while you later sort out your dual boot configuration.

This will give you some experience in using Ubuntu.
Thank you very much guys,I'm attempting to install Ubuntu 13.10 on the PC hopefully it'll work,I will post how the process goes

---

### Post by ABD_EL_HAMEED on 2013-09-05
Just tried to install Ubuntu 13.10 but there's a big problem now,When I tried to install it it gave me the option to erase disk and install along with other options instead of giving me the option to install along side windows so I canceled the installation cause I don't want that to happen now when I rebooted and tried to boot into windows IT WASN'T THERE and I can't boot into windows,What should I do now?I fear that windows is completely deleted from my hard drive
I didn't do anything for it to simply delete windows I just simply wanted to install Ubuntu 13.10 but when I found it gicing me the option to only erase the disk and install I simply canceled the installation and rebooted,so,what did I do wrong?Is there a way to rescue windows?

---

### Post by r_avital on 2013-09-05
> **ABD_EL_HAMEED said:**
> ...and I can't boot into windows,What should I do now?I fear that windows is completely deleted from my hard drive

No panic.  It's possible that Windows is still there.  

Instead of going immediately to install 13.10, can you run 13.01 from your DVD or USB?  With every Ubuntu distribution, there is a "Try" and "Install" -- use the "Try Ubuntu" option, this should boot into Ubuntu.

Once you booted into Ubuntu, use the terminal (Ctrl+Alt_T) and enter: gparted

It should show you a map of your hard drive.  You can make a screen-shot of that screen (Alt+PrintScreen), save it, and post it in a reply here (you have a fully functional Firefox browser in your "Try Ubuntu" session).

It's possible that only your UEFI partition is missing, or messed-up.  Do you have a Windows recovery disk, and a factory-reset disk from the manufacturer of your computer?  That would be the next step, but first, let's see that image so we can tell what your hard-drive and partitions look like.

---

### Post by ABD_EL_HAMEED on 2013-09-05
> **r_avital said:**
> No panic.  It's possible that Windows is still there.  

Instead of going immediately to install 13.10, can you run 13.01 from your DVD or USB?  With every Ubuntu distribution, there is a "Try" and "Install" -- use the "Try Ubuntu" option, this should boot into Ubuntu.

Once you booted into Ubuntu, use the terminal (Ctrl+Alt_T) and enter: gparted

It should show you a map of your hard drive.  You can make a screen-shot of that screen (Alt+PrintScreen), save it, and post it in a reply here (you have a fully functional Firefox browser in your "Try Ubuntu" session).

It's possible that only your UEFI partition is missing, or messed-up.  Do you have a Windows recovery disk, and a factory-reset disk from the manufacturer of your computer?  That would be the next step, but first, let's see that image so we can tell what your hard-drive and partitions look like.

Thanks I used the command you told but it needs root privilages :/,also I used GNU and ran the rescue command and it didn't find anything
Edit:now after using the sudo gparted command I found that my HDD was formatted since there's only 14.75 GB used on my PC :/
So I guess I'll simply reinstall everything again,I'll start with Ubuntu this time though u.u

---

### Post by r_avital on 2013-09-05
WAIT...

If you want to just install Ubuntu to see it working,  that's fine.  BUT, if you plan to dual-boot with Windows-7, [B]believe me,  it's much better if you install Windows FIRST.  

Please,[/B] folow the guide  in the link I posted in post number 6.

---

### Post by ABD_EL_HAMEED on 2013-09-05
> **r_avital said:**
> WAIT...

If you want to just install Ubuntu to see it working,  that's fine.  BUT, if you plan to dual-boot with Windows-7, [B]believe me,  it's much better if you install Windows FIRST.  

Please,[/B] folow the guide  in the link I posted in post number 6.

OK thanks I'll do so

---

### Post by ABD_EL_HAMEED on 2013-09-07
So after formatting my HDD I decided to install Ubuntu 13.04 first and so I did and it was working well so I went on installing windows and I partitioned using gparted from the Ubuntu LiveCD so instead of Ubuntu taking up my drive it now has 100GB of storage and I did notice a strange after the partitioning was over,before the partition it said that there was 18.xxGB used and after the partition there was only 5.xxGB used,anyway I went on to install windows on the empty new partition I created and after I finished installing it I restarted and I couldn't boot into Ubuntu anymore so I did a bit of a search and I tried various things to be able to restore Ubuntu again but only 1 thing worked and that was by booting from the LiveCD I used earlier and wrote those 2 commands
sudo mount /dev/sda /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
Those 2 lines worked as I'm now able to boot into Ubuntu again BUT I can't boot into windows now so what should I do?

---

### Post by dragonfly41 on 2013-09-08
> So after formatting my HDD I decided to install Ubuntu 13.04 first

You did not follow the advice given in post #11 to install Windows first!

Windows expects .. demands .. to run in the first partition.

You will have to reformat your drive into multiple partitions and reinstall first Windows and then Ubuntu.

e.g. my dual boot structure is

/dev/sda1      ntfs    Windows Vista    50 GB 
/dev/sda2      ntfs    Windows data     50 GB
/dev/sda3      extended partition (see multiple logical partitions below)
    /dev/sda4      ext4   Ubuntu 12.04   50 GB
    /dev/sda5      ext4   Ubuntu data     50 GB


but there can be variants on this structure where you allocate one logical partition to Ubuntu "/" (root) and another to Ubuntu "/home".   Search this forum for further dual-boot advice.

I ditched my windows "recover" partition since I have an installation CD.

Make sure you build a windows recovery disk as you reinstall Windows.

Another option is to install Ubuntu in an external USB drive.

---

