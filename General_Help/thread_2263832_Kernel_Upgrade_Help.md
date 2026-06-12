---
title: "Kernel Upgrade Help"
date: 2015-02-03
forum: General Help
---

### Post by Evil Wayz on 2015-02-03
I'm back after being with Mint for a few years, and I was wondering if there was a helper utility like there is in Mint.  It was located  within the software updater and told you what kernel you had, and what was available/compatible.

---

### Post by deadflowr on 2015-02-03
Unlike Mint, Ubuntu upgrades kernels, based upon which ever kernel series is installed, by default.
Simply run the software updater, and you'll get the latest for which ever version/series you have installed.

For example you've listed being on trusty, so the kernel series for trusty is the 3.13 series.
I believe the kernel install was something like 3.13.0-3(maybe something else I forget.
If you run an update you should bet the latest stable, which is 3.13.0-45.

No need to set anything to enable this.
It's all part of Ubuntu's security updates.

Hope this helps.

---

### Post by whitesmith on 2015-02-03
You can verify **deadflowr**'s advice by typing into a terminal```
uname -a
```. My system gives this information```
david@London:~$ uname -a
Linux London 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```Kernel and word width in a single utility. Kinda cool! Would be nice to have the OS version as well, but ours is not an ideal world.

---

### Post by Portaro on 2015-02-03
I made a tool that requires Gambas3 and curl installed on the system, and with this tool you can easily see what is the versions compatible and available with your system - [https://sourceforge.net/projects/kernelfind/](https://sourceforge.net/projects/kernelfind/) 
[IMG]https://a.fsdn.com/con/app/proj/kernelfind/screenshots/kernelfind1.png/182/137[/IMG]

Its a nice utility I do to stay informed how kernels I can install on my ubuntus.

There are other methods , with synaptic you can easily see linux-images and install with a click, my tool dont install only give the info about kernels available to the system.

---

### Post by Evil Wayz on 2015-02-03
I assume I have to compile something to use this?

---

### Post by monkeybrain20122 on 2015-02-03
> **Evil Wayz said:**
> I assume I have to compile something to use this?

No, he provides a .deb, just click to install.

---

### Post by monkeybrain20122 on 2015-02-03
> **deadflowr said:**
> 
For example you've listed being on trusty, so the kernel series for trusty is the 3.13 series.
I believe the kernel install was something like 3.13.0-3(maybe something else I forget.
If you run an update you should bet the latest stable, which is 3.13.0-45.
.

This is through official channel. But one can install any that works from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I am running 3.19 rc7 on Trusty, it fixes a very annoying problem of vlc crashing when vaapi is enabled on my laptop and it is faster than the stock 3.13 kernel.

If kernel upgrade doesn't work, normally just need to boot into the previous one and remove the new one (then maybe pin the kernel for til the next round of upgrade), not sure what purpose Mint's thing serves.

---

### Post by Evil Wayz on 2015-02-04
I didn't see a .deb at the location he provided, just a tarball.

---

### Post by monkeybrain20122 on 2015-02-04
Click Download and it offers kernelfind-gtk_0.0.2-1_all.deb

---

### Post by Evil Wayz on 2015-02-04
Tried all three debs, get unsatisfied dependency errors for stuff that apt-get says doesn't exist.

---

### Post by Portaro on 2015-02-04
Here -> [http://sourceforge.net/projects/kernelfind/files/Kernelfind/](http://sourceforge.net/projects/kernelfind/files/Kernelfind/) - the aplication show kernels compatible with your system, then you can search about versions kernels that you thinking to install or no.

Many Kernels are disponible, patch, modified etc . Like Liquorix for example.

---

### Post by Evil Wayz on 2015-02-04
Ok got it to work, but the kernels available in synaptic didn't match the ones in the program.  Upgraded anyways, got a bunch of usb error messages, but everything works, so.... thanks for the help guys.

---

### Post by monkeybrain20122 on 2015-02-05
If you don't know what you are doing you should stick to the kernels from the repository. Where do these kernels come from and why do you think it is necessary to upgrade kernels beyond what the system offers?

---

### Post by Evil Wayz on 2015-02-05
I did stick to the kernel from the repository.  It just didn't happen to pop up in that kernel find program.

---

