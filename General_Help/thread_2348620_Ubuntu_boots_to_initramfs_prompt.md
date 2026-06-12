---
title: "Ubuntu boots to initramfs prompt"
date: 2017-01-05
forum: General Help
---

### Post by brbegg on 2017-01-05
For some reason, I can no longer boot into Ubuntu. I believe it was version 14? I installed it with WUBI some time ago on a seperate partition. It worked fine for a while. Now, however, it boots up to a BusyBox prompt with initramfs. What does this mean, and what can I do to boot into the desktop again? (It dualboots with Windows 10 on my main computer and I don't want to mess up my computer...)

---

### Post by hakuna_matata on 2017-01-06
> **brbegg said:**
>  I believe it was version 14? I installed it with WUBI some time ago on a seperate partition. It worked fine for a while. Now, however, it boots up to a BusyBox prompt with initramfs. What does this mean, and what can I do to boot into the desktop again?
There are a lot of reasons for BusyBox prompts but the most common reason for Wubi is a [initramfs bug]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") . A temporary fix is to replace ro with rw in GRUB menu (see [askubuntu]("http://askubuntu.com/a/454943") ) OR to boot into a previous kernel version which still works. 

For [WubiUEFI]("https://github.com/hakuna-m/wubiuefi") I created a permanent fix [here]("https://github.com/hakuna-m/wubiuefi/issues/5#issuecomment-211083990") . It is based on unreleased [fix of noorez-kassam]("https://code.launchpad.net/%7Enoorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437")

Another possibility is to change **ro** to **rw** with **/etc/default/grub. **
If you change ```
GRUB_CMDLINE_LINUX=""
```
in **/etc/default/grub **to
```
GRUB_CMDLINE_LINUX="**rw**"
```
and update it with
```
sudo update-grub
``` (from German [ubuntuusers.de]("https://wiki.ubuntuusers.de/Wubi/Problembehebung/#BusyBox-nach-Start") ),
GRUB entries are permanently changed.

---

### Post by Impavidus on 2017-01-06
I have to link to this thread: [https://ubuntuforums.org/showthread.php?t=2229766](https://ubuntuforums.org/showthread.php?t=2229766)

Wubi doesn't work with most preinstalled Windows 10 (and 8) systems (because of UEFI, if I'm not mistaken) and is not on a separate partition, so are you really sure this is wubi?

Can you still boot Windows? Do you have backups?

---

### Post by brbegg on 2017-01-07
I will try these out.

---

### Post by brbegg on 2017-01-07
Yes, I did use WUBI. It is on a seperate partition of my drive, and I can still boot into Windows.

---

### Post by wildmanne39 on 2017-01-07
Please post a link to where you got the directions to install wubi in its own partition, because wubi installs inside windows and not to its own partition.

It has been unsupported for a long time.

---

### Post by ppnman on 2017-01-07
Wubi , really??
I think it is no longer supported &#129300;
Why you don't simply follow this (one of many many many all over the Internet) howto it works for me
http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/

---

### Post by hakuna_matata on 2017-01-08
> **wildmanne39 said:**
> because wubi installs inside windows and not to its own partition.

IMHO "separate partition" with Wubi means that brbegg didn't select Windows main partitition (C: drive on Windows) for installation. Probably, he selected a previously created Windows partition (e.g. D: on Windows). So Ubuntu has its own Windows host partition which contains the root partition image (ubuntu/disks/root.disk) and the swap file (ubuntu/disks/swap.disk).

@brbegg: Is it possible to read your Ubuntu files from Windows? see [here]("http://askubuntu.com/a/9935")

---

### Post by brbegg on 2017-01-08
Yes, that is what I did. It is on the U: partition, and I can easily access the files from Windows.

---

### Post by brbegg on 2017-01-08
I'm confused on how to do this... (I'm not a pro at linux &#128514;.) How exactly do I access "/etc/default/grub/" to change it?

---

### Post by brbegg on 2017-01-08
I think I may have found out the problem! The entire drive was COMPRESSED. *facepalm* I did that with a Windows partition once, and NTLDR wouldn't work if it was compressed. I'm going to try decompressing the drive and seeing if that solves the problem.

For those that are wondering, it's an NTFS partition.

---

### Post by brbegg on 2017-01-08
Yup! Decompressing the partition worked. Thank you to everyone who commented.

---

