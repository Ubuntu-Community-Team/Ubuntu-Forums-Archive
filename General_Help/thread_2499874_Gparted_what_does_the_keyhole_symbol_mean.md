---
title: "Gparted: what does the keyhole symbol mean?"
date: 2024-08-13
forum: General Help
---

### Post by makem2 on 2024-08-13
All of my partitions have a black keyhole shaped symbol next to them.

It is not a key.

I don't remember seeing these before and I cannot find anything, what does it mean?

---

### Post by yancek on 2024-08-13
Can you post an image here or elsewhere with a link?  A key icon means mounted and can't be changed.  A red circle or yellow triangle with an exclamation mark in it is an indication of some problem.  I've never seen a 'black keyhole' symbol.   Which version of Ubuntu and GParted are you using?

---

### Post by makem2 on 2024-08-13
> **yancek said:**
> Can you post an image here or elsewhere with a link?  A key icon means mounted and can't be changed.  A red circle or yellow triangle with an exclamation mark in it is an indication of some problem.  I've never seen a 'black keyhole' symbol.   Which version of Ubuntu and GParted are you using?

I am in good company then ;-)

[https://pasteboard.co/Jb5uBgsQHrvq.png](https://pasteboard.co/Jb5uBgsQHrvq.png)

Gparted ver. 1.5.0

```

makem@makem-22:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 24.04 LTS
Release:    24.04
Codename:    noble
makem@makem-22:~$ 

```

---

### Post by oldfred on 2024-08-13
I always install gparted, but know I cannot use it on mounted partitions. So only use it on my other drives.
With my Kubuntu 24.04, I have similar key hole, but so tiny I never noticed before.
It used to be a tiny key.
If you click (right click) on key, it gives a menu, one of which is unmount. But you cannot unmount the system you are using.

---

### Post by makem2 on 2024-08-13
> **oldfred said:**
> I always install gparted, but know I cannot use it on mounted partitions. So only use it on my other drives.
With my Kubuntu 24.04, I have similar key hole, but so tiny I never noticed before.
It used to be a tiny key.
If you click (right click) on key, it gives a menu, one of which is unmount. But you cannot unmount the system you are using.

The only time I have seen anything it that position it has meant there is a problem. However the machine appears to be functioning correctly.

Jellyfin was installed and it crashed, making a core dump. I could not even shut down. During the time I spent sorting that out I noticed those keyholes and thought somehow the core dump had caused the computer not to shutdown. I had 'not enough space on drive errors'.

I purged Jellyfin and Brave browser which was using Jellyfin at the time of the crash.

Still seeing those keyhole still worried me.

Yes, you can unmount and the keyhole disappears but returns when you mount. Information says nothing keyhole related.

Maybe the keyhole is related to 24.04

Why should every partition on each of 3 drives be affected?

---

