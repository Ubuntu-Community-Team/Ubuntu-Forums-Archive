---
title: "Clipboard Issues"
date: 2007-05-24
forum: General Help
---

### Post by syko21 on 2007-05-24
Every time i copy text from one window and accidentally close it the copied text doesn't paste. Is there a way to make it stay in the clipboard (or wherever it is recently switch from windows so I'm using the only terminology i know so far) after the window is closed?

---

### Post by earobinson on 2007-05-24
Your terminology is perfect. This is done as a security feature, but you can install glipper if you like and this will let you cut from one app, close the app, then paste to another app. > A clipboard manager for GNOME and other window managers
Enables multiple virtual clipboards in Gnome and other window managers
that support tray icons. Click the tray icon to select from a list of
previous clipboard entries. Supports a configurable number and length
of clipboard entries and saving clipboard history on exit.

Homepage: [http://glipper.sourceforge.net/](http://glipper.sourceforge.net/)

This program can be installed by searching for it in synaptic or in the terminal using ```
sudo apt-get install glipper
``` I found this app by searching synaptic for (gnome clipboard)

---

### Post by syko21 on 2007-05-24
whoa that was a quick reply, thanks worked like a charm

---

### Post by earobinson on 2007-05-25
Not a problem, glad to help. Synaptic search is your friend.

---

### Post by Arjunanda on 2007-06-01
Great and long awaited tool!

---

### Post by dovael on 2007-06-17
In the beginning using Ubuntu Feisty I installed glipper from Applications and it worked for a few days but then it stopped and I could not address its menu. I purged and installed it a few times again without success. In the terminal I got this note:
(process:7054): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed
I also tried to install klipper and again the icon didn't show a menu. Any suggestions?

---

### Post by earobinson on 2007-06-19
sounds like a bug, please report it! kipper wont work cuz its for kde

---

### Post by wpshooter on 2007-06-19
> **earobinson said:**
> Your terminology is perfect. This is done as a security feature, but you can install glipper if you like and this will let you cut from one app, close the app, then paste to another app. 

This program can be installed by searching for it in synaptic or in the terminal using ```
sudo apt-get install glipper
``` I found this app by searching synaptic for (gnome clipboard)

What version of Ubuntu are you using ?  I do not seem to be able to find this in Edgy.

P. S. - I find klipper but not glipper.  Can klipper be used successfully under Ubuntu/gnome ?

Thanks.

---

### Post by energiya on 2007-06-19
I use [gnome-clipboard-daemon]("http://members.chello.nl/~h.lai/gnome-clipboard-daemon/"). It works fine and doesn't stay in my way It's just a daemon remembering the last copy/cut, no GUI. (Don't install both glipper and gnome-clipboard-daemon). I think I'll take a look at glipper.

---

### Post by wpshooter on 2007-06-19
> **energiya said:**
> I use [gnome-clipboard-daemon]("http://members.chello.nl/~h.lai/gnome-clipboard-daemon/"). It works fine and doesn't stay in my way It's just a daemon remembering the last copy/cut, no GUI. (Don't install both glipper and gnome-clipboard-daemon). I think I'll take a look at glipper.

There must be something I am missing about this gnome clipboard-daemon, because then I download the binary per the instructions on the site and try to run, the command never seems to complete in the terminal and then when I try to copy and paste **NOTHING** happens ???

Thanks.

---

### Post by energiya on 2007-06-20
> **wpshooter said:**
> There must be something I am missing about this gnome clipboard-daemon, because then I download the binary per the instructions on the site and try to run, the command never seems to complete in the terminal and then when I try to copy and paste **NOTHING** happens ???

Thanks.

Tou could try downloading the source...
```

wget http://members.chello.nl/~h.lai/gnome-clipboard-daemon/clipboard-daemon-1.0.tar.bz2
tar xf clipboard-daemon-1.0.tar.bz2 
cd clipboard-daemon-1.0 
make
clipboard-daemon

```
It should not close imediatly, but stay opened in console. If it closes... check if you have any other clipboard manager opened and close it. If it still doesn't run, I don't know.

If you want to install it, cd to the source directory and
```

sudo make install

```
after that, to uninstall
```

sudo make uninstall

```

Don't forget to put it at startup if you like it.

Hope this helps.

---

