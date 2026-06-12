---
title: "Usable to sync mount error"
date: 2019-05-22
forum: General Help
---

### Post by tommy2k10 on 2019-05-22
I have a problem with my test machine (fortunately it is not my main one!). It only started happening after I did an in-house upgrade to Ubuntu 19.04.
From the Grub menu, I choose Ubuntu, and then I get:

Kernel Panic -not syncing: VFS: Unable to mount root fs on unkown-block(0,0)
CPU 0 PID 1 Comm Swapper/0#16-1-10 ubuntu
Hardware name: System manufacturer: System Product Name/M5A70L-MU/SB3 BIOS 1801 11/12/2013.

Call Trace:

dump stack+0x63/0x8a
panic+0x101/0x2a7
mount_block_root+0x238/0x2df
? do_early_param+0x95/0x95
mount_root+0x38/0x3a
prepare_namespace+0x139/0x18e
kermel_init_freeable+0x23c/0x262
? rest_init+0xb0/0xb0
kernet_init+0xe/0x100
ret_from_fork+0x22/0x40

Kernel Offset 0x14000000 from 0xfffffff81000000: relocation range 0xffffffff800000000-0xffffffffbffffff)
end Kernel Panic -not syncing: VFS: Unable to mount root fs on unkown-block(0,0)

I have tried Boot Repair to no avail
Strangely enough I cannot get in via a Live CD as when plugged in via USB, the computer turns itself off.
No change if the PSU is changed.

---

### Post by TheFu on 2019-05-22
What about a flash drive "Live UBuntu" environment? Does that work?

Initially, I was thinking a bad HDD, but if the CD doesn't work too (and it used to), then I'm thinking disk controller or motherboard.  It could also be another hardware issue like a bad GPU.  Really need to boot using alternate media, like a flash drive with an Ubuntu desktop on it, to see.

Changing the PSU was a good guess too.

---

### Post by tommy2k10 on 2019-05-23
I hadn't tried that! I will, and get back to you.

---

### Post by tommy2k10 on 2019-05-23
All this is very strange - I put Ubuntu on a USB flash drive and tried it from one of the ports on the back of my test machine, and it booted fine. However, the machine did turn itself off, so I had to do it a second time.
Strange partition structure in Disk Utility though - Extended Partition - Partition 2 249GB, /dev/sda2, Partition 5, 249GB LUKS, Linux, LUKS Encryption Version 1.
Then when I ran sudo fsck -f /dev/sda2, I got "fsck from util-linux 2.32 e2fsck 1.44.4 (18-Aug-2018) fsck.ext2 Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 Could this be a zero=;ength partition?
And then I ran sudo fsck -f /dev/sda5, all I get it "fsck from until-linux 2.32" and nothing else.
I also noticed the clock says 09.51 instead of 10.51 (the time I am writing this!)

---

### Post by dino99 on 2019-05-23
Have you checked the system with fsck from grub recovery ?
Also clean the system via clean/autoclean/autoremove/gtkorphan

---

### Post by tommy2k10 on 2019-05-23
Even grub recovery comes up with that error message as well!

---

### Post by tommy2k10 on 2019-05-23
> **dino99 said:**
> Have you checked the system with fsck from grub recovery ?
Also clean the system via clean/autoclean/autoremove/gtkorphan

How do I do that?

---

### Post by TheFu on 2019-05-23
> **tommy2k10 said:**
> All this is very strange - I put Ubuntu on a USB flash drive and tried it from one of the ports on the back of my test machine, and it booted fine. However, the machine did turn itself off, so I had to do it a second time.
Strange partition structure in Disk Utility though - Extended Partition - Partition 2 249GB, /dev/sda2, Partition 5, 249GB LUKS, Linux, LUKS Encryption Version 1.
Then when I ran sudo fsck -f /dev/sda2, I got "fsck from util-linux 2.32 e2fsck 1.44.4 (18-Aug-2018) fsck.ext2 Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 Could this be a zero=;ength partition?
And then I ran sudo fsck -f /dev/sda5, all I get it "fsck from until-linux 2.32" and nothing else.
I also noticed the clock says 09.51 instead of 10.51 (the time I am writing this!)

Assuming I'm reading your interpretation of the partitions correctly, it seems to be a whole drive encryption install.  You can't access anything inside sda5 until it gets "opened" using **cryptsetup** and LVM. Tell it to scan inside the unlocked encrypted container for VGs and LVs, **sudo vgscan -y**  If you boot from a USB flash drive - perhaps a Mate Desktop, then I'm positive you can gain access to the encrypted storage and LVM volumes, assuming you know the passphrase to unlock the encrypted areas. I've done this more than a few times.  Think I might have needed to install lvm and cryptsetup into the temporary environment after each reboot.

Update - **sudo vgscan -ya** is needed above to activate found VGs.

Until the LVs are seen post-LUKS decryption, you cannot fsck those volumes.

Please don't describe the command output. Run the commands and copy/paste both the exact command AND the output here.  We are used to seeing console output.  Also, whenever posting commands+output, please use "_code tags_" so all the columns line up. Basically, it should look identical here as it does in a terminal, without coloring.  That's in the AdvReply or GoAdvanced editor - use the # button like you would the "quote-tags"

If you can't copy/paste the output, redirect it to a file, then sneaker-net the file to another system where you can post using copy/paste.

A clock being off could easily just be the TZ variable isn't set correctly or isn't doing DST.

Tiny typos are killing my ability to help.

BTW, I'm fairly familiar with LUKS encryption. Been using it about 5 yrs now.  If you aren't intentionally using encrypted storage, then get your data out ASAP and reinstall without that overhead.  Also, encrypted storage has all sorts of liabilities, so be certain you have backups working perfectly, every time and know that you can restore from those backups.

If you need more detailed help, ask. But I'll need lots of commands to be run first.

---

### Post by tommy2k10 on 2019-05-28
I can see the data after I went to Files, clicked on the Encrypted drive and entered my password.

This is the output I got when I ran ```
sudo -vgscan -y
```:

```
Reading volume groups from cache.
Found volume group "ubuntu-vg" using metadata type lvm2.
```

---

### Post by TheFu on 2019-05-28
-vgscan?  I'd be surprised if that command was found.
[B]
sudo vgscan -ay[/B]
Might want to check the manpage for the command.

---

### Post by tommy2k10 on 2019-05-28
Sorry, it was the way I copied it out!

I did put```
sudo vgscan -y
```

---

### Post by TheFu on 2019-05-28
Need the --activate option - Sorry.  Best to always check the manpage, since we all make mistakes.

---

