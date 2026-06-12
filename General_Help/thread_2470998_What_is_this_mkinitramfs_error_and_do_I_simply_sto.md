---
title: "What is this mkinitramfs error and do I simply stop it by changing one line in a file"
date: 2022-01-19
forum: General Help
---

### Post by slaytanicprion on 2022-01-19
/etc/initramfs-tools/conf.d/resume.save ?  All it contains is this line : /etc/initramfs-tools/conf.d/resume  I've been having this problem ever since I installed Ubuntu Mate 20.04, now I'm up to 20.04.3, it doesn't prevent updates from working, but it is annoying and will show up everytime kernel updates are made. I've posted about it here before and read a lot about what it could be since then (plus taking account of the nice people who gave me solid leads into fixing this), it seems that it's because I installed the OS with no swap partition, since it's possible to do so in 20.04, but the OS saw an old, unused (at least in theory, it is using it) swap partition on an old hard drive I will be removing soon that has Mint 17.3 on it and a swap partition. I looked at Disks and it is using the swap partition on that different drive. Apparently this is related.  Also /etc/initramfs-tools/conf.d/resume contains   ```
RESUME=NONE
```  Everytime I boot before the gui login screen, I see a line about mkinitramfs and RESUME = none, it's a shame I can't seem to find it through logs, and it's not there long enough for me to write it down.   I've done my research since last time I posted about this, it's not a critical issue, but it's annoying and I don't know what will happen once I remove that old hard drive and replace it with the SSD I got in a box here right now, it might start to look for a missing swap partition on another drive that's not there. Or it might fix it.   I'm thinking maybe just changing the value of RESUME=none to something else might fix it, but it's not clear yet. Help needed still :\

[ATTACH=CONFIG]289853[/ATTACH]

---

### Post by slaytanicprion on 2022-01-20
This thread seems relevant to what I'm trying to correct : [https://ubuntuforums.org/showthread.php?t=2401012](https://ubuntuforums.org/showthread.php?t=2401012) . The thing is, they actually want their conf.d/resume file to say NONE in there.   ```
 /dev/sdb1: UUID="5de63a03-0b43-4705-8e28-ba7596f30082" TYPE="ext4" PARTUUID="d88eb14d-01" /dev/loop0: TYPE="squashfs" /dev/loop1: TYPE="squashfs" /dev/loop2: TYPE="squashfs" /dev/loop3: TYPE="squashfs" /dev/loop4: TYPE="squashfs" /dev/loop5: TYPE="squashfs" /dev/loop6: TYPE="squashfs" /dev/loop7: TYPE="squashfs" /dev/sdc1: UUID="260EE66F0EE63807" TYPE="ntfs" PARTUUID="000ee848-01" /dev/sdc2: LABEL="brandnew" UUID="28a09e21-c1a3-4bce-8bf5-bec48da98bfb" TYPE="ext4" PARTUUID="000ee848-02" /dev/sdc3: LABEL="7" UUID="6A284AAB284A75DB" TYPE="ntfs" PARTUUID="000ee848-03" /dev/sda1: UUID="1e9c4f66-b4fb-4d75-a6de-c53c44187f3e" TYPE="ext4" PARTUUID="00095704-01" /dev/sda5: UUID="9c3dc736-72b8-42ba-a452-6adeb1996a31" TYPE="swap" PARTUUID="00095704-05" /dev/sdd1: UUID="5D59C95C4A7116B4" TYPE="ntfs" PTTYPE="dos" PARTUUID="defd8464-0d02-426c-ab61-3b7edbb416a7" /dev/loop8: TYPE="squashfs" /dev/loop9: TYPE="squashfs" /dev/loop10: TYPE="squashfs" /dev/loop11: TYPE="squashfs" /dev/loop12: TYPE="squashfs" /dev/loop13: TYPE="squashfs" /dev/loop14: TYPE="squashfs" /dev/loop15: TYPE="squashfs" /dev/loop16: TYPE="squashfs" /dev/loop17: TYPE="squashfs" /dev/loop18: TYPE="squashfs" /dev/loop19: TYPE="squashfs" /dev/loop20: TYPE="squashfs" /dev/loop21: TYPE="squashfs" /dev/loop22: TYPE="squashfs" /dev/loop23: TYPE="squashfs" /dev/loop24: TYPE="squashfs" /dev/loop25: TYPE="squashfs" /dev/sde1: LABEL="Seagate Expansion Drive" UUID="BCE846FFE846B782" TYPE="ntfs" PTTYPE="atari" PARTUUID="000b3352-01" /dev/loop26: TYPE="squashfs" 
