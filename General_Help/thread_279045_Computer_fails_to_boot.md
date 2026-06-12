---
title: "Computer fails to boot"
date: 2006-10-14
forum: General Help
---

### Post by npang on 2006-10-14
Can a mod please move this thread to a more appropriate forum? It doesn't really belong in the sparc section


I had Kubuntu 6.10 installed on my computer and one day, it failed to boot. When I try to boot from the hard drive, it displays the error "Disk boot failure. Insert system disk and press enter". As it runs the power on self test, it takes 40 secs to detect the connected IDE drives, a HD and a DVD writer. I guessed that the master boot record failed on the HD.

I tried using my ever reliable knoppix 3.8.2 cd to fsck the partitions and reinstall grub. fsck reported no problems but I couldn't install grub onto the root partition. The following is the output from grub-install:
```
$ sudo grub-install /dev/hda1
Probing devices to guess bios drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```
I tried to grub-install two more times. The next time came with the same error message as previous. The third time had a new error message.
```
$ sudo grub-install /dev/hda1
Probing devices to guess bios drives. This may take a long time.
/dev/hda1 does not have any corresponding BIOS drive.

```

I tried the following as well:
```

$ sudo hexdump -n 512 -x /dev/hda
0000000 0000 0000 0000 0000 0000 0000 0000 0000
*
0000200

```

I tried reinstalling Kubuntu 6.10 with the text installer. I kept my /home partition intact and formatted and installed Kubuntu onto the root partion. Installation was fine and the installer said it managed to install grub successfully. When I rebooted, it had the insert system disk error. 

I booted knoppix again and mounted the HD partitions. I can modify data and I can create and remove new files in all the partions. I tried doing grub-install and hexdump again and the output was still the same.

Can someone please point me in the right direction to fix my problem? Thank you.

---

