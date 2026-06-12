---
title: "Reboot then grub failed.  Repairs failing"
date: 2020-06-12
forum: General Help
---

### Post by Yippee38 on 2020-06-12
I've got a Mythbuntu install that I've had running for years.  I run the updates when the prompt shows up, but I'm not sure what the current version of Ubuntu is.  I know it had 14 the last time I checked.  Every once in a while, when I reboot the machine, grub gets messed up.  This problem occurred the other day.

Now when I attempt to boot the machine, I get the typical:
```
error:  no such device:  cd7a24f4e....
grub rescue>
```

I've identified my root paritition as /dev/sda3, which is hd3,gpt3.  I attempted to fix this problem through grub rescue, by typing the following commands (found this on a forum somewhere):
```
grub rescue>set boot=(hd3,gpt3)
grub rescue>set prefix=(hd3,gpt3)/boot/grub
grub rescue>insmod normal
grub rescue>normal
```

However, when I run "insmod normal" I get:
```
error:  symbol 'grub_file_filters' not found.
```

I have no idea what that means or how to fix it.  I've googled, and not found any help on it.

I've also tried using Boot-Repair.  In the past, I've had great luck with this.  UEFI causes some problems, but I got around this by putting it on a bootable USB stick.  This time, however, when I tried the the recommended method of recovery, I got the following error:
```
dpkg-error detected.  Please open a terminal then type (or copy-paste) the following command:
sudo chroot "/mnt/boot-sav/sda3" dpkg-configure -a
Then close this window.
```

When I run that command in terminal, I get the following:
```
dpkg:  error:  Unable to access dpkg status area:  No such file or directory.
```

I googled that, but found nothing that was of any help.

I ran Boot-Repair again, but this time ran it for the bootinfo.  It can be found in this [pastebin]("https://paste.ubuntu.com/p/w6mhk9nfqk/").

Does anybody have any suggestions on how I can fix my boot issue?

---

### Post by oldfred on 2020-06-12
You show 18.04 installed in UEFI boot mode to a gpt partitioned drive on sda.
But sdb & sdd are older MBR partitioned. Your sdc is gpt.

But you have old grub BIOS boot in MBR of sda, sdb & sdd. Those will never work and if you boot in BIOS mode you will not boot and will give grub errors.
You must always boot in UEFI boot mode.

Are you booting in UEFI mode?
I might just totally reinstall grub using Boot-Repair in UEFI boot mode.

---

### Post by Yippee38 on 2020-06-13
> **oldfred said:**
> Are you booting in UEFI mode?

I actually have no idea.  I've spent all morning looking through the BIOS/UEFI Utility and googling info on the motherboard.  I can't find any information about switching the mother board between legacy mode and UEFI mode.  It acts like it's in Legacy/UEFI mode though.  When it boots, and I hit the key to bring up the boot menu, it shows me UEFI options and AHCI options.

> I might just totally reinstall grub using Boot-Repair in UEFI boot mode.

As far as I can tell, you cannot load Boot-Repair in legacy mode.  If I try to do so from a CD-ROM, it fails and tells me I need to launch it in UEFI mode.  As I've mentioned, I've tried that and it fails with the dpkg error.

---

### Post by oldfred on 2020-06-13
What brand/model system or motherboard?

Microsoft has required vendors to allow users to turn on/off UEFI Secure Boot. So you have settings somewhere.
Did you check your manual?

---

### Post by Yippee38 on 2020-06-13
ASRock FM2A85X Extreme6 motherboard.  I checked the manual.  I checked their website.  I look on YouTube, and I googled.  I also went through the UEFI Utility/BIOS about 6 times, screen by screen.  They talk about fastboot and secure boot, but not turning on and off UEFI.  I know UEFI is available as I boot my USB stick from the option that lists it as a UEFI device.  But it looks like Legacy stuff is enabled as well as those are options.

I also know from experience with other motherboards that some vendors hide those settings deep.

---

### Post by oldfred on 2020-06-13
One of my motherboards (neither Asrock) have UEFI settings under the CSM (legacy) boot line in UEFI/BIOS. That seems backwards as it is UEFI and turning on CSM is really an option in UEFI, not other way around.

I see this in your manual.
> PCI ROM Priority
Use this item to adjust PCI ROM Priority. The default value is [Legacy
ROM].

Have you updated UEFI to latest available from Asrock?
That may also reset some settings, so be prepared to redo them. I keep a list.

---

### Post by Yippee38 on 2020-06-14
> **oldfred said:**
> Have you updated UEFI to latest available from Asrock?

Yeah.  The last update was in 2013.  I've been running that version for a long time now.

---

### Post by Yippee38 on 2020-06-16
Does anybody have any clues about the "error:  symbol 'grub_file_filters' not found." error, or the "dpkg:  error:  Unable to access dpkg status area:  No such file or directory." error?

---

### Post by oldfred on 2020-06-16
This error looks like you are booting in BIOS mode, as it is looking for an UUID that does not exist.
> error:  no such device:  cd7a24f4e....

Your boot is on sda3:
> sda3 ext4     b7ac185d-80ec-4c13-a9a6-e011fa0a1ec8

Some used Boot-Repair and it worked, others had to do a full chroot.
[https://askubuntu.com/questions/1183951/grub-file-filters-not-found-after-ubuntu-19-10-upgrade](https://askubuntu.com/questions/1183951/grub-file-filters-not-found-after-ubuntu-19-10-upgrade)

UEFI full chroot:
chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.

---

### Post by Yippee38 on 2020-06-17
> **oldfred said:**
> You show 18.04 installed in UEFI boot mode to a gpt partitioned drive on sda.
But sdb & sdd are older MBR partitioned. Your sdc is gpt.

But you have old grub BIOS boot in MBR of sda, sdb & sdd. Those will never work and if you boot in BIOS mode you will not boot and will give grub errors.
You must always boot in UEFI boot mode.

Are you booting in UEFI mode?
I might just totally reinstall grub using Boot-Repair in UEFI boot mode.

Going back to your first response to me......

The grub BIOS /boot partitions in sda, sdb and sdd are old.  I just never removed them when I upgraded my system and switched over to a UEFI capable motherboard and larger disks.  So I'm not worried about those as I'm not trying to boot from those.

Do you think they are causing problems being there?

---

### Post by Yippee38 on 2020-06-17
> **oldfred said:**
> This error looks like you are booting in BIOS mode, as it is looking for an UUID that does not exist.


Your boot is on sda3:


Some used Boot-Repair and it worked, others had to do a full chroot.
[https://askubuntu.com/questions/1183951/grub-file-filters-not-found-after-ubuntu-19-10-upgrade](https://askubuntu.com/questions/1183951/grub-file-filters-not-found-after-ubuntu-19-10-upgrade)

UEFI full chroot:
chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.

The first link you included here led me, eventually, to this page:  [How can i reinstall GRUB to the EFI partition?]("https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition").  Following  the instructions in response #8, I was able to re-install GRUB and get my system booting again!  Of course, I had to change the drives to the appropriate designations (I entered sda1 for the EFI partition, sda3 for the / partition, and I skipped the /boot partition since I should be booting from the EFI paritition.  The steps listed also include installing grub to /sdb, but I had to use /sda.).

Thank you so much for your help!  I'm sorry that my knowledge is such that I needed so much help.

---

### Post by oldfred on 2020-06-17
You did good. 
A lot of new users do not understand drives & partitions in Linux and only think of "drives" in Windows that really are partitions.

---

