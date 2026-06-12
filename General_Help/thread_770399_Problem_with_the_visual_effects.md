---
title: "Problem with the visual effects"
date: 2008-04-27
forum: General Help
---

### Post by grimed on 2008-04-27
Hello...

I'm having a problem for some reason with loading the visual effects of Ubuntu 8.04 and i've checked the hardware drives and found out that my Nvidia graphic card is not working properly or "not in use" according to the OS.so i was wondering if anyone could help me with it,please note that I'm a complete newbe with Ubuntu OS so explain it step by step please....

Note:
*I'm using an HP pavilion dv6000 laptop 
*I'm using Nvidia Gefroce 8400M GS graphic card

---

### Post by akshar_patel_47 on 2008-04-27
First see if nvidia drivers are enabled or not. If it is then go to preferences-> appearances and then visual effects. Select normal or extra. It will then ask your permission to use the nvidia restricted drivers. Do all these with internet on so that it can download any package if necessary. This will change the status of your graphic card drivers to in use.

---

### Post by grimed on 2008-04-27
Nope still got the same error..."Desktop effects could not be enabled" ive noticed that the nvidia is enabled but as i said its status is "not in use"
for some reason...

---

### Post by akshar_patel_47 on 2008-04-27
Then go to the synaptic package manager and search nvidia. See which driver is installed. Do Complete uninstall of that driver manually.
Then go directly to appearence->visual effects and select extra which will install as well as start using your nvidia graphic card drivers.

This is the way I did it.

---

### Post by hal40k on 2008-04-27
Hey,
I'm having some problems getting the visual effects activated - the Restricted Drivers Manager says that an **ATI Accelerated Graphics Driver** is Enabled and In Use.

But I keep getting an error message when I try to activate visual effects:
*The Composite Extension is not Available* ...!... Help pls heh

---

### Post by grimed on 2008-04-27
sorry still the same error :s

---

### Post by Zorael on 2008-04-27
Nvidia: try entering the following in a terminal.
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup0804
$ sudo nvidia-xconfig -d 24 --add-argb-glx-visuals --allow-glx-with-composite --composite
```
The latter command won't work unless you have the nvidia driver package installed; nvidia-glx-new, nvidia-glx or nvidia-glx-legacy.

---

### Post by Ub1476 on 2008-04-27
> **hal40k said:**
> Hey,
I'm having some problems getting the visual effects activated - the Restricted Drivers Manager says that an **ATI Accelerated Graphics Driver** is Enabled and In Use.

But I keep getting an error message when I try to activate visual effects:
*The Composite Extension is not Available* ...!... Help pls heh


Post the output of:

```
cat /etc/X11/xorg.conf
```

And:

```
Compiz
```

**BUT**, if you are running Ubuntu 7.10 (Gutsy), which I think you do since you said "Restricted Driver Manager", you might have to install XGL (xserver-xgl) for it to work.

I strongly suggest you to upgrade to Ubuntu 8.04 LTS (Hardy Heron) if this is the case though.

---

### Post by hodenkat on 2008-04-27
OK - Here's what worked for me!

IBM T-40 : ATI Mobility Radeon 7500

Desktop effects working now just like they did running 7.10!

Go to : [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Hope this helps!:guitar:

---

