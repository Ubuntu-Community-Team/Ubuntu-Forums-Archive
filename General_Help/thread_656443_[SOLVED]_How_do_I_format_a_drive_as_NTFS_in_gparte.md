---
title: "[SOLVED] How do I format a drive as NTFS in gparted?"
date: 2008-01-02
forum: General Help
---

### Post by mjpatey on 2008-01-02
I just installed gparted, and am attempting to format a drive as NTFS.  Not my choice of filesystems, but it's an external USB HD that will eventually be attached to a Windows machine.

When I tell gparted to create a new partition, it gives a drop-down list of possible filesystems, but NTFS is one of the greyed-out ones.

I know I've done this before in a previous Ubuntu install... is there a package I need in order for Gparted to be able to format an NTFS partition?

Thanks!

-Mark

---

### Post by tech9 on 2008-01-02
you could try formatting it as vfat... that way you can save windows and Linux files to the drive...

```
sudo mkfs.vfat /dev/"your partition"
```

---

### Post by Craigus on 2008-01-02
Gparted can create NTFS partitions. Have you tried with the Gparted live cd ?

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Rocket2DMn on 2008-01-02
This may sound blatantly obvious, but have you installed ntfs-3g and enabled read/write from Applications->System Tools->NTFS Configuration Tool?

---

### Post by mjpatey on 2008-01-02
Thanks for all the responses!

After posting, I went into Synaptic and searched for "NTFS"... Gutsy does have basic NTFS support installed by default, but one utility wasn't included:  "ntfsprogs".  Its description in Synaptic said it provides the ability to format in NTFS, though no mention was made of integration with gparted.

Well, after installing ntfsprogs, I closed and re-opened gparted, and voila!  NTFS format is selectable in the GUI.  I have now formatted the partition, and have a brand-spanking-new 500GB NTFS removable USB drive for my wife to bring to work.

Thread marked as solved!

Thanks, everyone.

-Mark

---

### Post by Craigus on 2008-01-02
> but one utility wasn't included: "ntfsprogs"

That's very odd. Gparted only uses ntfsprogs, not ntfs-3g, and ntfsprogs is supposed to be there by default.

---

### Post by mjpatey on 2008-01-02
I installed gparted from Synaptic, and it didn't include ntfsprogs.  NTFS-3G seems to have been included in my Gutsy install by default, though.  I remember installing it manually in Feisty, but it looks like my fresh Gutsy install had it built-in.

-Mark

---

### Post by tech9 on 2008-01-02
> **mjpatey said:**
> Thanks for all the responses!

After posting, I went into Synaptic and searched for "NTFS"... Gutsy does have basic NTFS support installed by default, but one utility wasn't included:  "ntfsprogs".  Its description in Synaptic said it provides the ability to format in NTFS, though no mention was made of integration with gparted.

Well, after installing ntfsprogs, I closed and re-opened gparted, and voila!  NTFS format is selectable in the GUI.  I have now formatted the partition, and have a brand-spanking-new 500GB NTFS removable USB drive for my wife to bring to work.

Thread marked as solved!

Thanks, everyone.

-Mark

your welcome! :)

yeah, the NTFS tool is not installed by default in Gutsy.
also if you popped in the command that I posted earlier, that would be way faster.

---

### Post by Craigus on 2008-01-02
> I installed gparted from Synaptic

Stranger and stranger. Gparted is supposed to be there by default as well.

---

### Post by mjpatey on 2008-01-02
> **tech9 said:**
> your welcome! :)

yeah, the NTFS tool is not installed by default in Gutsy.
also if you popped in the command that I posted earlier, that would be way faster.

Yeah, it would have been quicker... but my wife's work people asked me to format it as NTFS.  Not my place to argue with them, unfortunately.

Thanks, just the same!

-Mark

---

### Post by mjpatey on 2008-01-02
> **Craigus said:**
> Stranger and stranger. Gparted is supposed to be there by default as well.

Nope, it wasn't.  :-)  Easy enought to install, though!

-M.

---

