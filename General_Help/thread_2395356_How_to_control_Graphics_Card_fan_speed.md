---
title: "How to control Graphics Card fan speed"
date: 2018-06-30
forum: General Help
---

### Post by adamdonm on 2018-06-30
Guys,

I just installed a new copy of Ubuntu Gnome. Everything went swimmingly. Unfortunately the graphics cards fan speed is quite high. I know this because I can hear it, and on my windows installation its quiet.

I'm new to Linux.

---

### Post by NM5TF on 2018-06-30
we need more information to be able to help....such as:

what graphics card do you have....is it PCI or USB ???

post the output of

```
inxi -G
```

you may need to install inxi first

```
sudo apt-get install inxi
```

tommy

---

### Post by adamdonm on 2018-07-01
Its an old Graphics card. AMD Radeon HD 6870, PCI

Output of inxi -G:

```
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts XT [Radeon HD 6870]
           Display Server: X.Org 1.19.5 driver: N/A
           Resolution: 1360x768@60.02hz, 1920x1080@60.00hz
           GLX Renderer: AMD BARTS (DRM 2.50.0 / 4.13.0-45-generic, LLVM 5.0.0)
           GLX Version: 3.0 Mesa 17.2.8
```

---

### Post by NM5TF on 2018-07-01
have you looked at AMD overdrive ???

[https://sourceforge.net/projects/amdovdrvctrl/]("https://sourceforge.net/projects/amdovdrvctrl/")

also....latest Xorg is v 1.20   you might need to update....

tommy

---

### Post by adamdonm on 2018-07-01
Some more information to share, and a probable solution!

I'm running two monitors, (the inxi output shows this). This morning I decided to disconnect the second monitor/tv. I restarted the system and all of a sudden the GPU fan is spinning like normal.

This suggests that I can't run Linux with two monitors, unless I buy a newer GPU I guess.

---

### Post by adamdonm on 2018-07-01
I don't know what Xorg is. How do I update it?

---

### Post by NM5TF on 2018-07-01
```
sudo apt-get update
```

will install current package updates...

---

### Post by adamdonm on 2018-07-01
> **NM5TF said:**
> ```
sudo apt-get update
```

will install current package updates...

Thanks. I've run that now. How do I know what version I have installed?

---

### Post by NM5TF on 2018-07-01
forgot to add after update then run

```
sudo apt-get upgrade
```

after upgrade run inxi-G again....it will tell you what version of Xorg you have,,,

Xorg is your display server...

---

### Post by adamdonm on 2018-07-01
> **NM5TF said:**
> forgot to add after update then run

```
sudo apt-get upgrade
```

after upgrade run inxi-G again....it will tell you what version of Xorg you have,,,

Xorg is your display server...

Followed your steps:
```
 sudo apt-get update
sudo apt-get upgrade
inxi -G
```

Display driver still shows as 1.19.5

---

### Post by NM5TF on 2018-07-01
> **adamdonm said:**
> Some more information to share, and a probable solution!

I'm running two monitors, (the inxi output shows this). This morning I decided to disconnect the second monitor/tv. I restarted the system and all of a sudden the GPU fan is spinning like normal.

This suggests that I can't run Linux with two monitors, unless I buy a newer GPU I guess.

my web research tells me that your card can run up to 4-6 monitors.....[https://askubuntu.com/questions/365238/how-many-monitors-support-the-radeon-hd-6870-eyefinity-with-ubuntu]("https://askubuntu.com/questions/365238/how-many-monitors-support-the-radeon-hd-6870-eyefinity-with-ubuntu")

maybe you will find the answer there...

tommy

---

### Post by pqwoerituytrueiwoq on 2018-07-01
Just cause the the card can run more than one display does not mean it will do so at it lowest clock speed
you are using the Gnome 3 UI, that is far from a light weight UI, not surprising it would require more power to run both displays since more power means more heat the fan speeds up to cool the GPU
You could try to improve airflow around the GPU or use a lighter weight desktop UI like XFCE or LXDE
You could improve airflow by using a a side panel fan, installing front chassis fan, adding a bottom intake fan, and or removing dust
larger fans make less noise than smaller ones as they move more air at lower RPMs, i would suggest 120/140mm fans (Noctua fans are extremely good for low noise, but they are not cheap)
You could probably just use a 120mm fan with a 5v adapter to run it off the red/black instead of yellow/black wires from a molex plug on your PSU
Yellow to black = 12v
Yellow to Red = 7V
Red to Black = 5V
Beyond this a power can can be slowed down by adding a resistor inline, not all fans will spin with only 5v or may require a flick to start moving
if your case does not support side or bottom fans you can cut a hole out and something like this:
[https://www.newegg.com/Product/Product.aspx?Item=N82E16811999217](https://www.newegg.com/Product/Product.aspx?Item=N82E16811999217)
there are also cheaper wire grills if you do not care about dust or looks
i would suggest a fan with a 120 or 140mm fan with a RPM or 800 to 1500 rating
another more extreme option would be a custom liquid cooler and or doing a liquid metal mod to the card (NO NOT USE LIQUID METAL ON ALUMINUM COOLERS, be sure to do research on how to use this stuff it takes very little and it is conductive)

---

