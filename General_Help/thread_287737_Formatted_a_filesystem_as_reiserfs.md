---
title: "Formatted a filesystem as reiserfs"
date: 2006-10-29
forum: General Help
---

### Post by ehird on 2006-10-29
Formatted my files partition as reiserfs - it contains tiny mp3 files (3mb) to episodes of tv shows (200mb+), so I chose reiserfs based on some reccomendations. It used to be ntfs.

My fstab line after quick editing now looks like this:
```

UUID=14902CDA902CC458 /media/sda1     auto    defaults 0       1

```
But mount complains that it can't find the device. Ideas?

---

### Post by kidders on 2006-10-29
Hi there,

Are you sure the UUID is correct?

One or two other (non-critical) suggestions:

[LIST]
[*]Change "auto" to reiserfs
[*]In ReiserFS terms, 3MB is _HUGE_, not tiny. If you are hoping to benefit from ReiserFS's sneaky little efficiencies for small files, your MP3s are miles too big.
[/LIST]

---

