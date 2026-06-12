---
title: "How do YOU mount your hard drive partitions in fstab?"
date: 2007-10-31
forum: General Help
---

### Post by matthias_k on 2007-10-31
Just wondering, are you mounting them by UUID or directly by device node name?

Because, for me, either way DOES NOT WORK. When mounting by UUID, every once in a while Ubuntu will hang on boot with a libata failure because /dev/disk/by-uuid does not exist and the UUID of the root partition can't be resolved.

On the other hand, mounting via device node names (e.g. /dev/sda1) does not work either, because this friggin piece of bull poo called libata does not mount devices in a deterministic order, which means that SOMETIMES my root device is /dev/sda1 and SOMETIMES it's /dev/sdb1 (which will obviously break any mount points defined in fstab).

So, am I the only one having these problems or what?

---

### Post by nowshining on 2007-10-31
ahh remove the 1 as I think sda1 is ur SWAP and it won't mount. so it would be /dev/sda
:)

---

### Post by matthias_k on 2007-10-31
Err, no. The number indicates the partition on the device referenced by /dev/sda. So /dev/sda1 is the first partition on whatever device /dev/sda is pointing to.

---

### Post by nowshining on 2007-10-31
did u try /dev/sda

??

---

### Post by matthias_k on 2007-10-31
> **nowshining said:**
> did u try /dev/sda

??
Listen kid, I really appreciate that you're trying to help me, but why don't you read up on Linux basics before trying to answer someone's post. Your answers show that you have absolutely no clue about how devices are handled in Linux.

---

### Post by nowshining on 2007-10-31
so an insult from u - IF U KNOW HOW LINUX WORKS THAT MUCH WHY NOT JUMP OUT OF HERE AND FIX IT URSELF IN THE SOURCE - MR. SMARTY PANTS.. :/

---

### Post by mdurham on 2007-10-31
I use the LABEL and have no problems, the UUID is too confusing for me

---

### Post by Subban on 2007-10-31
Mounted as UUID's here for two HD's /dev/sda and /dev/sdb and a third HD on /dev/hdd is mounted as named path /dev/hdd. The dvdrw is referenced and mounted with /dev/hdc.

As you can see I'm using both methods with two devices each and for me its behaving ok, so far :]

---

### Post by matthias_k on 2007-10-31
That's interesting, and pretty odd as well %-)

I didn't try to mount via labels, maybe I'll give that a shot. But it's still weird that sometimes the UUID symlinks are broken/do not exist at boot time. That looks like a bug to me. The report I filed does not receive much attention unfortunately.

Maybe I should try asking someone on the libata mailing list or file a bug against libata? The point is, I'm not exactly sure where the issue stems from, whether it's a kernel problem, a Ubuntu problem or a problem with libata in particular.

---

### Post by pointone on 2007-10-31
You could try mounting by path... check /dev/disk/by-path.

---

### Post by Rinzwind on 2007-10-31
> **matthias_k said:**
> That's interesting, and pretty odd as well %-)

I didn't try to mount via labels, maybe I'll give that a shot. But it's still weird that sometimes the UUID symlinks are broken/do not exist at boot time. That looks like a bug to me. The report I filed does not receive much attention unfortunately.

Maybe I should try asking someone on the libata mailing list or file a bug against libata? The point is, I'm not exactly sure where the issue stems from, whether it's a kernel problem, a Ubuntu problem or a problem with libata in particular.

Can it be that 1 of your drives sometimes comes up to slow and you've received your devicenames in the wrong order? I think I heard about something like that being a problem a couple of months ago BUT I am a n00b when it comes to debugging /etc/fstab ;) so don't blame me if this comment is wrong.

---

### Post by matthias_k on 2007-10-31
> matthias:~$ ls /dev/disk/by-path/
total 0
0 pci-0000:00:1f.1-scsi-0:0:0:0        0 pci-0000:00:1f.1-scsi-0:0:0:0-part3  0 pci-0000:00:1f.1-scsi-0:0:1:0
0 pci-0000:00:1f.1-scsi-0:0:0:0-part1  0 pci-0000:00:1f.1-scsi-0:0:0:0-part4
0 pci-0000:00:1f.1-scsi-0:0:0:0-part2  0 pci-0000:00:1f.1-scsi-0:0:0:0-part5

That looks pretty scary (this is taken from my notebook though, where I don't have this problem -- I'm at work right now). How do I figure out what's my root partition for example?

---

### Post by matthias_k on 2007-10-31
> **Rinzwind said:**
> Can it be that 1 of your drives sometimes comes up to slow and you've received your devicenames in the wrong order? I think I heard about something like that being a problem a couple of months ago BUT I am a n00b when it comes to debugging /etc/fstab ;) so don't blame me if this comment is wrong.

Interesting thought. Possible, but I'm not sure. How would I check if a disk awakes very slowly?

Another thing that may be "unusual" (compared to a typical setup that is) is that I have a second PCI IDE controller card for my third hard drive. I'm not sure how libata takes devices into account that are primary master on a second controller. Maybe that is the problem?

---

### Post by matthias_k on 2007-10-31
(on a second thought, it worked flawlessly with 7.04, so I doubt that's the problem)

---

### Post by goudaman on 2008-03-03
Hi there!

just a question if you resolved your problem...
as I have a similar prob with currently 8 HDs though.... 4 on the motherboards SATA, 2 on a PCIe eSata and 2 on a PCI SATA... 

every once in a while it busts up the "normal" order and all mount points are #$%ed.

Cheers
Chris

---

