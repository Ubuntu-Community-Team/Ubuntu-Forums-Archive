---
title: "Bad magic number in super-block"
date: 2023-01-30
forum: General Help
---

### Post by caterhamfan on 2023-01-30
I am trying to run fsck on my root system however keep coming up with the error below. The super block can not be read due to a bad magic number.

Sorry, the pic is a bit fuzzy. 

How can I solve this?

Thank you

---

### Post by MAFoElffen on 2023-01-31
I found this answer: [https://www.linode.com/community/questions/20599/how-do-i-fix-a-bad-magic-number-in-super-block-error](https://www.linode.com/community/questions/20599/how-do-i-fix-a-bad-magic-number-in-super-block-error)

---

### Post by TheFu on 2023-01-31
> **MAFoElffen said:**
> I found this answer: [https://www.linode.com/community/questions/20599/how-do-i-fix-a-bad-magic-number-in-super-block-error](https://www.linode.com/community/questions/20599/how-do-i-fix-a-bad-magic-number-in-super-block-error)

Whoa!!!!!!!   That instructions will put a file system over the partition table, which is never a good idea.  Be 100% certain you understand the way that Linux specifies the whole drive and each partition and where file systems might be located (which could be neither of those).

I'll check the image, if it is local (not external website).

Ok, you should never run an fsck on anything other than the file system. DO NOT RUN IT on the entire drive device, /dev/sda.  In theory, nothing bad should happen. Thankfully, the command I saw wasn't being run with elevated privileges, so it wouldn't be allowed to harm anything.

If you boot into the Recovery console (advanced grub options), there should be a way to have the system run fsck against all file systems connected to the system.   Or you can boot from into a "Try Ubuntu" environment off any Ubuntu/Lubuntu/Kubuntu/whatever Desktop install ISO and run the fsck manually.  This is a common way to fix booting issues, since we cannot modify simple disk storage while it is mounted.  Booting from the ISO won't mount the installed file systems, so admin maintenance work can be performed.

Of course, if you had good backups, then in about 15 minutes, you'd be back up and running, assuming the root problem isn't a failing drive.

---

### Post by tea for one on 2023-01-31
Assuming that your file system is ext4, this info may help:-
[https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)
I know the instructions are old, I haven't been able to find a more recent tutorial.
You may need elevated (sudo) privileges now.

---

