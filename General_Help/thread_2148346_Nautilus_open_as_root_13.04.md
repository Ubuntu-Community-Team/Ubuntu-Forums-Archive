---
title: "Nautilus open as root 13.04"
date: 2013-05-24
forum: General Help
---

### Post by SteveDeFacto on 2013-05-24
Thunar has the ability to add custom actions and other file [FONT=arial, sans-serif][SIZE=2][COLOR=#444444]browsers like PCManFM have the ability to open a folder as root. Where is this functionality in Nautilus? I see there use to be an extension called nautilus-gksu but the package is not in the repositories anymore. I've tried a few different guides on how to get this functionality in [/COLOR][/SIZE][/FONT][COLOR=#444444][FONT=arial]Nautilus but I have yet to find anything that works. I also tried the custom action extension for [/FONT][/COLOR][COLOR=#444444][FONT=arial]Nautilus but it does not appear to do anything.[/FONT][/COLOR]

---

### Post by Frogs Hair on 2013-05-24
Gnome keeps removing features and  you can restore some functionality with the following patch . It is likely the package [COLOR=#444444][FONT=arial]nautilus-gksu no longer works with the current version.[/FONT][/COLOR]   [http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)[COLOR=#444444][FONT=arial] [/FONT][/COLOR]

---

### Post by SteveDeFacto on 2013-05-24
> **Frogs Hair said:**
> Gnome keeps removing features and you can restore some functionality with the following patch . It is likely the package [COLOR=#444444][FONT=arial]nautilus-gksu no longer works with the current version.[/FONT][/COLOR][http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)
That fixed a few other problems I was having too! Thanks!

---

### Post by HiImTye on 2013-05-24
you could achieve this with a nautilus script

---

### Post by mc4man on 2013-05-24
Here I just use nautilus-actions as described in latter part of this post, in that case creating/using pkexec to implement.
( for better, worse or in between.
I guess you could install gksu & use gksudo in the nautilus-actions(s) instead of the pkexec deal ,I've had no issue with pkexec
[http://ubuntuforums.org/showthread.php?t=2138386&p=12625733&viewfull=1#post12625733](http://ubuntuforums.org/showthread.php?t=2138386&p=12625733&viewfull=1#post12625733)

---

### Post by cpsureshmpm on 2013-10-15
Just use Nautilus-Action script to implement this.
  
Install gksu and nautilus-actions from the Software Centre
Then open the Nautilus-Action Configuration Tool

In the Nautilus-Action Configuration Tool create a new action
In the Action tab, type '*Open Folder As Root*' in the Context label
In the Command tab, input the values '***gksu***' and '***nautilus %d/%w***' in Command Path and Parameters respectively.
Then Restart nautilus : *nautilus -q*

[ATTACH=CONFIG]246969[/ATTACH]        [ATTACH=CONFIG]246967[/ATTACH]       
[ATTACH=CONFIG]246970[/ATTACH]

---

### Post by stinkeye on 2013-10-15
If you use xdg-open you can open folders or text files as root with your preferred application.

---

