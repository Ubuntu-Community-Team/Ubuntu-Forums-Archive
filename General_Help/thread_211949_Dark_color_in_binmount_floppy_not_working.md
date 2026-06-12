---
title: "Dark color in /bin/mount floppy not working"
date: 2006-07-09
forum: General Help
---

### Post by delta_charlie on 2006-07-09
Hi all, I just installed ubuntu-6.06-alternate-amd64.iso onto a new computer that has a Sempron 2600 AMD 64 CPU. It installed the generic amd64 Kernel. 

The computer was bought with no OS So I tested the floppy by booting an old Linux boot floppy. This makes me think the drive and BIOS are talking to each other and working ok.

If I try to Use Nautilus 2.14.1 and double click on Floppy I get:
Unable to mount the selected floppy drive.

Next I tried a terminal window and:
sudo -i mount -t msdos/dev/fd0 /mnt

This produces the error: /bin/mount: Cannot execute binary file.

I did find mount in the bin director but it was highlighted in a dark color. Don't know what that means.

Any ideas?

Thanks, DC

---

