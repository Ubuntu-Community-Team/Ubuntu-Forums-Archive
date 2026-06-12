---
title: "[SOLVED] Can't boot into hardy again (Not again)"
date: 2008-07-04
forum: General Help
---

### Post by Hyper Tails on 2008-07-04
Yes I had this problem with my laptop about a month ago.
But this is a different way.
I built a desktop pc 2-3 weeks ago and installed vista and hardy (Used wubi)
And for some reason I can't get into ubuntu Because Of this stupid retarded busy box (I Hate busybox)won't let me in.
Even booting into vista and rebooting it propley doesn't work.

Help Please.

---

### Post by VMC on 2008-07-04
> **Hyper Tails said:**
> Yes I had this problem with my laptop about a month ago.
But this is a different way.
I built a desktop pc 2-3 weeks ago and installed vista and hardy (Used wubi)
And for some reason I can't get into ubuntu Because Of this stupid retarded busy box (I Hate busybox)won't let me in.
Even booting into vista and rebooting it propley doesn't work.

Help Please.

I don't know anything about Wubi except its a directory of some sort off of a Windows partition. So I'm guessing fdisk display wouldn't be of much help.

But even so, if you boot with a livecd and type :

```
sudo fdisk -l
```

That might help

Can you output the Grub menu list. It's normally found on /boot/grub/menu.list
Out put it this way:

```
cat /boot/grub/menu.list
```

---

### Post by Hyper Tails on 2008-07-04
> **VMC said:**
> I don't know anything about Wubi except its a directory of some sort off of a Windows partition. So I'm guessing fdisk display wouldn't be of much help.

But even so, if you boot with a livecd and type :

```
sudo fdisk -l
```

That might help

Can you output the Grub menu list. It's normally found on /boot/grub/menu.list
Out put it this way:

```
cat /boot/grub/menu.list
```


I don't use a live cd but i'l try the out put

---

### Post by Hyper Tails on 2008-07-05
nope no luck

---

### Post by Gunman1982 on 2008-07-05
Did you defrag your windows partition? (just a question, don't do it) I don't know how grub handles the access to the wubi created file on your windows partition.

Maybe you can fix it by using the supergrub disc.

---

### Post by Hyper Tails on 2008-07-05
Well i know what cost it to pop up.

yesterday morning i was on ubuntu and the power went out for a bit and when i came on i booted into vista and tried ubuntu and no luck

---

### Post by cariboo on 2008-07-05
Have a look at this:

[http://kempj.blogspot.com/2007/09/wubi-dangers.html](http://kempj.blogspot.com/2007/09/wubi-dangers.html)

It may help with your problem.

Jim

---

### Post by Hyper Tails on 2008-07-05
> **cariboo907 said:**
> Have a look at this:

[http://kempj.blogspot.com/2007/09/wubi-dangers.html](http://kempj.blogspot.com/2007/09/wubi-dangers.html)

It may help with your problem.

Jim

I can use this.
Maybe next time i'l partition my hard drive (But how do i do that) when i install ubuntu.
I'll do it now.

---

### Post by Totto90 on 2008-07-07
Run Windows, then run disk check on the drive where ubuntu is installed. let it fix the problem. that should fix it. It happened with me before.

---

### Post by Hyper Tails on 2008-07-14
I installed it again by partitioning my hardrive and i got it to work.

Thanks.

no more wubi!!!!

Bye Bye wubi hello partitioning!!!!111!!!

---

