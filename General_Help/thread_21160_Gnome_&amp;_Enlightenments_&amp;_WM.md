---
title: "Gnome &amp; Enlightenments &amp; WM"
date: 2005-03-20
forum: General Help
---

### Post by helmoltz on 2005-03-20
I wish to use gnome with enlightenment or other window manager. I have installed but I can't change metacity with other wm. Can someone help me?
I have installed also selectwm and wmanager, but for now I can't disable metacity.
Thanks

---

### Post by trilliji on 2005-07-14
I'm running this on gentoo, and Ubuntu is my stable machine and haven't done it there. I think this is generic to gnome and not to a specific distribution. Here are a few suggestions to try.

Create a new user to try this out. Once you have everthing working, repeat for the desired user.

System>Preferences>Sessions [Session Options]

Make sure either 'Ask on logout' or 'Automatically save changes to session' are checked. You need to be able to do this because you will be changing the session.

System>Preferences>Sessions [Current Session]

Locate metacity in the list and click on it. Change the Style to normal. Click Apply.

Open up a terminal window.

killall metacity && sleep 1 && enlightenment

( Or replace enlightenment which whatever enlightenment version you want to run )

System>Preferences>Sessions [Current Session]

Locate enlightenment in the list and click on it. Make sure it's order is set to 20 and Style is set to restart. Click Apply.

Close your terminal window. When you do this enlightenment should terminate and a new copy should be restarted.

Nautilus and enlightenment argue about the root window. You may or may not want to do this step, as it disables the drawing of the files from the desktop and automounting CD's and having the icon appear on the desktop. You might want to try it both ways.

System Tools>Configuration Editor

Apps-Nautilus-Preferences 

Uncheck the show_desktop preference.

Logout. If you used 'Ask on logout' about, make sure to check the checkbox to to save the session.


Note that e17 and gnome handle transparency differently. e17 uses true transparency and gnome uses pseudo-transparency. So using transparency with gnome will not naturally work right. You will need to issue a:

e17setroot -s <background filename>

To fix things up. 

This isn't perfect, but what I have figured out so far, I hope it gets you started.

There are resources at [http://www.get-e.org](http://www.get-e.org) to help you out more, including e-themes.

I hope you enjoy the Enlightened Gnome :)

---

### Post by trilliji on 2005-07-14
Note: One other setting might be helpful.

System Tools>Configuration Editor

Apps-panel-global

Set enable_animations to unchecked

---

### Post by ubuntuuser on 2005-08-01
You could type ```
windowmanagernamehere --replace 
``` at the command line. Type ```
metacity --replace 
``` to get metacity back.

---

