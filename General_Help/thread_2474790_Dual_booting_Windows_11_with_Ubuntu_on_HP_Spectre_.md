---
title: "Dual booting Windows 11 with Ubuntu on HP Spectre x360 15t"
date: 2022-05-08
forum: General Help
---

### Post by alaa0essam on 2022-05-08
[COLOR=#232629][FONT=-apple-system]I'm a new Ubuntu user, and I wanna dual boot Windows 11 which I installed later with Ubuntu I have HP Spectre x360 15t wiI'm a new Ubuntu user, and I wanna dual boot Windows 11 which I installed later with Ubuntu I have HP Spectre x360 15t with NVME SSD

• I did specify some space for Ubuntu partitions but whenever I boot from the USB drive to use this space to create Ubuntu partitions and install it, it doesn't show at all!


[/FONT][/COLOR]

---

### Post by yancek on 2022-05-08
It might be that your windows 11 is hibernated and Linux systems won't mount hibernated systems.  You could check hibernation setting under power management in window.
'

---

### Post by alaa0essam on 2022-05-08
Hi &#55356;&#57144;
No it's not hibernated
&#8226; I have HP Spectre x360 Convertible 15t-eb000
&#8226; Intel(R) Core(TM) i7-10750H CPU @ 2.60GHz   2.59 GHz
&#8226; 16.0 GB of RAM with Optane Memory
&#8226; I'm trying to dual boot Ubuntu 22.04 amd64


[https://ibb.co/cDP0MvF](https://ibb.co/cDP0MvF)


[https://ibb.co/wY3NS24](https://ibb.co/wY3NS24)


[https://ibb.co/bbHLb9j](https://ibb.co/bbHLb9j)


[https://ibb.co/GWB6S5f](https://ibb.co/GWB6S5f)


[https://ibb.co/v459D60](https://ibb.co/v459D60)


[https://ibb.co/TMZmBNT](https://ibb.co/TMZmBNT)


[https://ibb.co/vHFsyLV](https://ibb.co/vHFsyLV)


[https://ibb.co/SvTRwng](https://ibb.co/SvTRwng)

---

### Post by tea for one on 2022-05-08
> **alaa0essam said:**
> Hi 
• 16.0 GB of RAM with Optane Memory

Optane memory is a bit of an obstruction when installing Ubuntu (or similar Linux systems)

The attached thread has a lot of info, however, in essence, can you disable optane in your UEFI set up?

[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)

---

### Post by alaa0essam on 2022-05-11
Thanks so much, that was my problem yeah &#55356;&#57144;

---

### Post by tea for one on 2022-05-13
> **alaa0essam said:**
> Thanks so much, that was my problem yeah &#65533;&#65533;
Is this now solved?
If so, it is a nice gesture to mark the thread as solved to help other forum members/searchers?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

