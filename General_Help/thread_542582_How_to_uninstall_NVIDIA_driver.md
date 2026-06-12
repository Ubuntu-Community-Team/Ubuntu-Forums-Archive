---
title: "How to uninstall NVIDIA driver?"
date: 2007-09-04
forum: General Help
---

### Post by durkhrod chogori on 2007-09-04
I installed the latest NVIDIA driver with Mint but the font rendering was crap so I decided to uninstall the driver but in the process it crashed and rendered my distro unusable. Well Envy was the proggie I usec for that process.

Well I believe that this freaking NVIDIA driver is what is causing Ubuntu Feisty to display my fonts with a green halo and a green vertical line inside boxes.

I want to uninstall the updated NVIDIA driver if possible before to the old state of things, when my fonts looked good in this box.

Cheers.

---

### Post by jim_p on 2007-09-04
Where did you install the drivers from?
If you did it through synaptic, you can go back there and uninstall them and install them back.

If that does not work, try to change the drivers used by your system from nvidia's to ubuntu's ones
(like ...rollback drivers in windows) 
```
sudo dpkg-reconfigure xserver-xorg
```

Go through the process, there is lots of explaination provided, and when it comes to
picking up a driver, choose "nv" instead of "nvidia" (or vice versa)

---

### Post by Steve1961 on 2007-09-04
If you used the nvidia provided driver (I think that's what envy installs), once you've reconfigure xorg to use the nv driver just type the following in a terminal to uninstall the nvidia driver:

sudo nvidia-installer --uninstall

---

### Post by durkhrod chogori on 2007-09-04
Hi guys,

Don't know why but ENVY crashed my distro and now the green dots appear even in the BIOS fonts and when you first log on in your computer.

How do I fix this? Still by entering those commands you just told me.

Thanks a lot.

---

### Post by anaconda on 2007-09-04
well.. actually you dont really need to uninstall it. Just dont use it. 

One way to change back to the orginal free nvidia driver is to edit the xorg.conf -file and change the Driver from "nvidia" to "nv"

```
gksudo gedit /etc/X11/xorg.conf 
```

and search for this:
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"

and change it to :
Section "Device"
    Identifier     "Videocard0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"

save and then reboot (or press Ctrl-Alt-Backspace)

---

### Post by anaconda on 2007-09-04
> **durkhrod chogori said:**
> Hi guys,

Don't know why but ENVY crashed my distro and now the green dots appear even in the BIOS fonts and when you first log on in your computer.

How do I fix this? Still by entering those commands you just told me.

Thanks a lot.

Huh.. taht sounds interesting! The driver you use should have NO effect in your BIOS, because the driver isn't even loaded yet..

Hmm.. check that your displaycable is properly connected from both ends, and that your videocard is properly in its place.

---

### Post by durkhrod chogori on 2007-09-04
> **anaconda said:**
> Huh.. taht sounds interesting! The driver you use should have NO effect in your BIOS, because the driver isn't even loaded yet..

Hmm.. check that your displaycable is properly connected from both ends, and that your videocard is properly in its place.

I got this:

[B]Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Driver		"nv"
	BusID		"PCI:3:0:0"[/B]

Do I change this stuff?

///////////////////////////////////////////

I am using a laptop. Very compact and nothing loose in here.

Hmm. I know is bizarre, but I don't understand how uninstalling NVIDIA using ENVY crashed my computer and left that green garbage.

Thanks.

---

### Post by anaconda on 2007-09-04
> **durkhrod chogori said:**
> I got this:
[B]Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Driver		"nv"
	BusID		"PCI:3:0:0"[/B]

Do I change this stuff?

No, since you already have the "nv" driver, which is the what you want (its the default opensource free driver).  

"nvidia" is the restricted closed source driver, which would handle 3D acceleration better, but which didn't work for you.

---

