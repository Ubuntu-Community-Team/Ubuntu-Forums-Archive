---
title: "[SOLVED] GUI for xorg.conf"
date: 2008-03-24
forum: General Help
---

### Post by MountainX on 2008-03-24
I'm trying to configure my Trackpoint for scrolling. I found [one article that spoke about using SAX2]("http://opseast.wordpress.com/2007/11/05/getting-the-thinkpad-scroll-button-to-work-in-linux/") for this.

He says, "I have recently discovered that you can also use sax2 to setup the scrolling capability.  Fire up /usr/sbin/sax2."

Well, that didn't work for me in Gutsy, and after a lot of searching I see nothing but confusing and conflicting info.

Where do I get SAX2 for Gutsy? Thanks.

(Also, will it help me solve [this problem]("http://ubuntuforums.org/showthread.php?t=734358")? )

---

### Post by pointone on 2008-03-25
SaX2 is a module for YaST, which is the system management tool used by SUSE/openSUSE.

It's source is available [here]("http://en.opensuse.org/YaST/Development"), but I doubt it would work on Ubuntu.

The [yast4debian]("http://yast4debian.alioth.debian.org/") project is probably exactly what you want, but it seems to have died off.

Just for kicks, post the rest of those instructions given for setting up scrolling with SaX2. It may be possible to run these commands on an openSUSE system and see what changes are made to the xorg.conf, or at the very least try to imagine. You could also try setting it up in the openSUSE live CD environment.

---

### Post by MountainX on 2008-03-25
I just got a solution for my trackpoint scrolling here:
[http://ubuntuforums.org/showthread.php?t=730045](http://ubuntuforums.org/showthread.php?t=730045)

Thank you for the information about SaX2. 

Did you see this?
[http://digg.com/linux_unix/Ubuntu_getting_Xorg_conf_GUI](http://digg.com/linux_unix/Ubuntu_getting_Xorg_conf_GUI)

Check out this one comment. (I'm not sure why that info is on Digg but seemingly nowhere to be found here on UbuntuForums.org.)

I hate to be the bearer of bad news but the implementation of Xorg 7.3 into Ubuntu will be delayed until Gutsy+1 (see [https://blueprints.launchpad.net/ubuntu/+spec/xorg7.3](https://blueprints.launchpad.net/ubuntu/+spec/xorg7.3) ). Since displayconfig-gtk requires Xorg 7.3 as a dependency (according to this launchpad spec sheet [https://blueprints.launchpad.net/ubuntu/+spec/displayconfig-gtk](https://blueprints.launchpad.net/ubuntu/+spec/displayconfig-gtk) ) there is a chance that this GUI will be removed by release time in October. Some of the features of the Xorg GUI covered in TFA depend on Xorg 7.3, such as testing multiple resolutions on the fly without requiring a complete restart of X. Notice how TFA says this feature is "alpha and buggy"...that's because it hasn't even been implemented yet!

Hopefully (and I never thought I'd say this) Gutsy will be delayed just a week a longer to squeeze in Xorg 7.3 and make these sorely needed features available in the next release of Ubuntu, rather than next April. After all, the new Xorg release only missed the feature freeze mark by a week and half.

---

### Post by alexforcefive on 2008-03-25
> **MountainX said:**
> Did you see this?
[http://digg.com/linux_unix/Ubuntu_getting_Xorg_conf_GUI](http://digg.com/linux_unix/Ubuntu_getting_Xorg_conf_GUI)

Check out this one comment. (I'm not sure why that info is on Digg but seemingly nowhere to be found here on UbuntuForums.org.)

Hang on, why do I have this in 7.10? Did I install it, or was it included in an update or something? Go to system > administration > screens and graphics

It's not working on my computer, anyway. It thinks I'm running vesa drivers with my screen at 640*480... :confused:

---

### Post by MountainX on 2008-03-25
That's interesting. Maybe it came from an update.

---

### Post by chewearn on 2008-03-25
This was included in Gutsy since it's release (Oct 07).  However, afaik, it's not 100% functional.

---

### Post by dcstar on 2008-03-25
> **AstalaVista said:**
> This was included in Gutsy since it's release (Oct 07).  However, afaik, it's not 100% functional.

And it can produce some strange outcomes if you play with it!

You can make the dpkg-reconfigure sort of GUI with the following:

```
sudo dpkg-reconfigure debconf
```

and select "Gnome", then in a terminal inside Gnome the:

```
sudo dpkg-reconfigure xserver-xorg
```

will have nice drop down boxes etc.

---

