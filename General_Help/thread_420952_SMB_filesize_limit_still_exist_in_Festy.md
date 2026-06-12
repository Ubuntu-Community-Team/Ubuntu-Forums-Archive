---
title: "SMB filesize limit still exist in Festy?"
date: 2007-04-24
forum: General Help
---

### Post by asipi on 2007-04-24
HI,

does anyone know if the SMB 2 or 4 GB filesize limit still exist in Festy?
or it has been solved...

---

### Post by lassegs on 2007-04-24
Could you please elaborate?

I have to shares, both 300GB and I have mounted one windows disk 150GB, all over SMB.

---

### Post by asipi on 2007-04-24
e.g if I want to copy a 4.7 GB dvd iso-image to a windows share from a linuxbox I could not because smbmount have a 2 GB filesizelimit, and it tells when after 2GB transferred "File size limit exceeded"

I've read that the solution is under way but I don't know if it is implemented in Festy or not.

---

### Post by mdurham on 2007-04-24
> **lassegs said:**
> Could you please elaborate?

I have to shares, both 300GB and I have mounted one windows disk 150GB, all over SMB.
He's talking about file size not disc size.

---

### Post by bofphile on 2007-04-24
This limit doesn't exist anymore with Feisty. I've copied a 7,7 GB ISO image without any problem. :)

---

### Post by g8m on 2007-04-24
There is a "lfs" (large file support) option with smbmount. Using that breaks the 2 Gb limit.

---

### Post by asipi on 2007-04-24
thx for the infos

---

