---
title: "Mount NTFS at boot instead of after clicking it in Places"
date: 2008-05-02
forum: General Help
---

### Post by Bastaard on 2008-05-02
I got 1 NTFS partition (blkid output):

```
/dev/sda6: UUID="68787497787465AA" LABEL="Archivos" TYPE="ntfs"
```

Which mounts perfectly well when I click Places->Archivos (mount output):
```

/dev/sda6 on /media/Archivos type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
```

However, I want this partition to mount (read/write) at boot instead of having to mount it by clicking it in Places (I have to click it another time to actually open it up in Nautilus). Tried adding the following to /etc/fstab, but without result:

```
/dev/sda6 /media/Archivos fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096
```

Any help would be greatly appreciated!

---

### Post by TeoBigusGeekus on 2008-05-02
Go to Synaptic and install ntfs-config.
Then go to Applications->System Tools->Ntfs configuration.
Choose your volume and check all boxes...

---

### Post by Bastaard on 2008-05-02
> **TeoBigusGeekus said:**
> Go to Synaptic and install ntfs-config.
Then go to Applications->System Tools->Ntfs configuration.
Choose your volume and check all boxes...

Isn't there an easier way to do it, without installing extra software? And is this the standard behaviour of NTFS partitions in Ubuntu Hardy or does it mount at boot for other people?

---

### Post by adityakavoor on 2008-05-02
edit your fstab

---

### Post by TeoBigusGeekus on 2008-05-02
> **Bastaard said:**
> Isn't there an easier way to do it, without installing extra software? And is this the standard behaviour of NTFS partitions in Ubuntu Hardy or does it mount at boot for other people?
That's the standard behaviour in Hardy as well as in Gutsy. You could edit your fstab as mentioned above, but that's the hard way of doing it...

---

### Post by Bastaard on 2008-05-04
This worked, thanks!

---

