---
title: "Samba: Cannot mount subdirectory, root directory works"
date: 2006-08-19
forum: General Help
---

### Post by fafek2 on 2006-08-19
Samba doesn't want to mount a network share:

```
[B]sudo mount -t smbfs //speed-3000/Fafek_pliki/Profile /mnt/Fafek_pliki

5906: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed[/B]
```


However, this mount call is successful:

[B]
sudo mount -t smbfs //speed-3000/Fafek_pliki /mnt/Fafek_pliki[/B]


Directory smb://speed-3000/Fafek_pliki/Profile exists!

---

### Post by lcg on 2006-08-19
> **fafek2 said:**
> Samba doesn't want to mount a network share:

```
[B]sudo mount -t smbfs //speed-3000/Fafek_pliki/Profile /mnt/Fafek_pliki

5906: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed[/B]
```


However, this mount call is successful:

[B]
sudo mount -t smbfs //speed-3000/Fafek_pliki /mnt/Fafek_pliki[/B]


Directory smb://speed-3000/Fafek_pliki/Profile exists!
Do you also have a share configured on the samba server for this directory?
You can only mount samba shares, not subdirectories of shares.

HTH,
Lars

---

### Post by fafek2 on 2006-08-20
So, I can't mount subdir of Windows share? Anyway, thank you.

---

### Post by opera118 on 2006-08-20
Nope, in the same way you can't mount a subdirectory in a hard disk partition, and in the same way you can't ping domain.com/path, only domain.com.
It's actually pretty reasonable.

---

