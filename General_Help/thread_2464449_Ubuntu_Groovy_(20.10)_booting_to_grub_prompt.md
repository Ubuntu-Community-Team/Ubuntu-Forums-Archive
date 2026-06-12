---
title: "Ubuntu Groovy (20.10) booting to grub prompt"
date: 2021-07-02
forum: General Help
---

### Post by RossGammon on 2021-07-02
This morning I turned my Ubuntu Groovy machine on and got the grub prompt. I have not been doing anything recently other than emailing, browsing & installing updates when prompted by the Software Centre (including yesterday). It is possible I have a hardware problem, but I am hoping something happened in a recent update. There is a lot of conflicting information on the web, so I thought I would post here for some specific advice for my situation.

I have an SSD device to boot from, plus two SATA drives configured with a software RAID1 mirror for the home partition. There is also an external USB HDD plugged in which I backup the home drive to using the standard Backup utility.

At the grub prompt:
grub> set
..
cmdpath=(hd2,gpt1)/EFI/UBUNTU
...
prefix=(hd2,gpt1)/boot/grub
root=hd2,gpt1

grub> ls /
ubuntu/ boot/

grub> ls /ubuntu
grubx64.efi ...... grub.cfg ...... (blanks equals other .efi files)

grub> ls /boot
bootx64.efi ........ (blanks equals other .efi files)

grub> cat (hd2,gpt1)/efi/ubuntu/grub.cfg
search.fs_uuid <long-number-I-don't-want-to-type> root
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

The prefix does not match where the grub.cfg file is. There is no "grub" directory under "/boot". But I was more worried that I did not see the usual vmlinuz and initrd files and directories that most troubleshooting guides mention.

With crossed fingers I typed:
grub> boot
error: you need to load the kernel first

But where is it?

Any ideas on how to work out what has gone wrong from the grub prompt? I wanted to do this before attacking the problem from a Ubuntu 20.10 Live ISO where I have the power to make things worse!

Thanks

Ross

---

### Post by yancek on 2021-07-02
From the information you posted above, hd2,gpt1 is the EFI partition and the grub.cfg file there points to the partition on which Ubuntu is actually installed.  That would be the UUID, the long number you don't want to type.  So run the blkid command and check to see if it is the correct UUID for the Ubuntu filesystem install.  This would be where the /boot/grub directory is and there is another grub.cfg file there which contains all the menuentries you see when you boot.  The boot directory on that partition should also contain the vmlinuz/initrd files.e

---

### Post by RossGammon on 2021-07-02
Thanks yancek - I think that is getting me closer.

I don't seem  to have access to the blkid command at the grub prompt, but I did an "ls  (hdx, y)" of all the partitions listed with a "ls", and this lists the  UUID and the NAME of the partition. None of the UUIDs matched the UUID  in the grub.cfg I posted in the EFI partition. But one of the partitions  had the label 'UbuntuRoot'.

When I did an "ls" of this  partition, actually "ls (hd6,gpt2)/", I could see the /boot/grub  directory, and the grub.cfg there has all the grub menu items. I could  also see a lot of kernels there in the /boot directory.

I will try manually typing the commands in the /efi grub.cfg command with the UUID of this UbuntuRoot partition.

---

### Post by RossGammon on 2021-07-02
Yes - that worked. I am writing this from the machine that was broken.

There are some new software updates available, so before I log out I will do an apt upgrade, and then a update grub to see if that permanently fixes it.

---

### Post by RossGammon on 2021-07-02
OK, the apt upgrade and the grub update did not permanently fix it.

1. I cannot edit the grub.cfg file in the /efi partition from the grub prompt. If I manually boot into the system, where does the file live so I can edit it there?
2. What has changed the grub.cfg file yesterday? My apt log only shows some firefox & python updates (unattended). Some kernels were removed 5 days ago.

---

### Post by RossGammon on 2021-07-02
So - I found the 3 line grub.cfg mounted under /boot/efi/EFI/ubuntu. But this actually had the correct UUID (maybe after the update-grub command).

Another reboot, but still the old grub.cfg with the wrong UUID takes me to the grub prompt.

Some more googling, and someone suggested "sudo dpkg-reconfigure grub-efi-amd64". I manually ran the configfile command from grub prompt again, booted into Ubuntu and ran the dpkg-reconfigure command, then rebooted.

Success! :-)

I wonder what caused this mess?

---

### Post by RossGammon on 2021-07-16
So it has happened again one week later. I shut down the machine last night, but it wanted to install some updates. When I booted this morning I am back at the grub prompt. Once I get it working again, I will have to report a bug - but against what package?

---

### Post by Impavidus on 2021-07-16
Ubuntu 20.10 will reach end of life this month. Even if this is a bug and you can identify the package containing it, chances are low that it will be fixed before 20.10 dies. Maybe it's better to investigate this after moving to 21.04, if the problem is still present.

---

