---
title: "Suspend button"
date: 2006-12-03
forum: General Help
---

### Post by ekerazha on 2006-12-03
Hi,
I can suspend (standby) my PC from the GDM menu, but I don't have the Suspend button on the shutdown panel of GNOME (I've it on another system).

I could I add that button? Thanks.

---

### Post by speedman on 2006-12-03
You can create a suspend script and add a launcher to the gnome panel for one click suspend as follows.

mkdir ~/bin

vi ~/bin/gnome-suspend

Insert the following:

#/bin/bash

dbus-send --session \
          --dest=org.gnome.PowerManager \
          --type=method_call \
          --print-reply \
          --reply-timeout=2000 \
          /org/gnome/PowerManager \
          org.gnome.PowerManager.Suspend

Save the file and make it executable:

chmod +x ~/bin/gnome-suspend

Add a custom launcher to your gnome panel and point it at ~/bin/gnome-suspend, choose an icon and you'll be set.


Regards,

SM

---

### Post by ekerazha on 2006-12-03
Yeah this is a workaround... so is the "button lacking" from the quit panel a bug of Ubuntu?

---

### Post by speedman on 2006-12-03
The suspend option appears for me when logging out of Gnome on edgy, but I use the method I described above for a quicker means to suspend my laptop.

Using the suspend option from the log out menu is a minimum of three clicks, my method is one click. :) 


Regards,

SM

---

### Post by ekerazha on 2006-12-03
> **speedman said:**
> The suspend option appears for me when logging out of Gnome on edgy, but I use the method I described above for a quicker means to suspend my laptop.

But on my laptop with Edgy I've the "Suspend" button on the quit panel of Gnome... no need to logout to GDM before suspending.

---

### Post by speedman on 2006-12-03
You've lost me.  Your first post states you don't have the option, but now you state you do.  Care to rephrase your question?


Regards,

SM

---

### Post by Rui Pais on 2006-12-03
> **ekerazha said:**
> Hi,
I can suspend (standby) my PC from the GDM menu, but I don't have the Suspend button on the shutdown panel of GNOME (I've it on another system).

I could I add that button? Thanks.

Hi, 
try launch gconf-editor and go to:
/apps/gnome-power-manager

and check if the entry 'can_suspend' checkbox have a checked mark.

---

