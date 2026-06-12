---
title: "Ubuntu freezing problem"
date: 2008-06-01
forum: General Help
---

### Post by jamieh on 2008-06-01
Hi,
I thought my hard drive was failing, because Ubuntu kept freezing, even though Windows was fine on the other drive (I have two).
So I replaced the Ubuntu hard drive, and I'm still having a problem with freezing, even on the new drive. Ubuntu works fine on my laptop, and I used the exact same CD to install it. But on my desktop, it will just completely freeze after about a half-hour of use. Again, my Windows drive DOES NOT FREEZE (Surprisingly).

When Ubuntu is frozen, Ctrl-Alt-Backspace does not work.

I really don't know if this is a hardware or software problem.

It's Ubuntu 8.04.
7.04 never had this problem. I just skipped 7.10 because by the time I "felt like" upgrading, 8.04 was just around the corner :)

Help!

---

### Post by benerivo on 2008-06-01
When it freezes, will the mouse cursor move, and will the keyboard LED'S (ie. NumLock, CapsLock) still switch on/off?

---

### Post by jamieh on 2008-06-01
> **benerivo said:**
> When it freezes, will the mouse cursor move, and will the keyboard LED'S (ie. NumLock, CapsLock) still switch on/off?

The mouse doesn't move, but the red light on the bottom stays lit
The keyboard LEDs stay as they were and cannot be changed

---

### Post by benerivo on 2008-06-01
In my limited experience, if the hardare works, then after 30 mins is totally frozen as you describe, it is probably a hardware problem. What is your hardware? I would also try another live cd (try this [one]("http://tinyme.mypclinuxos.com/wiki/doku.php?id=download"))

---

### Post by jamieh on 2008-06-01
> **benerivo said:**
> What is your hardware?

Is there a program that makes a list of all your hardware? I can't name everything in my PC (I'm lazy)

---

### Post by benerivo on 2008-06-02
> **jamieh said:**
> Is there a program that makes a list of all your hardware? I can't name everything in my PC (I'm lazy)
I know```
lspci
```in a termiinal should bring up a list. Also immediately after it has crashed, then start it up again, open a console and run```
dmesg
```This should list what looks like 'system events' in chronological order. Maybe this might help you find what happened at trhe moment of freeze. Also try another live cd for an hour.

---

