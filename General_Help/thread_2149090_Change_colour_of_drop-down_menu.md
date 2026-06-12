---
title: "Change colour of drop-down menu"
date: 2013-05-27
forum: General Help
---

### Post by motorcity909 on 2013-05-27
Hi all

I'm using the standard Greybird theme on Xubuntu 13.04 and wondered if there was a way to change the colour of the drop-down menu - as in the drop-down from the Applications menu on the top panel?  

See attached - white background with black font - I'd prefer the background darker with a white font.

[ATTACH=CONFIG]243132[/ATTACH]


There used to be a theme that did this automatically in Xubuntu 12.04 but doesn't seem to be included now and I can't remember the name of it!

I'm wondering if the way to change it is buried somewhere in the file - /usr/share/themes/Greybird/gtk-2.0/gtkrc ??

Thanks as always
Dave

---

### Post by Dennis N on 2013-05-27
There is a small configuration tool from:

**ppa:shimmerproject/ppa**
package: **gtk-theme-config**

Customizes three things: Selected Items (text and background colors); Panel Color (text and background colors); _Menu Color (text and background colors)_. I have used it only for the panel so far, and it works for that in Xubuntu 13.04.

Once installed, shows up in your Settings dialog.
Please post back if the menu part works for you.

As to the theme with the dark grey menu background in Xubuntu 12.04, that was Greybird, which has since changed its colors.

---

### Post by motorcity909 on 2013-05-27
Hi Dennis

Thanks for your reply.  I installed gtk-theme-config on my second (test) machine.  

Sadly the menu section changes the drop down menus *within applications*, rather than the drop-down application menu from the panel.

Ah well, nevermind!

Maybe I could install Xubuntu 12.04 in V'box and get the 'old' Greybird theme from within it, then copy that into the themes folder on 13.04.

I'm sure there will be a setting within that gtkrc file but there are so many things in that, it's hard to see which might be the colour of a menu background!

Dave

---

### Post by motorcity909 on 2013-06-05
This may be helpful - just following up on the thread above.  I did indeed install 12.04 in Virtualbox and got the OLD Greybird theme and copied it over to the host 13.04 machine.   Created a .themes folder and put the old Greybird in there - named it "Greybird-1204".

It showed up straightaway with Settings Manager>Appearance>Style and I now have my black menu drop-down back.

One other change needed was it still had the old boxes around the text below desktop icons but the instructions here - [http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/](http://xubuntu.wordpress.com/2007/08/27/howto-remove-the-borders-of-your-desktop-icon-text/) - fixed that.  Old page but it still does the job.

This is another reminder of why I love Linux, Xubuntu, XFCE - it's your choice!

Cheers
Dave

---

