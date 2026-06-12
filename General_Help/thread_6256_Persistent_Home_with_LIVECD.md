---
title: "Persistent Home with LIVECD"
date: 2004-11-26
forum: General Help
---

### Post by bshea on 2004-11-26
I have figured out how to get the networking going (and continue to load windows) by keeping/changing the hostname back to 'ubuntu' from 'macaroni' but my question (which doesn't seem to have an answer on forums yet is:)

How do you create and save a persistent home (as mentioned at bootup) on a vfat (or possibly an NTFS disk?) I fig that the NTFS may be a bit much to ask for but how about a configuration save (or home dir save ) to vfat or simply a ext3 floppy? Is this really available???? If not, then why mentioned at boot up (grub) menu?

Sincerely waiting for answer...


B Shea

---

### Post by eco2geek on 2004-12-31
**Experiment 1:** Persistent home on existing ext3 partition

hda3 is an existing, ext3-formatted partition. A 100MB, ext2-formatted loopback image was created at the root prompt (#):
# mount /mnt/hda3 -o rw
# dd of=/mnt/hda3/morphix.img if=/dev/zero bs=1M count=100
# mke2fs -j /mnt/hda3/morphix.img

(Why "morphix.img"? Because the Ubuntu Live CD is based on [Morphix](http://www.morphix.org/).)

Test-mount the image:
# mount /mnt/hda3/morphix.img /mnt/test -o loop
# cd /mnt/test
# ls -la

Then the live CD was rebooted, and the loopback image was mounted as persistent home by pressing <Tab> to go to the GRUB command line, and entering "home=/dev/hda3/morphix.img".

Result: Works, with both the Ubuntu Live CD and [Gnoppix Live CD](http://www.gnoppix.org/).

**Experiment 2:** Same thing on a FAT32-formatted USB thumbdrive

Result: Failed. The loopback image was created just fine, but both Gnoppix and Ubuntu Live CDs complain about the FAT32 format of the thumbdrive when using "home=/dev/sda1/morphix.img" or "home/dev/sda1". Possible solution: Format the entire thumbdrive as ext2 or ext3.

**Experiment 3:** Format thumbdrive as ext2 and use the whole thing as persistent home. (**Warning: If you do this, the contents of the thumbdrive will be erased, and the contents will not be visible to Windows.**)

# umount /mnt/sda1
# mke2fs /dev/sda1

Then, reboot the live CD and use the code "home=/dev/sda1" at the GRUB prompt.

Result: Failed. The format succeeded, but the live CD evidently wants a loopback image to use.

**Experiment 4:** Copy over the "morphix.img" created in Experiment 1 to the thumbdrive and use it as persistent home.

# mount /mnt/hda3
# cp /mnt/hda3/morphix.img /mnt/sda1

Then, reboot the live CD and use the code "home=/dev/sda1/morphix.img" at the GRUB prompt.

Result: Succeeded.

**Conclusion:** If you want to use a persistent home on a USB thumbdrive/key/etc. with the Ubuntu live CD, format it as ext2, then create an ext2-formatted loopback image on it (call it "morphix.img" for sake of argument), and use the code "home=/dev/sda1/morphix.img" at the GRUB prompt.

---

