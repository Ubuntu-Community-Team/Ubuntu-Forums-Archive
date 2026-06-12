---
title: "Extremely large font under &quot;options&quot; menu at login"
date: 2007-03-25
forum: General Help
---

### Post by glxyjones on 2007-03-25
I am brand new to Ubuntu and I have literally spent the last two days troubleshooting everything from my wireless card drivers to beryl getting to run.  I owe a lot of gratitude to this forum for helping me with all the issues I've had. However, there is one problem I am having that I cannot seem to find any solution for. 

When I first installed Ubuntu I noticed my username and password fonts were extremely large and unreadable.  After getting the important fixes out of the way (see above) I tried to fix this one since it's more of a aesthetics problem than functional.  I read about modifying the font size in "Human.xml" file under /usr/share/gdm/themes/Human directory.  After messing with this for a little while I was able to get the font size in the username/password box to what I wanted.  However, I noticed the font size under the "options" menu in the bottom left were still huge.   No matter what font values I changed in "Human.xml" the fonts were still extremely big, to the point where one line takes up the entire screen.  I can't find and xml file or any other file that the "Human.xml" files links to for these values.  Any ideas?

---

### Post by glxyjones on 2007-03-27
any ideas?

---

### Post by seandlh on 2007-04-07
Are you using an nvidia graphics card?  I just installed edgy with a Geforce 6200 and LCD TV and saw this problem.  I was able to fix the problem with information from this bug:

[https://launchpad.net/ubuntu/+source/kdebase/+bug/37072]("https://launchpad.net/ubuntu/+source/kdebase/+bug/37072")

You can change the X server options in the System->Administration->Login Window.  Click on the security tab and then click on the Configure X Server button.  I added "-dpi 100" to the options and the problem went away.

-- Sean

---

### Post by i22yb on 2007-04-16
I'm running into the same problem.  I've got my computer plugged into a 37" HDTV and the latest Fiesty 7.04 beta boot CD gives me this same problem.  I'm assuming that Kubuntu can't detect the DPI of my TV and so I get this problem.

Is there an easy way to change the DPI setting when running from the install CD?  The fonts are so big I can't read anything when I boot from it.  Safe graphics mode doesn't help.  I have no problems if I plug in my 19" LCD monitor.  I know Kcontrol has a place to change the setting, but I can't get to it when the fonts are so large that 5 words take up the whole screen.  I'd like to not have to swap monitors all the time.  Any suggestions would be appreciated!

---

