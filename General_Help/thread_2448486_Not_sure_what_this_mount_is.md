---
title: "Not sure what this mount is"
date: 2020-08-08
forum: General Help
---

### Post by mickee384 on 2020-08-08
Since upgrading to ubuntu 20.04 I have a new mounted devise. Just curious what it is.. For sure don't want to unmount it not knowing. Here is a screenshot, hope that helps. Cheers!
[IMG]https://othersideoz.ca/mount.jpg[/IMG]

---

### Post by Bashing-om on 2020-08-08
mickee384; Hello -

Identify the 326MB volume ?
> 
new mounted devise. Just curious what it is..


what shows:
```

sudo fdisk -lu
mount

```

[INDENT]expect a secondary drive
[/INDENT]

---

### Post by Holger_Gehrke on 2020-08-08
Are you perhaps using the Android virtual machine [anbox]("http://anbox.io") ? The directory structure looks a bit like android and there is an anbox-init.sh file ... So it could be the container/virtual drive in which anbox runs.

Holger

---

### Post by mickee384 on 2020-08-16
it was the android virtual machine. Thanks!

---

