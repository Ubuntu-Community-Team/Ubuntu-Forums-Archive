---
title: "Where are my printer options??"
date: 2008-07-01
forum: General Help
---

### Post by Master_T on 2008-07-01
Hi guys....

Don't know if this is the correct place to post, but I didn't see any printing-related subforum.

SO here is the problem:

I went to the HP website and downloaded linux drivers for my HP PSC 1410, the page redirected here:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

so I downloaded and installed the package, all seemed to be fine, the printing itself works ok.

But the problem is: there are no advanced printing options.

I'll explain: on Windows, when I click the "proprieties" button next to the printer name before printing something it poops up a nice menu full with options and tweaks (page order, back/front printing settings, special paper settings, advanced color and ink settings, etc...)

If I click the same button in kubuntu 8.04 a different menu appears, which is much more limited, basically it only lets you choose printing resolution and if you want to print in color or grayscale.

Is it just that the linux driver has less options than the widnows one or is there a  different way to set advanced options???

Master_T

---

### Post by drs305 on 2008-07-01
Do you have cupsys installed on your computer. I have the hplip and cupsys and if I open my crowser link to "http://localhost:631/" I get a full menu of options. It could be your particular driver doesn't support more advanced options but I'm using a five year old HP and get a variety of options.

---

### Post by Master_T on 2008-07-09
> **drs305 said:**
> Do you have cupsys installed on your computer. I have the hplip and cupsys and if I open my crowser link to "http://localhost:631/" I get a full menu of options. It could be your particular driver doesn't support more advanced options but I'm using a five year old HP and get a variety of options.

I'll check it out asap and let you know if it works.... thx

---

### Post by Erlander on 2008-07-09
You could also look at System/Administration/Printing in the menus.

---

### Post by ramjet_1953 on 2008-07-09
If you want to use all of the facilities of HPLIP, you will also need to install the [COLOR="Blue"]python QT3 binding[/COLOR]s.

[COLOR="Red"]sudo apt-get install python-qt3[/COLOR]

Or use Synaptic to do the same.

Once this is done, follow this sequence.

1. In a terminal type in this:

[COLOR="#ff0000"]sudo hp-setup[/COLOR]

A window will open and guide you through setup.

2. In a terminal type in this:

[COLOR="#ff0000"]hp-toolbox[/COLOR]

A window will open, giving you access to all of the goodies, such as print head alignment, ink levels, and page setup.

You can easily make an entry in your menus, by using [COLOR="Blue"]System>Preferences>Main Menu[/COLOR]

Regards,
Roger :cool:

---