```    I think entering the UUID of the swap somewhere would fix things? BTW, I do not know what all those loop devices are, they appear by themselves and more keep showing up the longer the system is running, there is none after a clean reboot. I'm thinking I should point it to the swap partition that is on the old drive with the old Mint 17.3 that Ubuntu Mate 20.04.3 decides to use even if I didn't set a swap partition when installing it originally, as 20.04.1 ofc. This is the closest to my issue I can find, except they seem to want to the reverse of what I want, but after giving it much thought, since it insists on using the swap partition on that old drive (it's really old but will not die, first generation WD SATA drive before they even had colour coding) but I will have to remove it soon, I have to make space in my desktop for the brand new SSD I got since months but am putting off installing since I don't want to mess up this installation.

---

### Post by GhX6GZMB on 2022-01-20
Perhaps if you attach a CODE section instead of a picture of a cat? skunk? the responses would be more helpful.

---

### Post by slaytanicprion on 2022-01-20
The code is in the update from the Software Updater, it is not logged anywhere, hence why I gave a screengrab of my desktop, don't insult my old cat who died at 20 ½ y/o in sept 2020. Maybe I should have maximized the window to spare you from the mildest desktop image on earth.  I put everything that's needed to be known in code tags. The conflicting file that gives a permission denied despite root access has one line. In my second post I gave the results of a sudo blkid so the UUID of my drives could be seen, especially sda5 which is the swap from the old Mint 17.3 hard drive (sda) that Ubuntu Mate decided to use as a swap of its own even if it was on another hard drive. It's all there, if you have no idea then don't reply.

---

### Post by QIII on 2022-01-20
@slaytanicprion

You did not put everything that needed to be in code tags in code tags.

Rather than including images of terminal output, please copy the text from the terminal and post it between code tags.  That avoids possibly fuzzy images, insults aimed at pets and keeps those with slow connections or data limits from passing by when they see a large image.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.


> if you have no idea then don't reply.

Please do not dictate to others the manner or content of their replies.

---

### Post by slaytanicprion on 2022-01-21
You can't copy/paste text from the Software Updater in Ubuntu Mate.  Otherwise I would have done so, it's a pain, believe me, I know. Now..  that etc/initramfs-tools/config.d/resume file has to have its value of  RESUME=NONE changed to stop this is what I understand. Likely to the  swap partition on that other drive it is unfortunately using by default  (sda5). I'd like to know if I'm on the right track and if there is a  specific format to follow when entering the UUID...I never messed with  fstab and such, I know what a UUID is, but that's about it.

I put the contents of the file in code tags and I did (unfortunately it all came up one one line) do the same for the results given by "sudo blkid". I don't know what else you would want to have in code tags.

---

### Post by QIII on 2022-01-21
You can surely copy and paste from the terminal.

---

### Post by slaytanicprion on 2022-01-21
That is true, I don't do updates from the terminal because it wants to add packages that Software Updater doesn't want to (for good reason), I've got an AMD video adapter and that nvidia-prime package always wants to get installed when doing it manually. But I guess I'll find a way next time I update to do it through terminal. But everything one needs is included in my post.

---

### Post by QIII on 2022-01-21
And we request that rather than images, such things be included as text in code tags.

---

### Post by VMC on 2022-01-21
Try updating it ```
update-initramfs -h
```

---

### Post by slaytanicprion on 2022-01-26
permission denied, I can't do anything with initramfs.

I took screengrabs of the terminal last time I had updates. There were less instances of the error regarding that /etc/initramfs-tools/conf.d/resume and config.d/resume.save files (the latter contains only '/etc/initramfs-tools/conf.d/resume' and I've figured out it's the value in that file that needs changing.

There were less instances where the error appeared, there was no linux-firmware package updates this time, it also shows up when that gets updated. But if this helps those who will not even give a quick glance at something because it's in a GUI, I got you covered lol :

<image snipped>


I found an image host that gives bbcode to make images thumbnails, I'm sorry, the one I use normally was down when I made my OP, so I used another I wasn't familiar with, I know they have to be in this format, clickable thumbnails.

Just saying this out of courtesy, I've had a thread like this before, many helped, but we didn't end up to a conclusion. I deducted what was going on myself and some agreed but nobody had their Ubuntu using a swap partition on another drive when it was installed without a swap partition the old school way since 20.x.x doesn't need one. I've seen help sites and posts here where people are copying the UUID of a swap drive to that resume file to correct something, but the issue was always slightly different or as in the one I linked earlier, the reverse was wanted somehow.

As you can see in this update, it does finds Linux Mint 17.3 on one drive (sda), which is an old drive I am going to replace soon after I verify there isn't anything in there I haven't backed up that I would need later but I think I have it entirely backed up on some external drive that is not connected to anything right now, so I should be okay, the thing is, the OS is using that old OS' swap partition which is on a different drive, that happens to be sata 3gb/s, its a miracle it works so well 15 years later, WD doesn't make em like that anymore heh. Also ignore the Windows 7 it sees here, it's on the third (there's 3 hdd's currently in the desktop), it sees the boot partition but the system is gone entirely, I just didn't format the entire drive because doing so would cause major data loss, the drive win7 was on is a 4gb drive and there is other partitions than that right now that have data I cannot move, I have it backed up, but it would be very inconvenient for me to use OS-Uninstaller for example just to get rid of some drive's windows boot partition, the other partitions on it are ext4 and data only and it's a high performance (as high as a regular HDD can be), at least for a WD Black 4TB drive.

I think Fuse has something to do with this somehow. I want to install CurlFtpFS and installation fails because it says I don't have fuse version 2.2 and over when I have version 2.9.9-3, it's not seeing it, doing modprobe fuse doesn't show anything. Hence why I use blkid to list those drives and UUID's. I could be off, but this CurlFtpFs ./configure error got me thinking, there's something going on with Fuse that doesn't make sense here and maybe, just maybe that error I see at boot before the logon window and when I update kernel packages and mkinitramfs is called upon and permission is denied. I cannot even do "sudo initramfs-tools" it will tell me permission denied, even going straight into su in a root window.

edit: looked for curlftpfs in the current repos and there it was, unlike when I was running versions of ubuntu earlier than 20.x, but it installed fine the usual way, sudo apt install curlftpfs worked (which is great for me but it might not be a clue like I thought, still, the ./configure when trying to build it from source failing cos it couldn't find fuse was strange, the version of fuse on 20.04.3 is much much more recent than 2.2).

---

### Post by QIII on 2022-01-28
Please allow me to say this again:

Post all terminal commands and their results in code tags.  I have removed your image and left space for you to do as requested.

---

### Post by slaytanicprion on 2022-02-02
Ok, I did the latest update I knew would bring up the error. Thankfully it wasn't huge so I was able to catch it in terminal and copy paste it to Pluma

```
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for linux-image-5.4.0-97-generic (5.4.0-97.110) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-97-generic
/usr/sbin/mkinitramfs: 1: /etc/initramfs-tools/conf.d/resume.save: /etc/initramfs-tools/conf.d/resume: Permission denied
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-97-generic
Found initrd image: /boot/initrd.img-5.4.0-97-generic
Found linux image: /boot/vmlinuz-5.4.0-96-generic
Found initrd image: /boot/initrd.img-5.4.0-96-generic
Found linux image: /boot/vmlinuz-5.4.0-94-generic
Found initrd image: /boot/initrd.img-5.4.0-94-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint 17.3 Rosa (17.3) on /dev/sda1
Found Windows 7 on /dev/sdc3
done

```

Now I don't need to repeat myself regarding anything else, it all comes down to that resume file and what it contains. Seems like I'd have to put in the UUID of sda5, the swap partition on the old OS that's on the sda drive that Ubuntu decided to use despite installing it with no swap file, hence some incoherence in the background. The mkinitramfs error points to that file which deals with swap partitions. Hopefully we can move on to something more solid because I got a brand new SSD and I need to make an image of this OS and put it on that SSD (something I know how to do) but before I even install that drive, I need for the OS to be without basic errors like this. Thank you.

---

