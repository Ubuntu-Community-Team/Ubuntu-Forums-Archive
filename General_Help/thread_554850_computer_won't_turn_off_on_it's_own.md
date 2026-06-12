---
title: "computer won't turn off on it's own"
date: 2007-09-19
forum: General Help
---

### Post by namelessone on 2007-09-19
I have installed ubuntu on two pentium III machines now, and I have noticed an odd problem on both where when I shut down the computer, it never turns off--I have to do that myself by hitting the power button.

Is this just something that happens on older computers? I know that really old AT styled ones were like this, but pentium IIIs?

---

### Post by kidders on 2007-09-20
Hi there,

> **namelessone said:**
> Is this just something that happens on older computers?Yeah, 'fraid so. Some (*really* old) computers simply don't know how to turn themselves off. Others quite often have quirky power management interfaces that don't always behave as expected.

A lot of the time, other OSs (eg Windows) are perfectly capable of powering off computers with buggy power management, so your problem may be peculiar to Linux. If so, there are often (but not always) solutions, such as the addition of a kernel parameter in your /boot/grub/menu.lst.

Sorry for only giving you half an answer ... but I didn't want your thread to fall into the abyss without *some* kind of response. Try searching for Linux-related information on your particular motherboard. Someone else must've surely seen (and solved?) this problem before you ... I hope!

---

### Post by confused57 on 2007-09-20
I had a problem with Edgy completely shutting down on an AMD K6-2, 500 MHz, this worked for me:
```
gksudo gedit /etc/modules
```

add this line to the file:
```
apm power_off=1
```

---

### Post by FreewheelinFrank on 2007-09-20
Also a problem on some newer machines, like my 6 month old Evesham.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43961/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43961/)

---

