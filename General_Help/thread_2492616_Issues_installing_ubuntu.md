---
title: "Issues installing ubuntu"
date: 2023-11-17
forum: General Help
---

### Post by lofiwk on 2023-11-17
Hi, I think there's not enough room in this box for me to post all the troubleshooting message errors I'm going through while installing ubuntu 22 on my msi stealth 15m.  

I don't know what I'm even looking at, I've used tso live usb and they all succeed on installing ubuntu (only works on safe graphics) but once it's done installing and it asks for a restart, my pc just stops working.  If i turn it off manually and get it back up and running again, message error changes, but that gave me no solutions whatsoever.  

For some reason, I can't even install other distros now!  I used to cruise through all sorts of distros with no problem and now this piece of junk won't accept anything other than windows 11.  

What dl I do?  I'm really hitting a wall here.

---

### Post by yancek on 2023-11-17
I'd start by posting wome infor on the machine you are using such as the manufacturer, the age of the computer, any OS on the system, graphics card and what is  when you tried to install Ubuntu.  If I understand, you are only able to boot in safe graphics and you can boot and it seems to install but on reboot it doesn't boot?  When the install finishes and you see the option to continue using or restart, you select restart and it freezes, is that correct?

---

### Post by lofiwk on 2023-11-17
You are right all the way until the freezing part.  I'm using a MSI Stealth 15M A11UEK, it has a RTX 3060 and Intel Core i7-11375H of 11th gen.  Wish I knew why's this happening now all of a sudden.  I wanted to test out the nvidia broadcast eye contact feature and since vm's can access to hardware i couldn't install the drivers which made me wanna install windows for a bit.  Worst mistake at all.  Wasn't even that good.  

[COLOR=#BDC1C6][FONT=arial][ link] [/FONT][/COLOR][https://imgur.com/a/4Bf8FZW](https://imgur.com/a/4Bf8FZW)[COLOR=#BDC1C6][FONT=arial][ /link]

[/FONT][/COLOR]If you saw the pictures I thank you for helping me sort this out.  

The first photo it's the main issue.  That's what happened when I tried rebooting the pc after the instalation was done.

If I manually turn off the pc and go back in, there's either two messages I'll eventually see which is the second and last photo.  I can never know!  

English is not my main language.  So if I'm not explaining myself well enough.
[IMG]https://imgur.com/a/4Bf8FZW[/IMG][IMG]https://imgur.com/a/4Bf8FZW[/IMG][IMG]https://imgur.com/a/4Bf8FZW[/IMG]

---

### Post by oldfred on 2023-11-17
Screen shot looks like some sort of drive issue.
It may need fsck.
Can you boot recovery mode from grub menu, which can let you run fsck as partitions are not yet mounted.
Or you can run fsck from live mode of live installer flash drive.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p3
sudo e2fsck -f -y -v /dev/nvme0n1p3

If you have to use safe graphics to install, it means when installing you need to also select to install proprietary drivers to get correct video.
If you can boot to recovery mode you can install drivers. This auto selects preferred driver for your card. You can choose others.
sudo ubuntu-drivers autoinstall

---

