---
title: "install package"
date: 2008-04-16
forum: General Help
---

### Post by hashi856 on 2008-04-16
I downloaded a tar.gz package from gnome-look.org, but can't figure out how to install it. It's a desklet called cal.I've seen the "how to install anything on Ubuntu" site, but can't find the package on synaptic. Where can I get instructions on how to install tar.gz packages?

---

### Post by antemon on 2008-04-16
what exactly is it?
GDM theme? Metacity? Dexklet? etc etc?

---

### Post by nicedude on 2008-04-16
Since you said it came from gnomelookorg I am gonna go out on a limb here and assume you download a new theme, icon set  or login screen for your Gnome Desktop. If so these types of files are not installed via synaptic or an apt-get, they are actually simple to install but use a different method. For themes & IconSets you right click on the desktop and select "change desktop background" this will open a GUI window next select the tab THEMES and you should see some standard themes to choose from, now just drag your new theme file you downloaded onto that window and release it, then select it from the theme list - thats it for installing a theme. If your trying to install a new password login screen its different for these files you open a terminal window and type "sudo gdmsetup" without the quotes (sudo is for root privilege so type your password when asked) this will bring up another GUI window just select the tab named "local" and you will see a list of login screens already installed, now just drag your new login screen file onto that window and release it and it will be installed. Just remember the gdmsetup command since whenever you want to change your login you go there to select what login screen you want to use.

well if you are talking about something other than themes & logins, my bad :-)   if you are then thats your answer. hope this helped you out.

---

### Post by hashi856 on 2008-04-16
> **antemon said:**
> what exactly is it?
GDM theme? Metacity? Dexklet? etc etc?

a desklet

---

### Post by DarkWater on 2008-04-16
First you should probably untar it.

tar xvzf /path/to/file.tar.gz

---

