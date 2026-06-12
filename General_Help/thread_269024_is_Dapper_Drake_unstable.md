---
title: "is Dapper Drake unstable?"
date: 2006-10-01
forum: General Help
---

### Post by Sambie on 2006-10-01
After reiceving a virus while running windows I've decided to install   Dapper Drake 6.06.1 onto my machine to get away from all of theses spywares/viruses and etc.

So far I must sadly report that I've recieved 3 severe freezes (I couldnt even move the mouse)on my machine of which I had to restart my entire machine.

Is anybody else having theses freezes or am I the only one?

I also updated my system.

---

### Post by finnjimm on 2006-10-01
That is not normal. It's most likely a hardware problem. I'd suggest running exhaustive tests with memtest86 first...

---

### Post by aysiu on 2006-10-01
Freezes generally come about for one of three reasons:
1. Hardware failure (as finnjimm mentioned already)
2. Lack of the proper video drivers (if you need to install Nvidia drivers, for example)
3. Insufficient RAM

---

### Post by Sambie on 2006-10-01
Ok how can you do that? Sorry Im a rookie :(

---

### Post by aysiu on 2006-10-01
When you first boot up, there should be a boot menu with a regular Ubuntu, a "recovery mode" Ubuntu, and a "memtest."

If you select the "memtest," it'll test your memory.

To install Nvidia drivers (if you actually have an Nvidia graphics card), look here:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by nthdegree on 2006-10-01
"Freezes generally come about for one of three reasons:
 1. Hardware failure (as finnjimm mentioned already)
 2. Lack of the proper video drivers (if you need to install Nvidia drivers, for example)
 3. Insufficient RAM"

If you have used Automatix or EasyUbuntu, reinstall your system.  If you are using nVidia binary drivers get rid of them.  If you are using any form of non open-source binary-only software uninstall it now.

At least 1 in 20 people I talk to with Linux problems like that are using proprietary drivers or proprietary software, as soon as the system was set up with only FOSS software all was well again.

---

### Post by aysiu on 2006-10-01
Really? I'd always seen it as the opposite. Someone has an Nvidia card but is using the Nv driver instead of the native (and proprietary) Nvidia driver and experiences occasional freeze-ups.

How are we getting such different perceptions?

---

### Post by yopnono on 2006-10-01
> **Sambie said:**
> After reiceving a virus while running windows I've decided to install   Dapper Drake 6.06.1 onto my machine to get away from all of theses spywares/viruses and etc.

So far I must sadly report that I've recieved 3 severe freezes (I couldnt even move the mouse)on my machine of which I had to restart my entire machine.

Is anybody else having theses freezes or am I the only one?

I also updated my system.

In the beginning of down yes. It could not even wakeup after suspend on my Dell. But now... it's unstable as a rock. ;)

---

### Post by Kateikyoushi on 2006-10-01
> **yopnono said:**
> In the beginning of down yes. It could not even wakeup after suspend on my Dell. But now... it's unstable as a rock. ;)

I wonder how would you describe it, if it were stable.

---

### Post by yopnono on 2006-10-01
> **Kateikyoushi said:**
> I wonder how would you describe it, if it were stable.

Well it was unstable when it came out, now it's stable.

```
But now... it's ***unstable*** as a *rock*.
```
Irony

---

### Post by bigaltx on 2006-10-01
Aysui's right, I've never had any luck with the nv driver ie. crashes and lockups. No problems since installing the proprietary nvdia driver 6 months ago.

---

### Post by Grog140 on 2006-10-01
I get lock ups with the Skype beta. I am not sure if I get them with the non-beta because I can't replicate the error but sometimes when I call/recieve a call I get hard locks.

Pretty annoying, hopefully I will be able to fix it some day.

---

### Post by guine on 2006-10-01
For most people dapper seems to be very stable but you wouldnt be alone if you are having dapper constantly crashing even though you have working hardware.(thats the case for me)  If your hardware is good and you cant figure out how to fix dapper you could try installing breezy which one of my friends and I have both done because dapper was unusable for us and breezy has been working fine for both of us after going back to it.

---

