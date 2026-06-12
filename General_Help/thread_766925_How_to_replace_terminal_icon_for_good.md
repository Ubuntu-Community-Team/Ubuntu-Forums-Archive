---
title: "How to replace terminal icon for good?"
date: 2008-04-25
forum: General Help
---

### Post by orbital on 2008-04-25
I have installed a new icon set but when I click on gnome terminal I get the ugly old icon. Where should I copy the new gnome terminal icon so I get rid of the old one for good?

---

### Post by Stochastic on 2008-04-25
Sounds like you installed an incomplete icon set or at least one that wasn't built for your release of Ubuntu.  The best way to solve this would be to take the icon set you downloaded, untar it to a folder for you to work on, COPY (don't move) your default icon set to a similar location (you'll find it in /usr/share/icons/).  Then go through the contents of the default icon set systematically looking for the terminal icons.  You'll notice that quite a few of the icons are symbolic links to a similarly named icon.  My guess is that your new icon set either doesn't have the resolution of the terminal icon in place, or it's missing one of the symbolic links.  Fix whatever inconsistencies you find, retar the folder and reinstall the new theme.  You may also want to take some notes as you do this and submit your changes back to the original icon set maintainer so others won't have to go through all this hassle.  Hope this helps a bit, let me know if you get stuck.

---

### Post by orbital on 2008-04-25
The problem is that after installing any icon set, when I click on terminal, it shows up on Avant window navigator with the _old_ icon. The _new_ icon is being used in the applications menu as well as the desktop panel. Any idea how to get this working?

---

### Post by Stochastic on 2008-04-25
Oh, then it should be as simple as right clicking the icon in AWN, going into preferences (though I'm not an AWN user so you may need to go to the settings section and then to your launcher's preferences).  Once there you should see an icon that you can click on and change what icon is used for your launcher.  If that doesn't solve the icons in your listing of windows open too, then your only remaining option would be to go searching in /usr/share/icons/ (probably in gnome icon set) for the offending old terminal icon, and manually replace it - this is kinda overkill though and I'd suggest renaming the old icons rather than deleting to prevent "permanent damage".

---

