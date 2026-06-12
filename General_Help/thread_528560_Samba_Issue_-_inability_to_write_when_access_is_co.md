---
title: "Samba Issue - inability to write when access is correct."
date: 2007-08-18
forum: General Help
---

### Post by xoddoza on 2007-08-18
Heya,

I've got a fileserver with 5x 400 gig drives in it raided as raid 5.

Works nicly except having some slight issues with samba. I had it all working fine copying and writing (once i got rid of the silly realtek network) but it required a user to login to access anything on the servers. This didnt go down well with the flatmates etc so i removed the ability in samba to login and made it guest.

My issue now, is that You can view the files prefectly, but when you try to copy ON, or move them you get a file in use error or denied error.

I've checked the permisions settings and as far as i can tell its set to reads and writes. Is there somthing that needs to be done to allow guests to edit?

Samba Conf
```
[global]
workgroup = XXXX
wins support = no

interfaces = lo eth1
bind interfaces only = true
security = share
guest account = nobody

[Entity Movies]
        comment = Movies
        path = XXXXX
        browseable = yes
        guest ok = yes
	writable = yes
        read only = no

[Entity Music]
        comment = Music
        path = XXXXX
        browseable = yes
        guest ok = yes
	writable = yes
        read only = no

[Entity Programs]
        comment = Programs
        path = XXXXX
        browseable = yes
        guest ok = yes
	writable = yes
        read only = no
```

---

### Post by Blindraven on 2007-08-18
make an account guest/guest  then chown the dirs to nobody = guest/guest and either 775 or 777 the files/folders.

---

### Post by xoddoza on 2007-08-18
Cheers that worked perfectly.

---

