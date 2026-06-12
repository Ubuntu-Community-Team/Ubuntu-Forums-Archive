---
title: "How to list installed packages on a non-running system?"
date: 2013-02-04
forum: General Help
---

### Post by jkounis on 2013-02-04
I have an Ubuntu 10.10 system that crashed due to file system corruption. I have several backups, but the most recent backups have the corrupted files. I cannot simply restore the backup and run from the last backup because the system won't boot.

Since version 10.10 is old and unsupported anyway, I rebuilt the system starting with a fresh 12.10 install. Fortunately, all my data files were backed up and I didn't lose anything. 

However, I am having a hard time recreating the list of installed packages. I know the command "dpkg --get-selections" will list them on a running system.

I believe the answer is to look at /var/lib/apt/extended_states and /var/lib/aptitude/pkgstates. It seems that the union of these two files comprises a list of everything that was installed with either aptitude or apt. Is this assumption correct?

---

### Post by papibe on 2013-02-04
Hi jkounis.

If the partitions are yet mountable, i.e. not that corrupted, you could mount them, bind them, and then do a chroot. Then you can the selections.

Take a look at the procedure [here]("https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot"). That tutorial is to repair/reinstall grub, but it's the same idea.

Just s thought. Let us know how it goes.
Regards.

---

### Post by jkounis on 2013-02-04
> **papibe said:**
> Hi jkounis.

If the partitions are yet mountable, i.e. not that corrupted, you could mount them, bind them, and then do a chroot. Then you can the selections.

Take a look at the procedure [here]("https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot"). That tutorial is to repair/reinstall grub, but it's the same idea.

Just s thought. Let us know how it goes.
Regards.

Thank you! It was a great idea. I hadn't considered using chroot.

It worked excellently and just took a few seconds. It was much easier than trying to sort through /var/lib/apt/extended_states and /var/lib/aptitude/pkgstates.

---

### Post by jkounis on 2013-02-04
UPDATE: This turns out to be a handy way of restoring other parts of the system, like listing out the installed Apache modules with apachectl, installed perl modules with instmodsh, and installed PECL and PEAR modules, etc.

---

### Post by papibe on 2013-02-04
:D Glad you worked it out.

---

