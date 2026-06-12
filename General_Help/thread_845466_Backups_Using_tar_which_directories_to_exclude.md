---
title: "Backups Using tar: which directories to exclude?"
date: 2008-06-30
forum: General Help
---

### Post by russlar on 2008-06-30
Hello all,

I'm trying to write a script to back up my system using tar, and I'm wondering which directories I should exclude. So far, I'm planning on excluding /dev, /mnt, /media, /proc, /etc/fstab, /sys, /var/run and /etc/acpi. The goal is to enable me to extract my tarball over a fresh install of gutsy, in case I blow up my system.

Am I missing any that would cause me problems if they overwrote a newer version?

---

### Post by chrisccoulson on 2008-06-30
> **russlar said:**
> Hello all,

I'm trying to write a script to back up my system using tar, and I'm wondering which directories I should exclude. So far, I'm planning on excluding /dev, /mnt, /media, /proc, /etc/fstab, /sys, /var/run and /etc/acpi. The goal is to enable me to extract my tarball over a fresh install of gutsy, in case I blow up my system.

Am I missing any that would cause me problems if they overwrote a newer version?

You've got it pretty much spot-on. I've used this method successfully several times (and restored a whole system using it), and I exclude any virtual or temporary filesystems. The ones I exclude are /dev, /proc, /sys, /tmp, /var/run and /var/lock. I also exclude /home from my tar backups, as I backup this using a separate regime.

You obviously have to remember to recreate these on a restored system though.

Why the need to exclude /etc/fstab, /etc/acpi, /mnt and /media though? /etc/fstab and /etc/acpi will both be useful when restoring from a backup. I would include /media and /mnt if they are empty at the time of backup, as it removes the risk of you forgetting to recreate these folders when you restore from it.

This is the guide I followed initially: [http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by russlar on 2008-06-30
> **chrisccoulson said:**
> Why the need to exclude /etc/fstab, /etc/acpi, /mnt and /media though?

Because I'll be doing my restore to a fresh install, which may (or may not) have different hardware and HDD configurations.

---

### Post by chrisccoulson on 2008-06-30
Thanks for the clarification. That definately makes sense for /etc/fstab, but I think /etc/acpi is common between machines using different hardware. I don't think any of the files are customized for different hardware. They all come from the acpi-support package (correct me if I'm wrong though)

---

### Post by russlar on 2008-07-01
ok, so I gave it a shot:

```
root@HAL-ubuntu:/# tar -cvvfjp sysbackup.tar.bz2 --exclude='/proc/*' --exclude='/sys/*' --exclude='/etc/fstab' --exclude='/media/*' --exclude='/dev/*' --exclude='/mnt/*' --exclude='/etc/grub.conf' --exclude='/var/run' --exclude='/2.5sata/*' --exclude='/home/rgillette/*' --exclude='/sysbackup.tar.bz2' /

```

I end up with a file called jp, and the last line of the very verbose output is something along the lines of Error: exited from previous errors.

Judging by the size of the jp file, it is the right size, but the wrong name. I'm using the -j and -p options to use bzip2 and keep permissions.

:confused:

---

### Post by cycloptivity on 2008-07-02
Your like me - as in stuffing up the tar options order; Try this '-cvvjpf'

---

### Post by chrisccoulson on 2008-07-02
Yes, the 'f' has to be the last option, because it takes 'sysbackup.tar.bz2' as a parameter I think. Hence why you ended up with an archive called 'jp' the first time.

---

### Post by russlar on 2008-07-02
Good call.

I wound up using rsync instead.

---

