---
title: "Resolution"
date: 2007-03-18
forum: General Help
---

### Post by LilTricky on 2007-03-18
Ive got a 19" widescreen and it support 1440x900, i installed the gfx drivers (had problems wit the before but thanks to the peeps on here i got it working) but the resolution is set at 1024x768 and it doesnt have a resolution thats any higher in the option, ive configured the xserver to 1440x900, if i need to configure it through aticonfig can anyone tell me how???

please help!! :(

---

### Post by CocoAUS on 2007-03-18
Can you post your xorg.conf file?  Basically just the screen and monitor sections are needed.

The key to making your resolution work is simply putting in the proper HorizSync and VertRefresh rates.  Do that, make sure your resolution is included in the default depth, then restart X and you should be good to go.

---

### Post by LilTricky on 2007-03-18
> **CocoAUS said:**
> Can you post your xorg.conf file?  Basically just the screen and monitor sections are needed.

The key to making your resolution work is simply putting in the proper HorizSync and VertRefresh rates.  Do that, make sure your resolution is included in the default depth, then restart X and you should be good to go.

Im really new to Linux (noobie) how can i do that?

And i heard about this command open /etc/X11/xorg.conf or something and it says Permission deined even though im logged in as su in terminal

---

### Post by CocoAUS on 2007-03-18
This command should work to open your xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```

Then you can just copy and paste it here.

For the HorizSync and VertRefresh values, you'll just need to look it up in your monitor's manual or google for them online.  They might be called refresh rates, frequencies, etc.  You'll need to look up specifically what they are for the resolution you want to use.

---

