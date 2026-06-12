---
title: "Neither grub-rescue nor grub-probe detect my ext2 filesystem"
date: 2017-02-17
forum: General Help
---

### Post by oliver-story on 2017-02-17
Hi all

I've recently updated my partition layout and now can't boot nor reinstall Grub.

When I turn on the computer I'm dropped into a 'grub rescue' shell. From here the command 'ls' shows all my partitions, but returns an 'unknown filesystem' error if I try to list details about any particular partition (e.g. with ls (hd0,1) - which is my boot partition).

However I these commands do work from a USB-booted supergrub2 disk, and I'm able to use this to boot my system.

My basic setup is:
- booting using legacy BIOS mode
/ on /dev/ubuntu/root (LVM partition on /dev/sda5 formatted as Ext4)
/boot on /dev/sda1 (formatted as Ext2)

Changes I made included:
- shrinking the /dev/sda5 partition containing the LVM /dev/ubuntu/root partition and filesystem, and moving it to the right to make space for the next step
- expanding the /boot partition and filesystem from around 200MB to around 400MB (I kept running out of space whenever there was a kernel upgrade)
- shrink /dev/sdb1 and the /dev/ubuntu/library LVM partition and filesystem, to make space at the end of the second drive
- copy a windows partition from an old laptop to /dev/sdb2 (hoping to transfer it into a virtual machine) - I've now deleted this partition in case it was the cause of the issues I'm experiencing.

Although these changes could be the source of my problem, I note the partitions are all accessible from within my system and are detected by the supergrub2 boot disk.

I've tried quite a few approaches to repair this:

1) from within the system (booted using supergrub2):
a) 

```
# sudo grub-install /dev/sda
```

Returns:
Installing for i386-pc platform.
grub-install: error: unknown filesystem

```
# sudo update-grub
```
 
Returns:
Generating grub configuration file ...
grub-probe: error: unknown filesystem

For reference, here's the output of running ```
# sudo grub-probe -vvv -d /dev/sda1 -t fs
``` which seems to be where the filesystem detection attempt takes place:
[http://pastebin.com/QMYR0k2c](http://pastebin.com/QMYR0k2c)

(also doesn't generate a grub.cfg - unsurprisingly given it can't detect the filesystem...

b) purging and reinstalling grub, which gives the error:[INDENT][COLOR=#000000]Grub failed to install to the following devices: /dev/sda[/COLOR]

[COLOR=#000000]Do you want to continue anyway? If you do, your computer may not start up properly.[/COLOR][/INDENT]

I said 'yes' then repeated step a) above 

c) using the boot-repair program (which recommended a purge and reinstall of grub, but wasn't able to complete)


2) from within a live session of Ubuntu 16.04, booted from USB:

a) check the filesystems with ```
fsck -f -p /dev/sda1
``` and ```
fsck -f -p /dev/ubuntu/root
``` (neither returned any errors)

b) mounted filesystems and tried ```
sudo grub-install /dev/sda
``` and ```
sudo update-grub
``` from within a chroot - which again both fail with an 'unknown filesystem' error.

c) mounted filesystems and tried 

```
# sudo grub-install [COLOR=#000000][FONT=monospace]--boot-directory=/mnt/boot /dev/sda[/FONT][/COLOR]

```
then repeat from step 1 a) ...

Link to bootinfoscript output (note this was generated with the supergrub2 USB disk inserted - because that's how I booted. It shows up as /dev/sdc):
[http://pastebin.com/Miff0pBR](http://pastebin.com/Miff0pBR)

Link to shorter bootinfoscript output with supergrub2 USB disk removed:
[http://pastebin.com/r93hcUsC](http://pastebin.com/r93hcUsC) 

NB there's no grub.cfg because the processes that are supposed to auto-generate it fail before they get to this stage.

---

### Post by ajgreeny on 2017-02-18
Hi oliver-story, and welcome to the forums.

It will be best if we can see exactly what is going on here if you go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by oliver-story on 2017-02-18
Thanks, added a link in my original post.

---

### Post by ajgreeny on 2017-02-19
Unfortunately I can not help you other than to say that the report is not what I expected to see, and it does not look as if you have properly installed Ubuntu so far; certainly there is no grub.cfg file to be seen, which is essential.  This may be the result of you changing your partition layout so please tell us in more detail what that means and what you actually did.

I see also that you have a good mix of different filesystems with LVM on two of the disks, about which I know nothing, and sdc appears to be formatted as hfs+, the Apple Mac filesystem.

I shall have to leave you in the hope that others come along and are able to help you with this.

---

### Post by oliver-story on 2017-02-20
Thanks for taking a look. For anyone who comes after:

- /dev/sdc is the supergrub2 USB disk - the hfs+ filesystem on there is part of the supergrub2 ISO. I will re-post a bootinfoscript output with the USB disk removed to reduce confusion.

- I installed Ubuntu on this computer several years ago and it's been running great - it's fully functional other than the ability to boot itself!
- grub.cfg is missing because it gets removed when you purge the grub-pc packages. As I understand it, it should be auto-generated when you install grub or run update-grub, but as both of these processes fail without detecting the ext2 filesystem on /dev/sda1 (let alone the LVM partitions), grub.cfg hasn't been re-created yet.

---

### Post by westie457 on 2017-02-20
Hi, looking at your pastebin links both have this section ```

