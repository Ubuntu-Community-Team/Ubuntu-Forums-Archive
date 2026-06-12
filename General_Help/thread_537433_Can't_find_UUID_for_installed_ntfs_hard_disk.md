---
title: "Can't find UUID for installed ntfs hard disk"
date: 2007-08-28
forum: General Help
---

### Post by Rizlaw on 2007-08-28
I just installed a Maxtor 300GB ntfs formatted hard disk into my Ubuntu 7.04 system. It will be used by Ubuntu and a VMware XP virtual machine for keeping backups.

I connected the drive to my motherboard's (Asus A8N-SLI Deluxe) Silicon Image Raid Controller (on the SATA1 port) and set it up as a simple JBOD disk. Four other SATA drives are connected to the motherboard's primary controller (sda, sdb, sdc and sdd)

The command "sudo fdisk -l" shows that the drive is seen by Ubuntu as "/dev/sde", however, when I look in the **/dev/disk/by-uuid** folder I do not find the new drive's UUID number.

At the moment I have the drive mounted as **/dev/sde     /media/Max300**, but I would prefer to use "UUID=" in place of "/dev/sde".

Is there something about drives connected to a raid controller that prevents Linux from generating a UUID?

Thanks for any help.

---

### Post by merlinus on 2007-08-28
You might try;

```

blkid

```

-merlin

---

### Post by Rizlaw on 2007-08-28
> **merlinus said:**
> You might try;

```

blkid

```

-merlin

Thanks, but that just tells me that /dev/sde is Type="ntfs".

---

### Post by logos34 on 2007-08-28
cancel

---

### Post by logos34 on 2007-08-28
> **Rizlaw said:**
> I just installed a Maxtor 300GB ntfs formatted hard disk into my Ubuntu 7.04 system. 

...

The command "sudo fdisk -l" shows that the drive is seen by Ubuntu as "/dev/sde", however, when I look in the **/dev/disk/by-uuid** folder I do not find the new drive's UUID number.

At the moment I have the drive mounted as **/dev/sde     /media/Max300**, but I would prefer to use "UUID=" in place of "/dev/sde".

Format it as one big ntfs (or other fs) primary partition so you have 'sde**[COLOR="Red"]1[/COLOR]**', then mount it and check /dev/disk/by-uuid

---

### Post by Rizlaw on 2007-08-28
> **logos34 said:**
> Format it as one big ntfs (or other fs) primary partition so you have 'sde**[COLOR="Red"]1[/COLOR]**', then mount it and check /dev/disk/by-uuid

Sorry, I forgot to add "1" after "sde". I have already done all you mentioned and there is no UUID for the mounted /dev/sde1 device. The drive is formatted as one ntfs partition.

---

### Post by merlinus on 2007-08-29
As originally suggested by logos34:

ls -l /dev/disk/by-uuid

may work.

-merlin

---

### Post by dasunst3r on 2007-08-29
Try issuing the command *sudo vol_id /dev/sde1*.

---

### Post by logos34 on 2007-08-29
> **merlinus said:**
> As originally suggested by logos34:

ls -l /dev/disk/by-uuid

may work.

-merlin

Yeah, I retracted that after I saw he had already checked the folder. Unless he overlooked it.

By the way, does anyone know how to generate a new uuid for a partition?  I looked in the man pages for uuidgen and uuid_generate but could find no real help or usage examples.

---

### Post by logos34 on 2007-08-29
Hopefully the command 'sudo vol_id /dev/sde1' posted by dasunst3r will work.  

Unless the JBOD array is causing some problem.

Apparently to manually generate a UUID you just do 

**uuidgen -t **(time-based)
**uuidgen -r** (random)

Or maybe you use a web-based generator like this[ one here]("http://kruithof.xs4all.nl/uuid/uuidgen")?

To manually assign it to a device I guess you just create a device-block symlink in /dev/disk/by-uuid pointing to /dev/<partition>.  

hmm...curious about this. (i've never really bothered to look into it because frankly I hate uuids and avoid them whenvever possible!)

---

### Post by dasunst3r on 2007-08-29
> **logos34 said:**
> To manually assign it to a device I guess you just create a device-block symlink in /dev/disk/by-uuid pointing to /dev/<partition>.  

hmm...curious about this. (i've never really bothered to look into it because frankly I hate uuids and avoid them whenvever possible!)I think the purpose of UUIDs is to separate the device nodes from the device points.  The benefit of this would come on a server with a boatload of drive slots.  With the classical method, if you insert the drive into the wrong slot and you could get some pretty unpleasant surprises, yes?  On the other hand, with UUIDs, you can just shove the drive into any slot and achieve the same result.

---

### Post by Rizlaw on 2007-08-29
Thanks Merlinus, logos34 and dasunst3r for all your help and suggestions.

However, I decided to give up on using my Asus motherboard's Sil Raid Controller as a JBOD device. What I needed was 4 additional non-raid SATA ports, and I totally forgot that I had a new Promise controller card that provided that solution in my collection of PCI cards.

I pulled out my Promise SATA-300-TX4 controller card, installed it and Ubuntu 7.04 automatically recognized it and saw the problem hard disk drive on port 1. I now see the UUID for the drive and all is well in the land of Linux.

Thanks again.:)

---

