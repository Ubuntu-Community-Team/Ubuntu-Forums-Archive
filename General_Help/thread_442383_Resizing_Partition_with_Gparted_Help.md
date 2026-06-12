---
title: "Resizing Partition with Gparted Help"
date: 2007-05-13
forum: General Help
---

### Post by zangelacos on 2007-05-13
I'm trying to resize my main ubuntu partition, but when I open up gparted on the live cd, all I can do is shrink, delete, or format the partition. I have about 12.5 GB of unallocated space, but gparted only gives me the option to do what I mentioned earlier.

I've included a screenshot from within ubuntu just to give you an idea of what I'm looking at. This was taken after I partitioned the free space, thinking that maybe I could just use that instead of increasing the size of the main partition. That may have worked, but I don't have permission to write to it :/

Any help at all would be greatly appreciated. Thanks :)

---

### Post by merlinus on 2007-05-13
You might try downloading the iso for the gparted live cd, which is a newer version that may allow you to do this.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by zvacet on 2007-05-13
You don´t have  unallocated space,but 12.5 GB partition and some data on it.If it is not something important you can make it unallocated and after that resize your main partition to unallocated space and make it bigger that way.Take merlinus advice and download Gparted live CD and do it with it.

---

### Post by zangelacos on 2007-05-13
Yeah, that's exactly what I did, but there's no option to make the partition bigger. Also, the gparted live CD won't find my storage devices, but the one in the ubuntu live cd does. The Gparted disc just says its searching for the devices and never actually finds them.

---

### Post by zvacet on 2007-05-13
I think that Cd have option** force vesa driver**.Try with that.On your screenshot I see partition not unallocated space.Delete that partition and you will have unallocated space.After that resize your partition on unallocated space.Good luck.If Gparted don´t work for you you have to boot with your Ubuntu live CD.You can not do anything until partitions are locked and they are locked because they are runinig.

---

