---
title: "&quot;Ubuntu software&quot; dosn't start"
date: 2020-04-29
forum: General Help
---

### Post by asb3 on 2020-04-29
A few days ago I did a clean install of Ubuntu 20.04.
One of the icons that appears on the dash is the orange Ubuntu Software.
When I click on it, I get the "busy" icon for a few seconds, and nothing else happens.
How can I debug it?

Related question: How can I find the action taken when I click on an icon in the dash? If I place the cursor over an icon I get the name of the application, but that's not the same as the equivalent terminal command: "Ubuntu software" is not a terminal command.

---

### Post by ActionParsnip on 2020-04-29
Firstly, let updates and so forth finish. If there are no updates running or packages installing then reboot. If this doesn't work then run:

```

sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a

```

This will unlock the packages for you. You can then run:

```

sudo apt update && sudo apt upgrade

```

This should now be smooth

---

### Post by Dennis N on 2020-04-29
In default Ubuntu 20.04, 'Ubuntu Software' icon opens a snap version of Gnome Software. If you have trouble with this snap, you have the option of installing with apt the version of Gnome Software from the Ubuntu Repository. 

The snap version package of Gnome Software is named **snap-store**. Remove it.
```
snap remove snap-store
```
then install Gnome Software from the Ubuntu Repository:
```
sudo apt install gnome-software
```
The Software Store is now named 'Software' in your Application search.

In the 20.04 Ubuntu Repository, ubuntu-software can still be installed, but it just a transitional package to install gnome-software, so you would get the same result.

---

### Post by asb3 on 2020-04-29
Thanks for the response.
No snap applications work on my installation; they all fail with the "unable to access directory" error message.
I removed snap-store and installed gnome-software, and it works.

I'd still like to know how to find the command run when an icon in the dash is clicked.

---

### Post by Dennis N on 2020-04-29
> I'd still like to know how to find the command run when an icon in the dash is clicked. 
You would have to look at the .desktop file to see the actual command that's executed. Look for the line Exec= in the .desktop file. Those are in **/usr/share/applications** for things installed by apt from the repos. For snap packages, they are in **/var/lib/snapd/desktop/applications**.
```
dmn@Sydney-vm:/var/lib/snapd/desktop/applications$ ls
atari800-jz_atari800.desktop               libreoffice_draw.desktop
chromium_chromium.desktop                  libreoffice_impress.desktop
gnome-calculator_gnome-calculator.desktop  libreoffice_libreoffice.desktop
gnome-characters_gnome-characters.desktop  libreoffice_math.desktop
gnome-logs_gnome-logs.desktop              libreoffice_writer.desktop
libreoffice_base.desktop                   mimeinfo.cache
libreoffice_calc.desktop                   snap-store_snap-store.desktop

```
Exec commands for installed snaps are usually more complex.
For Gnome Characters:
```
Exec=env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/gnome-characters_gnome-characters.desktop /snap/bin/gnome-characters

```

---

