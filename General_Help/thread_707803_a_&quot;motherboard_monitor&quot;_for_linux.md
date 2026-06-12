---
title: "a &quot;motherboard monitor&quot; for linux"
date: 2008-02-25
forum: General Help
---

### Post by onemanclapping on 2008-02-25
hi,

is there any kind of "motherboard monitor" (the windows application that lets you know the temperature, usage, etc of your CPU) that I can use with Ubuntu?

It would be nice if it could be minimized to the upper panel, showing only the temperature of the CPU, like MBM.

thanks in advance,

André

---

### Post by fritz_monroe on 2008-02-25
I use GKrelM on my laptop.  Does the stuff you are asking about, but I don't know if it's able to be minimized.  I have mine as the right inch of my desktop and my browser is expanded out to the edge of GKrellM.  Lots of skins available for it.  Personally I like the transparent ones.

---

### Post by fjgaude on 2008-02-25
Ubuntu handles everything you wish to do, have on your desktop.

```
sudo apt-get install hddtemp lm-sensors sensors-applet gkrellm
```

This will give all and more than you wish for. Then you have to configure the sensors by running:

```
sudo sensors-detect
```

Use the default responses. Then you can get skins for gkrellm from [www.muhri.net](www.muhri.net), they are 100s.

Use a right-click on the panel to install sensors there. This maybe all you want. Ubuntu has it all. Trust me. <smile>

Let us know how you are doing.

---

### Post by Wolfghar on 2008-02-25
This is probably what your looking for, it worked for me.

[http://www.techthrob.com/tech/linuxsensors.php]("http://www.techthrob.com/tech/linuxsensors.php")

---

### Post by onemanclapping on 2008-02-26
thanks for the quick reply. I'll test them as soon as I get home :)

---

