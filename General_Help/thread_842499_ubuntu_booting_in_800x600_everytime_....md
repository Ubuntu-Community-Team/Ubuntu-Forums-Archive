---
title: "ubuntu booting in 800x600 everytime ..."
date: 2008-06-27
forum: General Help
---

### Post by Mia_tech on 2008-06-27
after I update my pc..the nvida driver was gone, and I ended up installing the nvdiang-gtk application, after that I was able to get my screen working again, but now every time I boot the pc I get an 800x600 screen and then an out of screen "login screen" in which I can even see when I'm typing my login username and password, has anyone come across something like this and knows how to fix it?

thanks

---

### Post by trevelyan on 2008-06-27
are you using the propietary driver from nvidia.com?
if not you should install those instead.
whats your graphics card?

---

### Post by Rhubarb on 2008-06-27
I'm not sure why you're not getting a login screen, but once Ubuntu has loaded up, press Alt + F2, then enter this in:
```
gksu displayconfig-gtk
```
This will give you a nice window where you can set your resolution / video card drivers / screen type.
Once finished, press OK then log out / restart Ubuntu and it should all be nice again.

---

### Post by Mia_tech on 2008-06-27
> **trevelyan said:**
> are you using the propietary driver from nvidia.com?
if not you should install those instead.
whats your graphics card?

here's my card
```
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```

what do you mean, like go to the nvida website and download their driver and install them?

thanks

---

### Post by trevelyan on 2008-06-27
yes thats what i meant.. but [here is the link]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/NVIDIA-Linux-x86-173.14.09-pkg1.run") to download the 32bit version driver.

i've attached the instructions on how to install the driver in a .doc file which you can open with openoffice word processor.
i suggest writing the instruccions down on a piece of paper or printing them out.

let me know how it went. ;)

---

### Post by Mia_tech on 2008-06-27
> **Rhubarb said:**
> I'm not sure why you're not getting a login screen, but once Ubuntu has loaded up, press Alt + F2, then enter this in:
```
gksu displayconfig-gtk
```
This will give you a nice window where you can set your resolution / video card drivers / screen type.
Once finished, press OK then log out / restart Ubuntu and it should all be nice again.

ohh yes I'm getting a login screen, it's just not showing the username box or the password box inside the screen...I tried your method but didn't work..still the same thing

thanks

---

### Post by trevelyan on 2008-06-27
ok to fix your issue without installing the nvidia propietary driver (though i recomend you do it anyways) do this.

navigate to:
/usr/share/applications

open "Screens and Graphics" and on the "screen" tab. where it says "model" choose an LCD with your monitor's native resolution or the resolution you want. click OK
then back on the "screen" tab where it says "resolution" pick the resolution you want. then click ok and logout and back in for changes to take effect.

that will take care of the 800x600 res all the time but it might not take care of the "out of screen" login screen. if it didnt get fixed on its own, to fix it.. let me see if i remember correctly.. you have to open your xorg file.

type this in a terminal:
 sudo gedit /etc/X11/xorg.conf

but i dont remember exactly what it is you have to change.. i think it was something related to the "screen" section. and change the resolution to something else (even if its already what you want it to be). then log out and then back in.. and then change it to what you actually want it to be and then log out and see if its fixed now.

let me know how that goes.. again... its better if you just install the driver becuase it autoconfigure all this for you.

---

