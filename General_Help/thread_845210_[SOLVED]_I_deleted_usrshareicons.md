---
title: "[SOLVED] I deleted /usr/share/icons"
date: 2008-06-30
forum: General Help
---

### Post by ashkev on 2008-06-30
I somehow deleted /usr/share/icons  Where can I download the contents of this directory so I can put it back?

Thanks

---

### Post by geirha on 2008-06-30
This should list all packages that install files in that directory
```
dpkg -S /usr/share/icons
```

Reinstalling all those packages should get those files back. Something like this should do it all in one line:
```
dpkg -S /usr/share/icons | cut -d: -f1 | sed 's/,//g' | xargs sudo aptitude reinstall
```

---

### Post by ashkev on 2008-06-30
I tried that line and got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  kivio kpresenter krita kthesaurus kword libwv2-1c2 
The following packages will be REINSTALLED:
  alacarte amarok apport bluez-gnome brasero bug-buddy capplets-data 
  cervisia compizconfig-settings-manager deskbar-applet dmz-cursor-theme 
  envyng-core eog evince f-spot fglrx-control file-roller gconf-editor gdm 
  gimp-data gnome-accessibility-themes gnome-app-install gnome-applets-data 
  gnome-games-data gnome-icon-theme gnome-media-common 
  gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel-data 
  gnome-power-manager gnome-session gnome-system-tools gnome-themes 
  gnome-utils gnucash-common gucharmap hicolor-icon-theme human-icon-theme 
  jockey-common karbon kchart kdebase-data kdelibs-data kexi kfilereplace 
  kformula kghostview kicker kimagemapeditor kivio-data klinkstatus 
  koffice-data kommander kompare koshell kplato kpresenter-data krita-data 
  kspread kugar kword-data kxsldbg libdjvulibre15 liblaunchpad-integration1 
  nautilus-cd-burner nautilus-data network-manager-gnome 
  openoffice.org-common peazip pidgin-data quanta rhythmbox seahorse 
  software-properties-gtk sound-juicer synaptic tangerine-icon-theme tomboy 
  totem-common tracker transmission-gtk ubuntu-artwork update-manager 
  update-notifier vinagre xcursor-themes yelp 
0 packages upgraded, 0 newly installed, 88 reinstalled, 6 to remove and 0 not upgraded.
Need to get 109MB/162MB of archives. After unpacking 24.1MB will be freed.
Do you want to continue? [Y/n/?] Abort.
xargs: sudo: exited with status 255; aborting

```

---

### Post by geirha on 2008-06-30
Ok, stdin comes from the pipe, so we can't give it the y for yes manually, so add -y to the aptitude command to assume yes on all questions.
```
dpkg -S /usr/share/icons | cut -d: -f1 | sed 's/,//g' | xargs sudo -y aptitude reinstall
```

---

### Post by ashkev on 2008-06-30
Thanks, I am sure that would work, but I just figured out that the directory wasn't really gone, I had just changed the permissions so that I couldn't see it.  All is ok now.

Thanks

---

### Post by Superevil on 2008-08-27
It appears that the above command doesn't work

```
dpkg -S /usr/share/icons | cut -d: -f1 | sed 's/,//g' | xargs sudo -y aptitude reinstall
sudo: illegal option `-y'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ..
```.

I've tried moving the -y command at the end and I thought that would fix it but nope, I also removed the xargs line and again nothing.

---

### Post by Majiq on 2008-12-06
Uhh, I'm guessing no one really needed this (but I did!), so I just used this as a small hack-around:

```

sudo aptitude reinstall `dpkg -S /usr/share/icons | cut -d: f1 | sed 's/,//g'`

```

Yay, backticks.

---

