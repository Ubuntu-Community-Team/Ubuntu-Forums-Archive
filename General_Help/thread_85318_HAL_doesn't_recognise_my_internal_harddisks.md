---
title: "HAL doesn't recognise my internal harddisks?"
date: 2005-11-02
forum: General Help
---

### Post by jpetso on 2005-11-02
Hi all,

as a fresh convert from Gentoo, I already got a problem that I need help with and can't find reasonable documentation or previous cases for it.

When I installed Kubuntu (Breezy), I told the partitioner to mount the partitions of my internal hard disk at /media/partitionname. Maybe this is the reason, maybe not, the fact is that the media:/ kioslave (also known as "Storage Media") doesn't show those disks, which is kind of uncomfortable. Removable media, like USB sticks, external hard disks or CDs are shown there.

I think that HAL doesn't recognize these partitions, so media:/ doesn't know about them. They are mounted nevertheless, but I guess this is because they've got an appropriate entry in /etc/fstab. I later tried to move the mountpoints out of /media and into /mnt, but that didn't help either.

I don't know how all this stuff is handled in Kubuntu, and documentation is, well, non-existant. I had 2 other Kubuntu installs last week, and both of them showed the internal partitions in media:/. What am I doing wrong? How to fix this? ...help?

Thanks in advance,
  Jakob

---

### Post by !nkubus on 2005-11-02
media:// is Broked in Breezy right after the first update...

i'm still waiting an update to fix that :(

---

