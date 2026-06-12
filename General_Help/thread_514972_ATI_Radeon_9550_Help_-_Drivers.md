---
title: "ATI Radeon 9550 Help - Drivers"
date: 2007-08-01
forum: General Help
---

### Post by Vince4Amy on 2007-08-01
Hello.

I've been using Kubuntu for 2 years now. I've just decided to wipe my final machine & install Kubuntu on it. This machine has an ATI Radeon 9550. Since I've had no experience using ATI cards on Kubuntu I followed this guide here:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

I disabled the composite extension like it asked. And then I skipped down to method 2 as I wanted the more up to date drivers. This went great everything worked the way the guide said. Until I got to the stage > Configure the Driver. When I ran the commands:

```
sudo aticonfig --initial
```

And:

```
sudo aticonfig --overlay-type=Xv
```

I got some errors that I cannot paste here as I am currently on a Windows machine. I know one of them said Core Dumped. After rebooting my monitor said no signal after the Kubuntu boot screen.  I've now got a fresh installation of Kubuntu again. So how do I go about doing this?

Do I miss out the configure the driver step?

Thanking you in advance. 

Vince.

---

### Post by lundish on 2007-08-01
how about restricted drivers ?

it works for me (have the same card)

---

### Post by kelvin spratt on 2007-08-01
I have the same card as well works perfect with the default settings, its strange that the same card can be so different on one box to another, mine is never recognized as 9550 always 9600 and does not work with restricted drivers only default and i have 3d and acceleration as well the ATI cards are so hit and miss.

---

### Post by Vince4Amy on 2007-08-01
Okay thanks they did work. Just wanted the latest ones, but I see I probably don't need them. I had to install the Restricted Manager though because it's not included on Kubuntu.

---

