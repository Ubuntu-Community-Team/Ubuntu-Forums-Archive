---
title: "Where do i find Add/Remove KDE 4?"
date: 2008-03-02
forum: General Help
---

### Post by Dojan5 on 2008-03-02
To be honest i have more than one question...
The main one is, where do i find the Add/Remove for KDE 4?
I can only find Add/Remove for GNOME and KDE 3.5
Secondly, is there any Partition editor for KDE? I have a weird thing going on, my (Idiotically big) SWAP partition is never on when booting. I always have to manually turn it on, and thats a pain.
Then, is there a way to make KDE and GNOME make a menu for the apps?
I mean, before i reinstalled Ubuntu i had some menu addon which separated the applications. Only in GNOME though. It made a new menu in the menu called KDE and in there it put all the existing KDE applications. Im sorry, but i cant remember its name. Anyone know what it is called? Is there any for KDE (4 preferably)
Thanks for bearing with me.
/
Joel, the question master (:lolflag:)

---

### Post by Nzer24 on 2008-03-02
You won't find KDE 4 in the repositories because it isn't stable yet. You need to either install it from source or add a new repository for KDE 4. You should be able to find some sort of guide on the KDE website (I haven't looked).

KDE 4 is still in beta, so it won't be perfectly complete or stable, so make sure you know what you are doing.

---

### Post by amingv on 2008-03-02
On the official Kubuntu website, they have released the Alpha version of Hardy with KDE4, this will come as a side to the "Official" KDE3 release:
[https://wiki.kubuntu.org/HardyHeron/Alpha5/KubuntuKDE4](https://wiki.kubuntu.org/HardyHeron/Alpha5/KubuntuKDE4)
They also have a guide for installing KDE4 on Gutsy:
[http://kubuntu.org/announcements/kde-4.0.1.php](http://kubuntu.org/announcements/kde-4.0.1.php)

But as Nzer24 said, think twice before you install it. And if you do, be a good guy and report all bugs/strange behaviours you find, OK?

If you want a KDE native partitioning app you can use QtParted:

```
sudo apt-get install qtparted
```

Though there's no reason why you can't use gparted if you prefer, (I do).

Lastly, I do not know of the program you mention in your last question...

---

### Post by Dojan5 on 2008-03-03
KDE 4 has a stable release (As far as i know)
There is KDE 4.0.0 and KDE 4.0.1 which the last was released  2008-02-05.
I already have it installed, it is pretty stable, but when running a couple of "heavy" GNOME apps on KDE 4 it might crash, which ends with a loss of the panel (:lolflag:)
But im pretty sure it is out of beta...
And i meant Add/Remove programs for KDE 4.
I only have Add/Remove programs for KDE 3.5 and GNOME

---

