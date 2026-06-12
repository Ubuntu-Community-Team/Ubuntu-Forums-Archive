---
title: "Beryl has me beat"
date: 2008-03-18
forum: General Help
---

### Post by wilburforce on 2008-03-18
Hi Im new to Linux so please forgive my silly remarks.
I have installed Unbuntu 7.10 on a IBM thinkPad T43 with Intel integrated graphics.

The OS great.
For the last 4 days Ive tried everything i could find on Google copy and pasting code to no avail.

Is it possible if so can someone please spend some time talking me through it.

I feel i have made that many changes nothing will work.

If you are going to as me about file please understand I'm days old in Linux.

I live in hope that one day i will have Beryl

---

### Post by SIXAXIS on 2008-03-18
I don't know how to help you buddy as I too could not get Beryl working. I have a Compaq Presario V2000 and the official drivers, but there is a known problem with running XGL with this card in Ubuntu 7.10.

If you want try going to System>Administration>Restricted Drivers Manager and make sure that your graphics card driver is checked off there. Also make sure that you have the official drivers from Intel. If it doesn't work, then I guess you're out of luck. And by the looks of it, it seems that your graphics card is weak anyway.

---

### Post by PeterJS on 2008-03-18
Beryl is old and out dated, in 7.10 beryl was replaced with compiz-fusion which is included in the based installed. But ironically enough, the compiz configuration tool wasn't, so you'll want to install that:
```

sudo apt-get install compizconfig-settings-manager

```
Then you'll want to enable compiz by setting the effects level to custom under System > Preferences > Apperance > Visual effects.

And then all the compiz settings will be under System > Preferences > Advanced Desktop Effects Settings

EDIT: as to the card itself working, given Intel's use of open drivers I was under the impression it would Just Work(tm), or not work at all.

---

### Post by dwasifar on 2008-03-18
Hi Wilburforce,


You haven't said specifically what the problem is with your effects, but try installing xserver-xgl and then restart X (or just reboot). To install it, use Synaptic or from terminal do this:

```
sudo apt-get install xserver-xgl
```

Also check /etc/X11/xorg.conf to make sure you're using the best video driver for your hardware and not defaulting to vesa. Run this from a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

if you want to walk through the process of changing the xorg.conf.

---

### Post by wilburforce on 2008-03-18
Ok This is what im after i would like the cube.

I have not downloaded any drivers other than ubuntu 199 updates.
i have now done this:

sudo apt-get install compizconfig-settings-manager

it worked and i have a custom settings (nothing set) I have wobbly windows

what now

---

### Post by wilburforce on 2008-03-18
done what
dwasifar's said and now i have lost wobbly windows when i try to add apperance pref extra
i get error
something about child compis missing

---

### Post by dwasifar on 2008-03-18
> **wilburforce said:**
> done what
dwasifar's said and now i have lost wobbly windows when i try to add apperance pref extra
i get error
something about child compis missing

If it was better before installing xserver-xgl, then back it out and start over:

```
sudo apt-get remove xserver-xgl compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager
```

Then consult this blog [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") for some guidance on how to use the various Compiz settings.

---

