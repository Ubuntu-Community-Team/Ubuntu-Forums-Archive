---
title: "Why does it want to remove nvidia glx?"
date: 2007-01-09
forum: General Help
---

### Post by Russty of Oz on 2007-01-09
Hi all,

I got some more updates today, and once again it included the removal of nvidia glx.  In the past when this has happened it has sometimes been hell trying to get it working again.  So, why does it want to remove nvidia glx?  Is it necessary for some reason or is it just a computer glitch?  When I tell it not to remove it, I still have a update icon telling me that I have 1 update available.

Does anyone know what is going on here?

Russty

---

### Post by WiseElben on 2007-01-09
For me, trying to install nvidia-settings forces me to uninstall nvidia-glx, so perhaps you have something that is doing the same thing? I have nvidia-settings uninstalled, by the way.

---

### Post by Russty of Oz on 2007-01-09
Well, I rebooted and even though I didn't remove nvidia glx, I now cant get back into ubuntu!:( 

I have tried to reconfigure xserver but no luck yet.

Any ideas what else I can try?

---

### Post by justinjstark on 2007-01-10
I just got this too with the last updates.  The reason was because I had nvidia-glx from a third-party repository (amaranth I believe) and linux-restricted-modules depends on the ubuntu version.  So, rather than updating linux-restricted-modules, which may cause conflicts with the third-party nvidia-glx, apt-get instead decides just to remove both packages.

It's an easy fix.  Just remove nvidia-glx (third party) and install the ubuntu repository version.

It should be as simple as doing

```

sudo apt-get remove nvidia-glx
sudo apt-get install nvidia-glx

```

---

### Post by neewbe on 2007-03-17
hi everyone. I am new to ubuntu and to Linux. I have a GeForce4 MX 4000 what drivers do i need to install and how. PLease help me if you can.

---

### Post by fragos on 2007-03-17
For the Nvidia chip set there are two choices in Synaptic, nvidia-glx and nvidia-glx-legacy.  I'm reasonable sure nvidia-glx is what you want.

---

### Post by hikaricore on 2007-03-17
nvidia-settings is also i believe associated with the legacy drivers and is already included in nividia-glx which may cause further confusion.

You could avoid this entirely by installing the binary driver package directly from Nvidia's website, or by using the [envy script]("http://www.albertomilone.com/nvidia_scripts1.html").  Both of which will install the most recent version of the nvidia driver availiable.  With this you may need to reinstall the driver each time you upgrade your linux kernel (which shouldn't be too often).  But it saves the confusing package nvidia mess.

---

