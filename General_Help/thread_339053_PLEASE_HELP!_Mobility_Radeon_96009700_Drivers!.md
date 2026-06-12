---
title: "PLEASE HELP! Mobility Radeon 9600/9700 Drivers!"
date: 2007-01-15
forum: General Help
---

### Post by theaverageidiot on 2007-01-15
I have a Mobility Radeon 9700 (I think). Device Manager says "RV350 [Mobility Radeon 9600 M10]" but Cedega says "MOBILITY RADEON 9700 Generic", but I'm pretty sure it's a 9700.

Anyways, I followed this guide for the drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
The manual way.

And Cedega says "OpenGL Direct Rending" passes the test but "3D Acceleration" doesn't pass :(. Anyone know what I should do?

---

### Post by der_joachim on 2007-01-15
I have an Nvidia card, so I cannot help you there, but if you want to know which card you have, just issue the following command:
```
lspci | grep -i radeon
```

---

### Post by theaverageidiot on 2007-01-15
> **der_joachim said:**
> I have an Nvidia card, so I cannot help you there, but if you want to know which card you have, just issue the following command:
```
lspci | grep -i radeon
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

That's what is in the device manager. I really think I have a Mobility Radeon 9700 though :(. (I've got a laptop, a Dell XPS Gen 1)

---

### Post by peabody on 2007-01-15
> **theaverageidiot said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

That's what is in the device manager. I really think I have a Mobility Radeon 9700 though :(. (I've got a laptop, a Dell XPS Gen 1)

I wouldn't fret with the 9600vs 9700, it's likely that internally they're the same (perhaps slight hardware differences) and use the same driver.  What does "fglrxinfo" typed into a terminal say?  What does "lsmod | grep fglrx" typed into a terminal say?

---

### Post by theaverageidiot on 2007-01-16
> **peabody said:**
> I wouldn't fret with the 9600vs 9700, it's likely that internally they're the same (perhaps slight hardware differences) and use the same driver.  What does "fglrxinfo" typed into a terminal say?  What does "lsmod | grep fglrx" typed into a terminal say?

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)
```

```
$ lsmod | grep fglrx
fglrx                 534616  9 
agpgart                34888  2 fglrx,intel_agp
```

---

### Post by peabody on 2007-01-16
You have a mobility 9700 if that's what the official driver is reporting (and it is).  As to why Cedega reports no 3d acceleration, I'm not sure.  Have you tried running any games?

---

