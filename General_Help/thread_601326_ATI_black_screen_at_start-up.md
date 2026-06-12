---
title: "ATI black screen at start-up"
date: 2007-11-03
forum: General Help
---

### Post by asearle on 2007-11-03
I have an ASUS Z9200va laptop with a ATI Radeon X700 graphics adaptor and I must say 'bravo' because under Kubuntu 7.10 everything works fine ... even the wide screen is correctly recognised!

For over a year I had been fishing around trying to find a version of Linux which recognises the ATI graphics adaptor without installing extra software/drivers.  So I'm very pleased now.

However, the boot process is extremely long (about 4 minutes) during which time the screen is completely black.  Then, once the log-in window appears everything goes very quickly.

My suspicion here is that Ubuntu needs to do some testing and self-configuration to get the graphics settings right.  And that this is done at every boot.

So maybe if I set up a specific graphics driver or settings, then I would get to see the start-up process and maybe even it would be quicker.

But as everything is working otherwise, I am a bit loathe to try to 'fix a running system'.

Anyway, if someone knows a simple trick/setting that would help, then I would like to try that.

Otherwise I can just recommend/comment that under my particular laptop works fine under Kubuntu 7.10.

Regards,
Alan Searle

---

### Post by gdp77 on 2007-11-03
**1) First u need to edit the usplash.conf to setup the correct resolution of your screen**

```
sudo gedit /etc/usplash.conf
```


This is my usplash.conft (15" wide laptop)  :

```
# Usplash configuration file
xres=1280
yres=800
``` 

**2) now, type the correct resolution for your monitor and save.**

**3) then in a terminal type :**

```
sudo update-usplash-theme usplash-theme-ubuntu
```

Now u will have both the splash screen at boot and it will be MUCH faster :)

Have fun

---

### Post by Son of Silas on 2007-11-03
Thanks! that fixed the black screen and painfully slow boot time that stopped my wife switching to Ubuntu.

---

### Post by asearle on 2007-11-05
Many thanks:  This worked for me too but I had to make sure that the ubuntu theme was installed (I used System/Adept Manager).

The start-up is very fast now.

Thanks,
Alan

---

### Post by Mum_Chamber on 2007-12-12
even though I had the correct resolution, I had the black screen.

the update solved the issue for me. 

thanks a lot

---

