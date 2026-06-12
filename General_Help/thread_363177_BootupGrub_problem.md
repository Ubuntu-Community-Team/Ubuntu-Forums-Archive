---
title: "Bootup/Grub problem"
date: 2007-02-16
forum: General Help
---

### Post by Jaiinus on 2007-02-16
I'm using Ubuntu Ultimate (which is Edgy if I'm not mistaken) and I finally got everything configured except getting my SATA drives working (Silicon Images 3114 SATA/RAID PCI Card and 2 Seagate drives). I am running a very old mobo (Asus P3 1Ghz) and what happens is that the machine boots up from machine bios first no matter what and neither the mobo or card's bios has a feature to disable this. My options were to hotplug every time, and have my LVM partitions messed up by changing UID's, or try installing grub on the drives.

I went on to try to install grub on these drives but had a lot of issues. Giving up, I rebooted to try playing with the BIOS again to see if I could dig up some arcane, poorly named feature which would make things work. After giving up on all of that I unplugged the SATA drives and I end up getting this:

"Grub jabber"
grub>

Computer's Relevant Configuration:
/dev/hda1      /boot      ext3
/dev/hda2      swap
/dev/hda3      /            xfs
/dev/hda4      /home    xfs


So I figured that I just nuked grub and I'd have to reinstall it, no big problem. So, here's what I've tried and the joined GRUB errors:

Used Dapper Drake Server CD's "Fix Broken System" on hda3 aka / and mounted hda1 onto boot. Proceeded to try grub-install /dev/hda and received error which stated "hda does not have any corresponding bios drive". I also tried running shell from install enviroment and using grub-installer but it tries to install to /target. I have not tried chroot'ing and running grub-installer after mounting my filesystems though. Trying that now.

Used Ubuntu Ultimate DVD, switched over to virtual console, mounted / and /boot and chrooted. Attempted grub-install as well as following this: [http://kbase.redhat.com/faq/FAQ_79_4256.shtm](http://kbase.redhat.com/faq/FAQ_79_4256.shtm) which uses grub's command line to attempt installation. From here I get error 15: File Not Found when doing "find /boot/grub/stage1" even when I can SEE it. To add insult to injury, at one point I managed to do find /etc/passwd and it found it on (hd0,3) which is right, although I can't get it to do that anymore. From here I try use root on all sorts of drive/partition number combinations but I get Error 21: Selected disk does not exist on every combination.

Used both DD server CD and Ultimate DVD and tried the install trick.

In summary:
When I boot up I get to grub's command line. Have tried manual grub install as well as install-grub and get various versions of "can't find x".

Thanks for any help, and if anyone has a decent fix for my original SATA card problem and maybe some links to decent, plain worded GRUB instructionals I'd be appreciative.

---

