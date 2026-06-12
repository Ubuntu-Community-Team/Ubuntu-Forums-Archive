---
title: "Strange Issue After Repartition"
date: 2007-05-23
forum: General Help
---

### Post by Sweet Mercury on 2007-05-23
I recently used the GParted partitioning tool (awesome, bye the way) to repartition my 60GB hard drive. When I installed Ubuntu, I read the partitioning tool backwards and gave the Windows section 40GB and gave Ubuntu the rest.

I used the GParted tool to shrink the NTFS partition and make the ext3 partition bigger, and it had to rewrite (move) all the data over to the new start of the partition. Ever since then, when I come out of hibernation or boot the computer up, the ndiswrapper for my wireless "unloads" or something like that.

All I have to do to fix it is to open up terminal and type ```
 sudo modprobe ndiswrapper 
```, and the wireless reappears in the interface and works just fine.

It's more of a minor annoyance really.

If I type ```
ndiswrapper -m
``` I get ```
module configuration already contains alias directive
```

And as I understand it, the *ndisrapper -m* command is supposed to tell the wireless interface to load the ndiswrapper/driver on start up, so why isn't it working?

Is there a system file that I need to edit or something?

---

### Post by Sweet Mercury on 2007-05-24
Bump?

---

### Post by Sweet Mercury on 2007-05-26
Seriously, no one on this one?

---

### Post by Sweet Mercury on 2007-06-02
This is my last bump on this, I promise. I did wait a week though!

So come on, anyone?

---

