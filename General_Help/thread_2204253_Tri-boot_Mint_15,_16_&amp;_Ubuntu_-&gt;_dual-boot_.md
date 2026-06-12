---
title: "Tri-boot Mint 15, 16 &amp; Ubuntu -&gt; dual-boot Mint 16 &amp; Ubuntu but mint 15 still in grub"
date: 2014-02-07
forum: General Help
---

### Post by tyler-george on 2014-02-07
Hi all,

I recently had Mint 15 on my laptop but I wanted to upgrade so I just created a new partition and installed Mint 16 and copied all my documents. Then I decided I wanted to try Ubuntu 13.10 so I created another new partition and installed it there so I ended up with a Tri-boot system.

Then I deleted the Mint 15 partition, but it still shows up in the Grub menu. How do I delete it from the Grub menu?

Thanks in advance

---

### Post by sudodus on 2014-02-07
Boot into the system, that 'owns' grub. It is probably the system that you installed last, Ubuntu.

Run
```

sudo update-grub
```

which should scan the partitions for available operating systems and make entries in the grub menu for those found (and not for the one you removed).

---

### Post by tgalati4 on 2014-02-07
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by tyler-george on 2014-02-07
Thanks sudodus that worked!

---

### Post by tyler-george on 2014-02-07
> **sudodus said:**
> Boot into the system, that 'owns' grub. It is probably the system that you installed last, Ubuntu.

Run
```

sudo update-grub
```

which should scan the partitions for available operating systems and make entries in the grub menu for those found (and not for the one you removed).


Thanks that worked!

---

### Post by sudodus on 2014-02-08
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

