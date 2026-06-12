---
title: "Installation Parameter"
date: 2013-01-04
forum: General Help
---

### Post by anon_private on 2013-01-04
Hi,

I am thinking of installing Lubuntu 12.10 to the HD.

I will select dual boot, but am unsure regarding the size of the partition that I will need.

I understand that Lubuntu 12.10 needs 4GB for an installation, but how much extra should I include for updates, etc? I do not download a lot.

Can the size of the partition be changed after  it is set?

A couple of other points.

If the installation goes wrong for some reason, can I simply repeat he process and the process will simply over-right existing files?

If I use GParted before installtion and note the existing partition, I assume that the extra partition will be for Lubuntu?

Thanks.

A

---

### Post by 2F4U on 2013-01-04
> I understand that Lubuntu 12.10 needs 4GB for an installation, but how  much extra should I include for updates, etc? I do not download a lot.

For a minimal root partition (/) I usually choose between 10GB and 20 GB. The size of /home depends on how much data you intend to store.

> If the installation goes wrong for some reason, can I simply repeat he  process and the process will simply over-right existing files?

Yes, you can repeate the process. I usually then manually choose the partitions to install on.

---

### Post by anon_private on 2013-01-05
> **2F4U said:**
> For a minimal root partition (/) I usually choose between 10GB and 20 GB. The size of /home depends on how much data you intend to store.



Yes, you can repeate the process. I usually then manually choose the partitions to install on.

Thanks for replying

Looks like quite a lot of space for root. I'll choose the average 15GB. Why is so much space needed?

I don't download a lot. I don't know what to choose so I'll select say 2GB. Can this be changed if necessary after install?

Best wishes.

A

---

### Post by Impavidus on 2013-01-05
You can squeeze it in about 6 GB, even less, but whenever you install a program or even an update the usage of the root partition will increase and when you run out of space, your system won't boot. You'd better be on the save side. Most of the data in your root partition is actually not part of the base system, but in data used by various applications (stored in /usr/share; for example, I have 1.6GB of flight simulator data in my root partition, which is about 7GB in total).

To give you some more useful advise, could you tell how much hard disk space you have available? Disk size + what your other OS is using. As you consider installing Lubuntu, I assume you don't have a high-end system.

It is possible to change the partitions later, but it's rather complicated and a bit risky, so it's best to get it right the first time.

---

### Post by anon_private on 2013-01-05
> **Impavidus said:**
> You can squeeze it in about 6 GB, even less, but whenever you install a program or even an update the usage of the root partition will increase and when you run out of space, your system won't boot. You'd better be on the save side. Most of the data in your root partition is actually not part of the base system, but in data used by various applications (stored in /usr/share; for example, I have 1.6GB of flight simulator data in my root partition, which is about 7GB in total).

To give you some more useful advise, could you tell how much hard disk space you have available? Disk size + what your other OS is using. As you consider installing Lubuntu, I assume you don't have a high-end system.

It is possible to change the partitions later, but it's rather complicated and a bit risky, so it's best to get it right the first time.


Thank you for responding.

I have 512MB of RAM installed at present, hence Vista is not running at present, but I intend to keep this OS in case I decide to use it.

Unused space (from GParted):

Dell Utility 47MiB
Recovery 4.39 GiB
OS 191 GiB

I will use the standard facility when installing Lubuntu, that is clicking on the install icon and following the instructions.

I understand that at some stage I will be given the option of connecting with my files (optional). Can you tell me what this means?

I should finish with a dual boot system.

Thanks

---

### Post by anon_private on 2013-01-08
As part of the install procedure I see two rectangles: Allocate drive space...

Which one is for Vista, and which is to be allocated to Lubuntu? I will opt for a dual boot system

I noted that the minimum one way appears to be about 20MB and about 30MG the other way.

Is the left box Vista or for Linux?

Thanks

---

