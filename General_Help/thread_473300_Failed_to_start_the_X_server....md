---
title: "Failed to start the X server..."
date: 2007-06-13
forum: General Help
---

### Post by wie6Ein0 on 2007-06-13
I was attempting to make my laptop computer display a higher resolution by entering "sudo dpkg-reconfigure xserver-xorg" into the terminal. I somehow messed everything up and I'm getting a blue screen with the following message: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <Yes> <No>"

I tried reconfiguring again to get it working again but I had no luck. Is there a way that I can just reset the xserver-xorg to the default settings? I guess I can live with a lower resolution if I can get back into the computer. Please help!

---

### Post by nymphaeles on 2007-06-13
Sign in with your user ID and password at the login prompt.  Run the same command:

```

sudo dpkg-reconfigure xserver-xorg

```

Select the right card driver, and the right resolutions.  Reboot the machine.

---

### Post by wie6Ein0 on 2007-06-13
> **nymphaeles said:**
> Sign in with your user ID and password at the login prompt.  Run the same command:

```

sudo dpkg-reconfigure xserver-xorg

```Select the right card driver, and the right resolutions.  Reboot the machine.

I keep doing that and I never get it right... I'm just going to copy the xorg.conf file from the live cd and hope that works.

---

### Post by Trueno22 on 2007-06-13
just select the vesa driver and if you have a nvidia card or ati card use envy to configure the drivers for you

---

### Post by nymphaeles on 2007-06-13
Uhmm,

I believe it is the card driver that is misconfigured.  Do you know what kind of video card you have in the machine?
When you get the right driver, typical resolutions are "1024x768" "800x600" "648x480".  You can even manually edit the /etc/X11/xorg.conf using vi

```

sudo vi /etc/X11/xorg.conf

```

---

### Post by wie6Ein0 on 2007-06-13
> **nymphaeles said:**
> Uhmm,

I believe it is the card driver that is misconfigured.  Do you know what kind of video card you have in the machine?
When you get the right driver, typical resolutions are "1024x768" "800x600" "648x480".  You can even manually edit the /etc/X11/xorg.conf using vi

```

sudo vi /etc/X11/xorg.conf

```

I guess I'm just not start enough yet... I tried, I really did! I did what I said I was going to do and copied the xorg.conf file from the live cd. Everything is working again. I also made a backup for emergencies when I don't have access to the live cd. Thanks for everything!

---

