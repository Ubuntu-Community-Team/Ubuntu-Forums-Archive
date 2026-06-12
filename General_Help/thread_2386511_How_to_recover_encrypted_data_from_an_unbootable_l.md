---
title: "How to recover encrypted data from an unbootable laptop?"
date: 2018-03-06
forum: General Help
---

### Post by leon.strauss on 2018-03-06
I could not find any previous posts that matched this situation.  Apologies if this is a duplicate ...

My laptop runs Ubuntu Studio 16.04.2 with an encrypted partition for the user data.
During a routine Ubuntu software update, the laptop dropped to the grub> prompt.
From there, I have been unable to boot the laptop or recover my data.
(Lengthy) details are below.

I would appreciate any pointers on :
either
(a) how to repair and reboot my system
or
(b) boot a Live CD and access my encrypted data (e.g. to back it up so an external device)

Thank you for reading this.
    leon

(1) Symptom:
During an Ubuntu software update, while processing the linux-fairmware package, the screen went blank and displayed a grub> prompt.
Actions such as grub> boot, or grub> reboot, or power-cycling the laptop, all return to the grub> prompt.

(2) Partition layout
From # fdisk -l (when the system was new), the partitions look like this ...

/dev/sda1 ... EFI system
/dev/sda2 ... Linux (the vmlinuz kernels, initrd files etc are located here)
/dev/sda3 ... swap
/dev/sda4 ... LUKS-encrypted data (this is what I want to access)

grub> ls (hd0,gpt2)/
This shows me the vmlinuz and initrd files which I would expect to see in /boot, and two directories ... efi and lost+found

(3) Attempts to recover
(3.1) Attempt a manual boot
grub> set root=(hd0,gpt2)
grub> linux /vmlinuz-4.4.0-116-lowlatency root=/dev/sda2
grub> initrd /initrd.img-4.4.0-116-lowlatency
grub> boot

This initiates a boot sequence.  It prompts for my LUKS passphrase ...
   Please unlock disk sda4_crypt:
I enter my LUKS passphrase and the sequence continues until these errors ...
   Target flesystem doesn't have requested /sbin/init
    No init found.  Try passing init=bootarg
It then displays the (initramfs) prompt

From (initramfs) I can see the sbin directory but it does not contain init.
(initramfs) pwd
/
(initramfs) ls
dev    usr         sbin    conf    etc    var    init    proc
root    scripts    lib64    run    lib    bin    sys    tmp

I tried to execute /init directly but that also failed
(initramfs) ./init
It goes into a loop printing this message repeatedly ...
   cryptsetup: lvm is not available

(This is odd, I did not do the initial install on this system but I am pretty sure it does not use LVM)

I have to power-cycle to regain control and get back to grub>

(3.2) Boot Xubuntu 16.04.2 Live CD
This presented a text-based menu ...
* Try Xubuntu without installing
   Install Xubuntu
   OEM install
   Check disk for defects

(Curiously it did not present the usual graphical interface although this worked as usual on another machine where I tested the live CD)

I selected "Try Xubuntu"
Cntl-Alt-F1 to get a terminal.
Login as xubuntu
Get a root bash shell and mount my system partition ...
$ sudo bash
# mount /dev/sda2 /mnt
# ls /mnt
This shows me the vmlinuz, initrd files as seen from grub> ls (hd0,gpt2)/, plus 3 directories ... efi, grub and  lost+found.

# chroot /mnt
Fails with this message ...
   /bin/bash: No such file or directory

(4) This is my current situation.  I cannot see a way to progress from either (initramfs) or the Live CD # shell.
Thanks in advance for any clues, hints or tips.

---

### Post by panditax on 2018-03-07
3b) Access to your encrypted data:
Run live cd, open terminal then:
> sudo -i #or get root shell in other way
cryptsetyp luksOpen /dev/sda4 sda4_crypt
<Enter your password>
mount /dev/mapper/sda4_crypt /mnt

Now you have your data in /mnt, you can just cd and browse it/copy/whatever.

3a) Check [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by leon.strauss on 2018-03-07
Panditax, many thanks for your prompt response :-)
This worked ...
- Boot live CD (this time I got the graphics interface)
- open a terminal
- $ sudo bash
- # cryptsetup luksOpen /dev/sda4 sda4_crypt
- Enter LUKS password
This automatically mounted the volume on /media/xububtu/{log hex ID number}
I am now able to browse my encrypted data.  Backup to an external drive is in progress.

I will review the BootRepair link in due course.
Thanks again for the solution.

---

