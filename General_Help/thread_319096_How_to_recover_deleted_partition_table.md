---
title: "How to recover deleted partition table?"
date: 2006-12-15
forum: General Help
---

### Post by ADCO on 2006-12-15
In the course of installing an Ubuntu 5.something, I had a series of #%$@ problems which ended up very badly.

(precision, I'm a nOOb but not absolutely dumb)

Ubuntu was utterly unable to run the X server once it got installed. Additionnally, the grub file wasn't created with any boot for windows, hence I lost the access to windows.
I tried to edit the menu.lst in grub but though I spent hours following various instructions, windows was never to be found again, leaving me with a broken ubuntu and no windows.

Then is the real problem. Desperate with this, I decided to try and at least get Windows back. I inserted my windows CD, got into recovery mode, fixmbr-ed the system, and... all my partitions are gone.

So basically, starting from a functional windows, I end up with having lost absolutely everything to a bugging Ubuntu install (and  a very nice windows recovery tool, too).
So I am looking into recovering those partitions (and then I can start dreaming about actually using them). Can an Ubuntu live do that? How?

(didn't find in the FAQS and all, only how to create a new grub to get existing partitions, not recover those not even recognized by the install CD anymore).

Thanks in advance anyone for helping save my data from this horrendous Ubuntu experience ;) .

---

### Post by capitalistpiglet on 2006-12-15
I think whats happened is you formatted the entire drive, in which case your not going to be able to get any of your data back. When you installed did you manually edit the partition table? if not then the installer would have formatted the entire drive. Also why are you trying to install such a old version of ubuntu?

---

### Post by xopher on 2006-12-15
> in which case your not going to be able to get any of your data back

This might not be the definitive answer. There is a small chance of even recovering the complete partition. Now if I only remembered what the program was called. I'll try to look it up, don't give up hope just yet. :rolleyes:

---

### Post by xopher on 2006-12-15
Allright, didn't take that long really :) I've had some good experiences with these two:

> TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table). Partition table recovery using TestDisk is really easy.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

and
> PhotoRec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (Photo Recovery) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it'll work even if your media's filesystem is severely damaged or formatted. PhotoRec is safe to use, it will never attempt to write to the drive or memory support you are about to recover lost data from.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Now we need a quick guide how to use them as efficient as possible..

EDIT:

Both are available from the ubuntu repositories.

---

### Post by capitalistpiglet on 2006-12-15
I wouldnt hold out much hope of recovering much data since as i see it what he has done is first formatting the drive and put ubuntu on it then reformatted and put windows back on it. Im not sure how much data he will be able to recover after all that. But i guess its worth a shot.

---

### Post by chrisfay on 2006-12-15
Before thrashing around a bit, I would first definatively find out what files are left on the drive. You could boot into your Windows recovery disk and get to a command prompt. From their you can see what files are left in your Win partition if any...

---

### Post by ADCO on 2006-12-15
Hehe, I am not stupid enough to have formatted my drive ;).
As I said, the steps I took were simply to try and override the grub by a windows-driven MBR.
As a consequence, I lost, all the partition table, but all the data is still there, in the exact same situation. Only the MBR doesn't know it's there anymore. I just need, as a first step before trying to install something again, or before getting my windows bootable again, to get something to recover these partitions.

Thanks a lot Xopher, I'll try testdisk, if it can be run from a bootable disk, or an usb key.
The ubuntu does not have such a functionnality from the bootable CD? or from the live version?

---

### Post by Sef on 2006-12-15
Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

