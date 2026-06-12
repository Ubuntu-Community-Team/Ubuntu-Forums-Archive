---
title: "[SOLVED] Persistence not working on Live USB"
date: 2013-03-09
forum: General Help
---

### Post by JLeon85 on 2013-03-09
This is really frustrating. I've been trying to make a persistent USB of either Ubuntu or Lubuntu. I've tried Unetbootin on both Lubuntu and Win 8, as well as Live USB Creator on Win 8. It keeps appearing to burn the USB properly, but when I try to boot it just turns out to be a regular live USB. I've also tried three different USB drives to rule out any problem there. Does anyone have any suggestions? I've already wasted a lot of time on this, but I'm determined to get this to work. 

Thanks for any help.

---

### Post by dcstar on 2013-03-10
Why do you think the persistence does not work?

---

### Post by JLeon85 on 2013-03-10
> **dcstar said:**
> Why do you think the persistence does not work?

That's my question.

---

### Post by ManamiVixen on 2013-03-10
Here's an easy test to see is persistance is working. Boot using the live USB and connect to the internet. Then download a small file, like .jpg or something and put it in the home folder. Then reboot. If the file is still ther after reboot, persistance is fine. But of course if it isn't, there is an issue.

---

### Post by black veils on 2013-03-10
did you remember to choose the persistent space?

---

### Post by C.S.Cameron on 2013-03-10
Plug the flash drive into a running PC,
Do you see a file named casper-rw?
If not, persistence is not set up properly.

Following is how to **manually** make a Persistent install to flash drive:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
Enter the syslinux directory, (or for UNetbootin the root directory).
Make the syslinux.cfg file writeable
Replace the contents of the file syslinux.cfg with:

```

    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---

### Post by JLeon85 on 2013-03-10
Wow, thanks, those were amazing instructions, and I finally got it to  work! Also, thanks for that extra advice to get rid of the language and  install pop-up, that is a really nice touch. 

 I think I may have discovered what the problem was, but it is really  strange. When I first started following your instructions, I got an  error message saying it couldn't move syslinux from the drive. After a  little investigating, I found that files from the hidden trash folder on  the drive were automatically getting restored during the installation  process and those were blocking the new installation. These are files  from a previous installation of Puppy, so I'm not sure if it's a  problem exclusive to that. I'm also not sure how this could have affected three USB drives, two of which never had Puppy on them. Anyway, I had to log in as root to  permanently delete them, and then everything else went perfectly.


Thanks again!
:guitar:

---

