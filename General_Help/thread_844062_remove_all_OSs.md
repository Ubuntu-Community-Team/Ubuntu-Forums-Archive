---
title: "remove all OSs"
date: 2008-06-29
forum: General Help
---

### Post by the_jackel on 2008-06-29
i was messing around with ubuntu and i managed to do something to windows. i decided to reinstall ubuntu using the whole hard drive and thus remove windows completely. however, i want to get windows back as there are numerous programs that dont run on linux. i tried installing it but i got grub error 17. ive tried all sorts of things but i cant get rid of it (ive looked at all the threads on error 17, ive tried rejigging the partitions using GParted). talking to other people, error 17 occurs when you try and put windows on a computer where ubuntu already exists, but it doesnt occur if you put windows first and then ubuntu. in order to do this i need to remove ubuntu and the grub loader completely. i tried deleting the partition but that doesnt seem to remove grub. any help would be greatly appreciated

---

### Post by rraj.be on 2008-06-29
Actually what do you want to do now.

If you give us whats your exact need we could suggest a better IDEA.

Do you want to reinstall all OS freshly or do you want to recover your OS?

If any of the above is your requirement then please be clear about it.

You will get a good solution here.

---

### Post by the_jackel on 2008-06-29
i want to dual boot windows and ubuntu. but ive screwed around with the grub loader a lot so everythin ive tried has failed

---

### Post by rraj.be on 2008-06-29
> **the_jackel said:**
> i want to dual boot windows and ubuntu. but ive screwed around with the grub loader a lot so everythin ive tried has failed

What do you want to do now exactly?

This is my question

```
Is it to reinstall both your windows and ubuntu fresh?
```

---

### Post by the_jackel on 2008-06-29
yes. exactly

---

### Post by rraj.be on 2008-06-29
> **the_jackel said:**
> yes. exactly

Ok.Fine.

First boot into your ubuntu live cd or any other boot cd and make your hard disk wiped out completely if you can [I.E if you don't have any valuable data inside]
But its not compulsory to do this.


Then boot into your windows cd and install windows to a primary partition.

just boot into your ubuntu live cd and start installation.
```

In partition selection choose manual instead of Guided

```

Then make a partition of required size and to formate it to Ext3,and mount it to "/ "partition.

Make a partition of 1.5 or 2 GiB and formate it to "swap".

Now select your "/ "partition and click installation and there it goes very simple.

here is a very good Guide

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by the_jackel on 2008-06-29
how do u install windows to a primary partition

---

### Post by rraj.be on 2008-06-29
> **the_jackel said:**
> how do u install windows to a primary partition

By installing windows it will make its installation partition to be primary by default.

So there is no need for you to configure any thing regarding it.

---

### Post by the_jackel on 2008-06-29
what do you mean by "/" partition

---