[LIST]
[*][COLOR=#333333]========================= sda1/extlinux/extlinux.conf: =========================[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]--------------------------------------------------------------------------------[/COLOR]

[*][COLOR=#333333]## /boot/extlinux/extlinux.conf[/COLOR]

[*][COLOR=#333333]##[/COLOR]

[*][COLOR=#333333]## IMPORTANT WARNING[/COLOR]

[*][COLOR=#333333]##[/COLOR]

[*][COLOR=#333333]## The configuration of this file is generated automatically.[/COLOR]

[*][COLOR=#333333]## Do not edit this file manually, use: extlinux-update[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]default l0[/COLOR]

[*][COLOR=#333333]prompt 1[/COLOR]

[*][COLOR=#333333]timeout 50[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]include themes/debian/theme.cfg[/COLOR]

[*][COLOR=#333333]--------------------------------------------------------------------------------[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]=================== sda1: Location of files loaded by Grub: ====================[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]           GiB - GB             File                                 Fragment(s)[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]   0.093498230 = 0.100392960    vmlinuz-4.4.0-59-generic                       9[/COLOR]

[*][COLOR=#333333]   0.406000137 = 0.435939328    vmlinuz-4.4.0-62-generic                       9[/COLOR]

[*][COLOR=#333333]   0.367341042 = 0.394429440    initrd.img-4.4.0-59-generic                   13[/COLOR]

[*][COLOR=#333333]   0.320461273 = 0.344092672    initrd.img-4.4.0-62-generic                   14[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]================= sda1: Location of files loaded by Syslinux: ==================[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]           GiB - GB             File                                 Fragment(s)[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]   0.079590797 = 0.085459968    extlinux/extlinux.conf                         1[/COLOR]

[*][COLOR=#333333]   0.198682785 = 0.213334016    extlinux/chain.c32                             2[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333]============== sda1: Version of COM32(R) files used by Syslinux: ===============[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*][COLOR=#333333] extlinux/chain.c32                 :  COM32R module (v4.xx)[/COLOR]

[*][COLOR=#333333] [/COLOR]

[*]
[/LIST]

```
Knowing less about LVM than you and ajgreeny I am not sure if this is the problem or whether it contains a solution.

---

### Post by oliver-story on 2017-02-20
Thanks Westie457. Don't think it's the problem - the /sda1/extlinux/ etcetera files are I believe associated with syslinux, which is the bootloader Ubuntu used to use (according to this post: [http://askubuntu.com/questions/651902/what-is-the-difference-between-grub-and-syslinux](http://askubuntu.com/questions/651902/what-is-the-difference-between-grub-and-syslinux)).

As far as I can see from my bootinfoscript output, syslinux isn't installed in the MBR of /dev/sda so shouldn't get activated on boot.

To test this as an idea I've renamed the /boot/extlinux folder to a temporary name, and tried running sudo grub-install /dev/sda again. This returns the 'unknown filesystem' error i.e. no change.

---

### Post by oliver-story on 2017-02-22
I've now solved my issue with a work-around - getting rid of the separate /boot partition, moving /boot into my root partition, and then running grub-install and update-grub.

grub-install correctly detects that /boot is now inside an LVM container, and adds the necessary grub LVM module to core.img

I still don't know why grub-probe couldn't detect the ext2 filesystem on my /dev/sda1 partition. I can only think of:
- something wrong with the partition or filesystem - which doesn't seem likely since a different version of grub could boot it, and it is detected and used fine from within Ubuntu
- a bug in Grub - which doesn't seem likely as errors would be popping up for people all over the place if grub couldn't detect the ext2 filesystem.

---

