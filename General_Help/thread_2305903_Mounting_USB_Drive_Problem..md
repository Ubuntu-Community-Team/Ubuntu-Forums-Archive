---
title: "Mounting USB Drive Problem."
date: 2015-12-10
forum: General Help
---

### Post by jimford on 2015-12-10
I corrupted my Xubuntu system and have installed another on a different partition, with the intention of transferring my original home directory to the new system.

The original partition shows up on the desktop on the new system, but as my home directory is encrypted I can't access it directly. If I run the command <ecryptfs-mount-private> to access the directory, I get the message that it wasn't set up correctly.

I can get into the corrupted system, but the desktop doesn't work properly - but I can run a terminal and access the encrypted files.

I want to plug in a USB HD and copy the files from my home directory, so I can reboot to my new system and transfer the files - messy, but it ought to work.

The problems is that I can't mount the HD in the 'normal' way. It isn't mounted automatically and dmesg shows it as USB 2-2, rather than (say) /dev/sdb which I could cope with.

So, how do I mount a USB drive that's recognised as USB 2-2, please? Or better still can I un-encrypt my home directory? 

Jim

---

### Post by matt_symes on 2015-12-10
Hi

Let's look at mounting the pen stick first.

Boot into your old installation.

Open a terminal and type

```
tail -f /var/log/syslog
```

Plug in the USB pen drive and wait 10 seconds.

Post the text that appeared in  the terminal into your next post.

Kind regards

---

### Post by jimford on 2015-12-12
Thanks for the reply,Matt.

Yes, the USB drive showed as having been recognised in syslog. (I've got used to checking dmesg instead of the syslog, so had overlooked it).

I couldn't mount the drive because it was exfat, in spite of the fact that exfat drivers should have been on the system.

In the end, I gave up on that approach and pruned unnecessary stuff from my encrypted home directory, and copied it to a another in an unencrypted place on the FS. I was then able to boot the functional OS and retrieve the files from the mounted old FS.

Thanks again for your help.

Jim

---

