---
title: "Upgrading Video Card - Pre-Install Tips Please"
date: 2007-05-08
forum: General Help
---

### Post by DarthWHO on 2007-05-08
I'm about to install a new (well, new to me) video card. Getting rid of this ATI card for a Nvidia card. What are some recommendations before swapping out the hardware?

Is there anything software/OS wise that I should uninstall? Will Ubuntu recognize the new hardware and not attempt to use my previous ATI drivers and automatically install appropriate drivers?

Coming from Windows, I know I would practically have to do a full OS re-install if I wanted all my drivers to work together with a new card.

---

### Post by taurus on 2007-05-08
First, edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and change whatever driver to nv.

```
Driver       "nv"
```
Shutdown the computer and then replace the graphic card.  Then, boot up the machine and see if X is running again.

---

### Post by DarthWHO on 2007-05-08
Sounds simple enough ;)

My wife says that's a sure sign I will screw it up...

---

### Post by taurus on 2007-05-08
But if X doesn't run after you install nVidia card, then you just boot into recovery mode and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Or edit /etc/X11/xorg.conf

```
nano -Bw /etc/X11/xorg.conf
```
and replace "nv" with "vesa" for the driver.

```
Driver     "vesa"
```
Save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by DarthWHO on 2007-05-08
Thanks taurus, should be doing this tonight so I'll see how it goes.

---

### Post by Efros on 2007-05-08
will this procedure work in Feisty? I'm about to recieve a new FX7300 and want to replace my current fx5200 with it.

---

### Post by taurus on 2007-05-08
> **Efros said:**
> will this procedure work in Feisty? I'm about to recieve a new FX7300 and want to replace my current fx5200 with it.

Yes.

---

### Post by Efros on 2007-05-08
ta muchly, will be doing this on friday along with some new memory and an extra 1.5 Tb HD... I'm excited!!!

---

### Post by Efros on 2007-05-10
card arrived early, installed it couldn't enable restricted drivers, did a bit of scrabbling about and  finally used envy to get everything working peachy

---

### Post by gsiliceo on 2007-05-11
Hi, i have the exact same problem as the original poster, what line should i change to "nv"
thats the section in my xorg.config that i think i need to change, im just not sure about the Identifier and Bus Id.

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

---

### Post by Xeor on 2007-05-11
Driver "i810" --> Driver "nv"

---

### Post by gsiliceo on 2007-05-11
didn't work, and neither "nvidia" did, im afraid i'll have to reinstall ubuntu :(

---

### Post by taurus on 2007-05-11
Boot into recovery mode and reconfigure your X with

```
dpkg-reconfigure xserver-xorg
```

---

