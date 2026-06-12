---
title: "Captive problem"
date: 2004-12-16
forum: General Help
---

### Post by ibs on 2004-12-16
Hi, i'm new to Ubuntu and recently installed Captive NTFS so i could have read/write support on my NTFS disks. I really need to have write support on them and i can't convert them to FAT. 

After going through the captive-install-acquire proccess i got this message:

Although essential modules ("ntoskrnl.exe" and "ntfs.sys") are available you may still want to get their better version and/or more modules. 
Despite drivers were found no NTFS disk partitions were found on your computer. You still can mount read/write NTFS partitions by using filesystem type 'captive-ntfs' such as:
	mkdir /mnt/captive-LABEL_C
	mount -t captive-ntfs /dev/hda1 /mnt/captive-LABEL_C

Ok, i decided to try it and i got:

root@ubuntu:/home/ibs # mount -t captive-ntfs /dev/hda1 /mnt/windows-c
Captive NTFS v1.1.5.  Check a new version at: [http://www.jankratochvil.net/](http://www.jankratochvil.net/)
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
lufs module not loaded: Try running /usr/share/lufs/prepmod to see more. at /usr/bin/captive-lufsd line 180


Now i tried to run  /usr/share/lufs/prepmod and this is what i got:

root@ubuntu:/home/ibs # /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-4-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-4-386/kernel/fs/lufs
Failed to find kernel headers for 2.6.8.1-4-386
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-4-386.
No Linux kernel sources for your running kernel were found.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-4-386/build
                /usr/src/kernel-headers-2.6.8.1-4-386
                /usr/src/linux-2.6.8.1-4-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-4-386


What can i do about this? I am new to Ubuntu and in fact also a bit new to Linux. Could please someone help me? It is very urgent fo me to get this to work.

---

### Post by kahping on 2005-01-02
i myself am having the same problem; any help would really be appreciated.

i tried synaptic but a search turned out only older kernel headers, which is rather unhelpful.

kahping

---

### Post by GentleHatemonger on 2005-01-02
sudo apt-get install linux-headers-386

---

### Post by kahping on 2005-01-06
[QUOTE=GentleHatemonger]sudo apt-get install linux-headers-386[/QUOTE]

tried, same results. or do i have to restart ubuntu? since it's just kernel headers i assumed u needn't reboot/restart GNOME.

kahping

edit: typo

edit2: if u insist, i got this message: "E: Couldn't find package linux-headers-386"; same thing even after "sudo apt-get update" then "sudo apt-get install linux-headers-386"

---

