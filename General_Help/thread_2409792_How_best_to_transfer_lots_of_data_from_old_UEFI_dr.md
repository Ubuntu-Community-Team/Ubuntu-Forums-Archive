---
title: "How best to transfer lots of data from old UEFI drive to new UEFI drive (with LUKS)?"
date: 2019-01-06
forum: General Help
---

### Post by fr33z0n3r on 2019-01-06
I have 2 Ubuntu installs on separate internal drives.  They are both GPT/UEFI encrypted LVM installs.  But they are sharing the same mobo.  I'm replacing one with the other, effectively,  but I'd like to copy over all my data on it.


[LIST=1]
[*]I have a lot of data, and I'd like to ideally transfer it directly if possible. 
[*]I'd like to retain and not negatively impact the ability to boot either of the drives (OS's). 
[/LIST]

It seems like mounting the old drive internally would be ok, assuming I can mount the encrypted volume fine and that this wouldn't negatively impact the accessibility of the old OS - in case I need to run it again.

But is there any chance that having these 2 UEFI drives connected at the same time break the ability to boot one or the other?

Let me know your recommendation - keep in mind I have no other system to install a drive into - just the one.

TIA!

---

### Post by HermanAB on 2019-01-07
If you plug both in at the same time, then you may have trouble booting up.

You would need to select a boot drive in the BIOS.  If you cannot distinguish between them, boot with a USB install widget, then mount the two / partitions in /mnt/old and /mnt/new or some such, then you can copy to your heart's content.

You will only damage the UEFI, MBR or /boot if you go and write there.  Just don't do that.

---

### Post by oldfred on 2019-01-07
With UEFI, disconnecting a drive will have UEFI forget its entry. 
You then can use efibootmgr or reinstall grub to recreate an new UEFI entry. You may want to houseclean old entry.

As long as separate installs, so UUIDs & GUIDs are different you should be ok.
But if devices are both the standard /dev/ubuntu-vg/root, be sure not to use device in any command.
Not sure if device is used in grub's boot or not, I would check.

---

### Post by fr33z0n3r on 2019-01-07
On my old system this is what is in /boot/grub/grub.cfg

You can see /dev/mapper/ubuntu-root in all entries.

[IMG]https://i.imgur.com/IUiq4dB.png[/IMG]

---

### Post by oldfred on 2019-01-07
Are they separate installs, different UUID for /boot partition.
And in UEFI /efi/ubuntu/grub.cfg different UUID ?
I would think they booted install would not yet see the second install.
The issue has always been the system, BIOS or UEFI seeing two identical drives and then grub having identical UUIDs to use to boot from.

---

### Post by fr33z0n3r on 2019-01-07
they are separate (not cloned) installs.

the GUIDs are unique, but not sure about the volume names matching since you warned me about disconnecting them causes issues.
The UEFI grub.cfg guid is also different.

---

### Post by Dennis N on 2019-01-07
LVM won't let you mount LVs in two volume groups with the same name (ubuntu_vg). So you can't copy any files between the disks. Solution is to rename the volume group on the original disk. 

Here's a discussion found with google search:
[https://unix.stackexchange.com/questions/333914/two-physical-disks-with-same-volume-group-names-preventing-access](https://unix.stackexchange.com/questions/333914/two-physical-disks-with-same-volume-group-names-preventing-access)

---

### Post by fr33z0n3r on 2019-01-07
I manually named the vg on my original system, as I manually built it. it is just called ubuntu.

I'm not sure what 18.04 uses by default, and that is the question to be answered. I'll research it before doing anything.

---

### Post by Dennis N on 2019-01-07
Ubuntu uses ubuntu_vg. If they are different, should be no problem.

---

### Post by fr33z0n3r on 2019-01-11
> **oldfred said:**
> With UEFI, disconnecting a drive will have UEFI forget its entry. 
You then can use efibootmgr or reinstall grub to recreate an new UEFI entry. You may want to houseclean old entry.


Can you please explain to me about this process with efibootmgr?  I am guessing I would have to do this from my live USB?   Since it doesn't find any bootable device when the drive is unplugged (it seems based on the original issue)

Here is my boot-repair paste for my functioning system: [http://paste.ubuntu.com/p/K4QyQjpHNB/](http://paste.ubuntu.com/p/K4QyQjpHNB/)

As a note, my bios does not support adding a UEFI entry.  Not sure how common that is nowadays.

Would this create the Boot0000 option for me again?  Or is it more complex than that?

```
Boot0000* ubuntu    HD(1,GPT,b4ea1cb0-5b40-4a03-856c-04b407e94e13,0x800,0xf3800)/File(EFI\ubuntu\grubx64.efi)
```

```
sudo efibootmgr -c -l \\EFI\\ubuntu\\grubx64.efi -L "ubuntu" -p 1 -d /dev/sda
```

---

### Post by oldfred on 2019-01-11
See also 
man efibootmgr

These are typical entries I have seen:
        sudo efibootmgr -c  -w -L ubuntu -d /dev/sda -p1
sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.
[http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected](http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected)

I think yours may work, not sure about double slash but have seen some comments that it accepts several alternatives on slashes.

---

### Post by fr33z0n3r on 2019-01-12
I've been working up to the data migration setup.  

I made screenshots and BootInfo of the new OS config.

I've just kept both drives plugged in, and manually booted to the correct UEFI partition for the new OS.

While I'm logged into the new OS,  it shows an encrypted volume/partition in Files (GUI) and it seems to comprehend how to access it.

I think I'm going to try this instead of some manual hack.  Not sure why Ubuntu wouldn't properly support access to an encrypted volume (from within another OS relying upon an encrypted volume)

Wish me luck!

Rats - Got "Error unlocking /dev/sdb3: Failed to activate device: Operation not permitted"

---

### Post by oldfred on 2019-01-12
While older, the first part is just mounting an encrypted partition.

[https://ubuntuforums.org/showthread.php?p=4530641](https://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by fr33z0n3r on 2019-01-12
Turns out,  that I was able to mount it via the command line via just this command.

```
sudo cryptsetup luksOpen /dev/sdb3 my_old_drive
```

Then I had access in the Files app to browse and copy data.

I then used the GUI to unmount the volume,  seemingly without issue?

I still see the entries (PVs and LVs) related to that command in /dev/mapper.

So I ran some more commands.

```
# Mounting LUKS:

sudo cryptsetup luksOpen /dev/sdb3 my_old_drive

# This made the volume accessible in the GUI Files app

# Unmounting:

# First unmount in the GUI FIles app!

sudo lvchange -an /dev/ubuntu/root
sudo lvchange -an /dev/ubuntu/swap
sudo vgchange -an ubuntu
sudo cryptsetup close my_old_drive
```

---

