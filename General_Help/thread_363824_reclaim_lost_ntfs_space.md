---
title: "reclaim lost ntfs space"
date: 2007-02-17
forum: General Help
---

### Post by hduk on 2007-02-17
heeello...

i have installed several distributions on my laptop over the past year and resized my ntfs partition several times using qt/parted, somehow, i can't get windows back to recognise the space given back to it

in linux (amd64), qtparted shows 80gb for ntfs, but in windows (xp) only 60gb is available

can someone help explain how can i reclaim my 20gb for windows?

do i need a win or linux tool to fix?

cheery

hduk

---

### Post by FuturePilot on 2007-02-17
That's because it's still a separate partition. You just formated it in NTFS. What I would do is use GParted (you can still use qtparted if you'd like) and you have to delete the 20GB NTFS partition then resize your Windows partition to take up the unallocated space.

---

### Post by hduk on 2007-02-17
not quite,

in windows disk mgmt, it shows 4 partitions:

pqservice (3gb)
acer c: (80gb)
linux swap (2gb)
linux (10gb)

the key problem is that i only have 66gb available for the acer c: drive

in disk manager, the physical disk0 shows 80gb for the acer partiotion, but on the top section it shows capacity of 66gb

??

---

### Post by hduk on 2007-02-17
here's a screen shot of disk manager:

[attach]25533[/attach]

---

