---
title: "Xubuntu quantal: all fs's read-only after suspend/resume"
date: 2012-12-18
forum: General Help
---

### Post by billd42 on 2012-12-18
I'm running Xubuntu Quantal with kernel 3.5.0-19-generic.  The machine is a home-built one, based around an ASRock motherboard.  I use ext4 for all the filesystems on it.

Sometimes when I wake the machine from suspend, all the file systems are mounted read-only.  Magic Alt-SysRq key seems to be the only way to reboot the machine.

Then, when I try to reboot, the BIOS screen doesn't list the drive as present.  I have to power-cycle the box and then the drive comes back, every time.  This is the only time the BIOS screen doesn't show the drive.  If I reboot the machine at any other time, or cold-boot it from the power-off state, it's fine.

I've run SMART tests on the drive and those show no issues.  There's nothing in the system logfiles, because the kernel can't write to them because they're mounted read-only.

This is ONLY since doing a clean install of Quantal; previously I was running Precise on this hardware for about six months and did not have these issues.

Any ideas for what I can look at? Thanks.

---

### Post by Bashing-om on 2012-12-18
billd42; Hi !

If I were (and have been in similar) in this situation, I would run some file system check/repairs.
```
sudo fdisk -l
``` to identify the disk/partitions.
then:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```#if errors: -y auto answers yes for fixes needing response ==> see man e2fsck for sure !
```
sudo e2fsck -f -y -v /dev/sdb1
``` (oldfred's)[INDENT]let us know how it goes <== BDQ

[/INDENT]

---

### Post by Pjotr123 on 2012-12-18
Suspend on your machine may need this workaround:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)

Or consider switching back to 12.04 LTS, which is better anyway (being LTS):
[https://sites.google.com/site/easylinuxtipsproject/version](https://sites.google.com/site/easylinuxtipsproject/version)

Good luck! :)

---

### Post by billd42 on 2013-01-01
> **Bashing-om said:**
> billd42; Hi !
If I were (and have been in similar) in this situation, I would run some file system check/repairs.

Ran both of those fsck commands and they turned up no errors.

---

### Post by billd42 on 2013-01-01
> **Pjotr123 said:**
> Suspend on your machine may need this workaround:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)

Or consider switching back to 12.04 LTS, which is better anyway (being LTS):
[https://sites.google.com/site/easylinuxtipsproject/version](https://sites.google.com/site/easylinuxtipsproject/version)

Good luck! :)

Neither of those is what I would call a "fix".  The first one amounts to "If suspend doesn't work, just disable it."  That's like "The windshield wipers in my car don't work so my mechanic told me not to drive in the rain."

Going back to the last version isn't a "fix" either.

---

