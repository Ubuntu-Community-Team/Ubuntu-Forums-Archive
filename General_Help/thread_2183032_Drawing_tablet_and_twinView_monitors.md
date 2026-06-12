---
title: "Drawing tablet and twinView monitors"
date: 2013-10-23
forum: General Help
---

### Post by J_Me on 2013-10-23
I'd like to configure my drawing tablet so that it spans only one monitor and not two(I'm using twinView from nvidia)
Did some searching and found this [http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978) but it's a little outdated, so before I start messing with things thought I'd better ask if there are any other alternatives.
I'm running kubuntu 12.04 with an nvidia graphics card
TIA

---

### Post by Favux on 2013-10-23
Hi J_Me,

Welcome to Ubuntu forums!


I gather you have a Wacom tablet?  Don't know if the KDE Wacom configuration gui applet assists with monitor placement like the Gnome version does:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools)

You are correct and that thread is outdated.  A new xsetwacom parameter was added called MapToOutput.  If the gui configuration applet doesn't do the job that is what you would want to use.
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up)

---

### Post by J_Me on 2013-10-23
Thanks for the reply Favux
I should have mentioned the tablets make, it's not a wacom but a Aiptek
[http://www.amazon.com/Aiptek-Slim-12-1-Inch-Tablet/dp/B000RAHUOW](http://www.amazon.com/Aiptek-Slim-12-1-Inch-Tablet/dp/B000RAHUOW)
Also I should have searched apt-get kde wacom as it returns "kde-config-tablet" which works like a charm
Thank for the help

---

### Post by Favux on 2013-10-23
Good!  :)

For completeness' sake instructions on how to do it through the command line for non-wacom tablets are at the [Multi-Monitor HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112852").

---

