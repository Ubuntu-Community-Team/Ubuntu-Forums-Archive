---
title: "Suspend to disk"
date: 2022-11-09
forum: General Help
---

### Post by zkab on 2022-11-09
How do I specify that my notebook should suspend to disk instead of RAM?
I have 22.10.

---

### Post by ne29914 on 2022-11-09
You don't.
Hibernate needs to be installed and configured manually and a swap partition defined on your hard drive.
Plenty of recipes around, do a search.

---

### Post by kurt18947 on 2022-11-09
> **ne29914 said:**
> You don't.
Hibernate needs to be installed and configured manually and a swap partition defined on your hard drive.
Plenty of recipes around, do a search.

How is the reliability of hibernate these days? It used to be pretty unreliable which is why it was dropped from the power menu. That was some years ago though. Personally with SSDs a cold boot is pretty fast and there's little question about the stability of the resulting session. Suspend to RAM should be fine for several hours without depleting a laptop battery much. Well, unless your laptop battery is like mine:redface:.

---

### Post by zkab on 2022-11-10
OK ... maybe suspend to RAM is the way to go ...

---

### Post by mIk3_08 on 2022-11-10
> **kurt18947 said:**
> How is the reliability of hibernate these days? 
Suspend is available in my Linux Ubuntu 22.04 LTS, For me if you don't  have enough battery for your suspension I prefer to use hibernation.  Hibernation will save you're unsaved works and files. You can still  enable hibernation in your system and its up to your configurations that you can  trust it or not. [Click Here]("https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/") for details. Regards and cheers

---

### Post by kurt18947 on 2022-11-11
There's one other thing to be aware of re hibernate. Hibernate requires a swap **partition.** Ubuntu used to create a swap partition as part of the installation by default. A few releases ago - 2 or 3? - there's a swap** file** created instead. A swap file will not work with hibernate, there is a hardware partition required larger than the amount of installed RAM, I think the recommendation was installed RAM X 1.5 for swap partition. This was a consideration when the default partitioning scheme was BIOS and was limited to 4 partitions. The 4th partition could be extended. The new partitioning scheme is GPT and doesn't have the 4 partition limitation. My memory could be off on this though so check around.

---

### Post by ne29914 on 2022-11-11
I wouldn't say that a swap partition is **required**, there are lots of web pages trumpeting the swapfile solution.
I've never managed to get it to work, and I haven't heard of other users either. Go figure.
Swap partition always works. A size of RAM plus 20% is enough.

---

