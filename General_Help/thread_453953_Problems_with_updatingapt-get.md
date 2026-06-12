---
title: "Problems with updating/apt-get"
date: 2007-05-24
forum: General Help
---

### Post by woopud on 2007-05-24
I just changed from "regular" Feisty to Ubuntu Studio which all went fine until I got available updates.  It gave me the following message: 

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So I open up a terminal and do the following:

```
woopud@woopud-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 lmms galan mx44 cheesetracker gnome-bin rezound kaconnect
  libgtk-canvas1 libsdl-gfx1.2-4 fftw2 spiralsynthmodular libgnome32 gnusound
  ardour-gtk lmms-common gnome-libs-data ecamegapedal om libart2 specimen
  libgnorbagtk0 qmidiroute gdk-imlib1 kluppe libscsynth1 qmidicontrol
  gcc-3.4-base horgand libphat0 ams libsdl-sound1.2 qmidiarp qsampler solfege
  libgnomeui32 libdb3 qarecord sfftw2 libgdk-pixbuf2 freewheeling imlib-base
  ardour-session-exchange gmorgan amsynth liborbit0 gdk-imlib11 libgig3c2
  soundstretch python-ecasound2.2 libgnomesupport0 ecasound libclalsadrv1
  libg2c0 supercollider sweep libsclang1 libfox1.4 soundtracker liblscp
  libgnorba27
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ardour
The following NEW packages will be installed:
  ardour
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
4 not fully installed or removed.
Need to get 0B/4968kB of archives.
After unpacking 17.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 131201 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
woopud@woopud-desktop:~$ 


```

What did I do wrong ?

Bert

---

### Post by mbradlcu on 2007-05-25
can you un-install ardour-gtk first?
```
sudo apt-get remove ardour-gtk
```

---

### Post by woopud on 2007-05-25
Tried that, gave me the same problem.

```
woopud@woopud-desktop:~$ sudo apt-get remove ardour-gtk
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ubuntustudio-audio: Depends: ardour
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
woopud@woopud-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 lmms galan mx44 cheesetracker gnome-bin rezound kaconnect
  libgtk-canvas1 libsdl-gfx1.2-4 fftw2 spiralsynthmodular libgnome32 gnusound
  ardour-gtk lmms-common gnome-libs-data ecamegapedal om libart2 specimen
  libgnorbagtk0 qmidiroute gdk-imlib1 kluppe libscsynth1 qmidicontrol
  gcc-3.4-base horgand libphat0 ams libsdl-sound1.2 qmidiarp qsampler solfege
  libgnomeui32 libdb3 qarecord sfftw2 libgdk-pixbuf2 freewheeling imlib-base
  ardour-session-exchange gmorgan amsynth liborbit0 gdk-imlib11 libgig3c2
  soundstretch python-ecasound2.2 libgnomesupport0 ecasound libclalsadrv1
  libg2c0 supercollider sweep libsclang1 libfox1.4 soundtracker liblscp
  libgnorba27
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ardour
The following NEW packages will be installed:
  ardour
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 0B/4968kB of archives.
After unpacking 17.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 131201 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
woopud@woopud-desktop:~$ 


```

Bert

---

### Post by mbradlcu on 2007-05-26
how about removing or moving the file the install is trying to overwrite?
/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo

---

### Post by woopud on 2007-05-26
What exactly do I have to do to manualy delete this file ?

Bert

---

### Post by mbradlcu on 2007-05-27
for safe measure I'd move it (if it does indeed exist):
```
sudo mv /usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo ~/
```
this will move the file to your home dir. If doing this causes more problems you can just move it back:
```
sudo mv ~/gtk_ardour.mo /usr/share/local/de_DE/LC_MESSAGES/
```

---

### Post by woopud on 2007-05-27
Gives me the same problem.

Bert

---

### Post by woopud on 2007-05-28
Somehow I got it fixed now, suddenly the 'autoremove" option did work after several tries.  Seems everything is okay now, thanks everybody for the suggestions.

Bert

---

