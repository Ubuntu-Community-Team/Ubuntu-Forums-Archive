---
title: "Running compiz on :0 as well as :1"
date: 2008-06-13
forum: General Help
---

### Post by kprateek88 on 2008-06-13
I have been using Compiz on my laptop for a long time without problems, always on (:0, vt7). A simple "compiz --replace" starts compiz normally. Today I logged in as a different user, on (:1, vt9), and tried starting compiz (compiz was running on (:0, vt7) all the time). This is what happened:

```

$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

This is an Acer Aspire 4720 with an Intel Graphics card:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

What is happening?

---

### Post by pytheas22 on 2008-06-13
I read about a year ago that it was impossible for various reasons to run more than one instance of compiz at a time.  Consequently, you can't have more than one user using desktop effects at the same time.  As far as I know, this is still the case, so I'd imagine that's why it won't work for you.  You'll have to kill compiz for the first user before the second user can have it.

---

### Post by Forlong on 2008-06-14
It is possible by now to run Compiz on multiple users, but unfortunately not on an intel chip.

---

### Post by kprateek88 on 2008-06-14
> **Forlong said:**
> It is possible by now to run Compiz on multiple users, but unfortunately not on an intel chip.
I see... and here I was thinking that an Intel chip is my best bet since it has open source drivers.

---

### Post by Forlong on 2008-06-14
Well, you wouldn't expect an onboard chip to be powerful enough to run two 3D fullscreen games at a time, though, would you?

---

### Post by n2dabloo on 2008-06-30
I suspect my problem is with: no rendering? How do I install the correct driver to get my Intel card to work with Compiz?, Thanks in advance.  
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card.

---

### Post by pytheas22 on 2008-06-30
> I suspect my problem is with: no rendering? How do I install the correct driver to get my Intel card to work with Compiz?, Thanks in advance.
Gathering information about your system...

Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
Driver in use: vesa
Rendering method: None

Checking if it's possible to run Compiz on your system... [SKIP]

Checking for hardware/setup problems... [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) y

The vesa driver is not capable of running Compiz, you need to install the
proper driver for your graphics card.

You're using the vesa driver for some reason, not Intel.  vesa is the generic fallback driver that only supports basic rendering.  I don't know how you ended up on vesa--there may be some other problem that needs to be addressed--but here's what to do to try to force the system to use the advanced driver:

Open up a terminal and open your xorg.conf with:
```

sudo gedit /etc/X11/xorg.conf
```

then look for a section that says:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

and add a line to that section so that it says:

```

Section "Device"
	Identifier	"Configured Video Device"
        Driver  "intel"
EndSection
```

then save the file, log out of Gnome and log back in.  Hopefully compiz will be working.

---

