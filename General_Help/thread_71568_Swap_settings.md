---
title: "Swap settings"
date: 2005-10-03
forum: General Help
---

### Post by kb7ypf on 2005-10-03
Hi All-
I have a quesiton or two. 
Q.  Do I need to use Memory Swap?  I have 512 Meg Ram.
If you recommend the use of memory swap, how would I do that and what drive do I put it on? Or can I use the Ubuntu 7GB dirve (where Ubuntu lives) I have partitioned for Ubuntu?  That is probably not a good idea as I may run into problems with a shrinking volume as I add programs.  Any help would be greately appreciated.  
Thanks for your help.
Dick

---

### Post by FLeiXiuS on 2005-10-03
SWAP is highly reccomended.  Without it your machine will seriously suffer.  A SWAP partition is just the same as having "x" more memory.  'x' being the size of the swap partition.  Basically, virtual memory.

Create a partition as you normally would.  Then format it with mkfs.swap. 

I my self would require a reboot for such a change to the system.  The swap drive should automatically be detected and mounted correctly.

---

### Post by kb7ypf on 2005-10-03
Thanks for your response.

I am a Newbie, so with that said, where would I find instructions on how to create a memory swap.

Thanks again.


Dick

---

### Post by FLeiXiuS on 2005-10-03
All you have to do is create a partition with 2x your current memory.  1024MB in other words :-).  You can download qtparted to aide with the partition creation process.

```
$ apt-get install qtparted
```

Be sure to have the extra repositories enabled as mentioned on [http://ubuntuguide.org](http://ubuntuguide.org).

After the creation of the partition.  Find the partition label. (ie: /dev/hda1, /dev/hdb1)  QTParted should tell you this information.

Now format the partition as a swap device.

```
$ sudo mkswap <partition label>

ex: sudo mkswap /dev/hda7

```

---

### Post by kb7ypf on 2005-10-03
Thanks FLeiXiuS-

It worked great...

Glad you are around to help out.

Again, many thanks.


Dick

---

### Post by FLeiXiuS on 2005-10-04
:-) No problem, always glad to see a welcomed new Ubuntu user.  Enjoy!

---

