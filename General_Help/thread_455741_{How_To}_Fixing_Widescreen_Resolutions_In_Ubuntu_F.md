---
title: "{How To} Fixing Widescreen Resolutions In Ubuntu Feisty"
date: 2007-05-26
forum: General Help
---

### Post by mwiebelhaus on 2007-05-26
MANY PEOPLE have been having problems with [COLOR="Red"]Intel Graphics[/COLOR] in widescreen so I screwed around for a couple of days and this finally worked.

[LIST=1]
[*]Open Up Your [COLOR="Blue"]Terminal[/COLOR]
[/LIST]
[LIST=2]
[*]Copy and Paste This into your Terminal. [COLOR="Blue"]sudo apt-get install xserver-xorg-video-intel[/COLOR]
[/LIST]
[LIST=3]
[*]When this is finished [COLOR="Blue"]REBOOT[/COLOR]
[/LIST]
[LIST=4]
[*]Then go to [COLOR="Blue"]System>Preferences>Screen Resolution[/COLOR] to see all of the new options.
[/LIST]

---

### Post by JohnPhys on 2007-05-27
Many people have reported issues with that driver when compiz/beryl are enabled and watching videos using the xv driver.  The issues don't seem to be there if a composite windows manager isn't enabled.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/111257](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/111257)

---

### Post by mwiebelhaus on 2007-05-27
O.K., But this is the only solution 'ive found to get wide screen.

---

### Post by screaminj3sus on 2007-05-27
I've had the same problem no matter what card I use (Nvidia, ATI) THe only way I can get widescreen in ubuntu is Nvidia-settings, I;ve tried many other distros that have no problems with this (Suse, PClinuxOS, Mandriva) Hopefully they fix it in the next release.

---

### Post by JohnPhys on 2007-05-27
For intel chipsets, have you tried installing 915resolution?  That worked flawlessly on two different gateways with the intel graphics, both at 1280x800 and 1440x900 native resolutions.

---

### Post by mwiebelhaus on 2007-05-27
Whats the diiference though between what i did and 915 resolution?

---

### Post by jasongegere on 2007-06-26
> **mwiebelhaus said:**
> MANY PEOPLE have been having problems with [COLOR="Red"]Intel Graphics[/COLOR] in widescreen so I screwed around for a couple of days and this finally worked.

[LIST=1]
[*]Open Up Your [COLOR="Blue"]Terminal[/COLOR]
[/LIST]
[LIST=2]
[*]Copy and Paste This into your Terminal. [COLOR="Blue"]sudo apt-get install xserver-xorg-video-intel[/COLOR]
[/LIST]
[LIST=3]
[*]When this is finished [COLOR="Blue"]REBOOT[/COLOR]
[/LIST]
[LIST=4]
[*]Then go to [COLOR="Blue"]System>Preferences>Screen Resolution[/COLOR] to see all of the new options.
[/LIST]

Thank you so much for this solution this worked great for me. I have a ASUS W3000. You made my night. :popcorn:

---

### Post by glaze0101 on 2007-08-20
Thank you so much worked great, I have a Fujitsu A6030 1280x800
-glaze0101

---

