---
title: "how do you install xfce?"
date: 2017-02-21
forum: General Help
---

### Post by juntjoo2 on 2017-02-21
I followed this guide here: [http://www.tecmint.com/install-xfce-desktop-in-ubuntu-and-linux-mint/comment-page-1/#comment-869696](http://www.tecmint.com/install-xfce-desktop-in-ubuntu-and-linux-mint/comment-page-1/#comment-869696)

and nothing happened.  

What is supposed to happen after you install it anyway?  

And what happens to "gnome", which I think I have. 

Speaking of which, how do I know if I have gnome or xfce or some other whatever these things are called?  

And is there a way to switch between the two?

If a program doesn't work for whatever reason after you've installed it in this fashion, how do you find it and take it off?

BTW I'm switching to another one of these things because something weird is happening with MS office under WINE so it was suggested I try a different one of these interface things.  

Thanks!

---

### Post by speartip on 2017-02-21
```
sudo apt install xubuntu-desktop
```
Then log out & at the login screen pick the xubuntu session.
Your gnome session should be untouched.

---

### Post by juntjoo2 on 2017-02-21
thanks, what's that, xubuntu desktop? it took a long time and seemed to install libreoffice which I believe I previously uninstalled to save space.

---

### Post by howefield on 2017-02-21
> **juntjoo2 said:**
> thanks, what's that, xubuntu desktop? it took a long time and seemed to install libreoffice which I believe I previously uninstalled to save space.

"apt-cache show" can be useful to checkout the description of a package, will detail the dependencies and recommends.. eg

```
apt-cache show xubuntu-desktop
```

Extract from output..
```
Depends: alsa-base, alsa-utils, anacron, bc, ca-certificates, dmz-cursor-theme, doc-base, fonts-dejavu-core, fonts-freefont-ttf,
foomatic-db-compressed-ppds, genisoimage, ghostscript-x, gtk2-engines-pixbuf, inputattach, language-selector-gnome,
 libasound2-plugins, libsasl2-modules, lightdm, lightdm-gtk-greeter, memtest86+, openprinting-ppds, pm-utils, printer-driver-pnm2ppa, rfkill, thunar, 
thunar-volman, tumbler, ubuntu-drivers-common, unzip, update-manager, wireless-tools, wpasupplicant, xdg-user-dirs, xdg-user-dirs-gtk, 
xdg-utils, xfce4-appfinder, xfce4-notifyd, xfce4-panel, xfce4-session, xfce4-settings, xfdesktop4, xfwm4, xkb-data, xorg, xterm, 
xubuntu-artwork, xubuntu-core, xubuntu-default-settings, zenity, zip
Recommends: acpi-support, app-install-data-partner, apport-gtk, apt-offline, avahi-autoipd, avahi-daemon, blueman, bluez, bluez-cups, brltty,
brltty-x11, catfish, cups, cups-bsd, cups-client, cups-filters, desktop-file-utils, espeak, evince, file-roller, firefox, fonts-guru, fonts-kacst-one,
fonts-khmeros-core, fonts-lao, fonts-liberation, fonts-lklug-sinhala, fonts-nanum, fonts-noto-cjk, fonts-noto-hinted, fonts-opensymbol, fonts-sil-abyssinica, 
fonts-sil-padauk, fonts-takao-pgothic, fonts-thai-tlwg, fonts-tibetan-machine, fwupd, fwupdate, fwupdate-signed, gcc, gigolo, 
gnome-accessibility-themes, gnome-calculator, gnome-mines, gnome-software, gnome-sudoku, gnome-system-tools, greybird-gtk-theme,
 gstreamer1.0-pulseaudio, gtk-theme-config, gucharmap, gvfs-backends, gvfs-fuse, hplip, im-config, indicator-application, 
indicator-messages, indicator-sound, inxi, kerneloops-daemon, laptop-detect, libnotify-bin, libnss-mdns, libpam-gnome-keyring, 
libreoffice-calc, libreoffice-gtk, libreoffice-style-elementary, libreoffice-writer, libxfce4ui-utils, light-locker, lightdm-gtk-greeter-settings, make, menulibre,
 mousepad, mugshot, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome, numix-gtk-theme, 
onboard, orage, packagekit, parole, pastebinit, pavucontrol, pcmciautils, pidgin, pidgin-otr, pinentry-gtk2, policykit-desktop-privileges, printer-driver-brlaser, 
printer-driver-c2esp, printer-driver-foo2zjs, printer-driver-min12xxw, printer-driver-ptouch, printer-driver-pxljr, 
printer-driver-sag-gdi, printer-driver-splix, ristretto, simple-scan, snapd, software-properties-gtk, speech-dispatcher, 
system-config-printer-gnome, thunar-archive-plugin, thunar-media-tags-plugin, thunderbird, transmission-gtk, ttf-ancient-fonts-symbola, 
ttf-ubuntu-font-family, update-notifier, whoopsie, xcursor-themes, xfburn, xfce4-cpugraph-plugin, xfce4-dict, xfce4-indicator-plugin, 
xfce4-mailwatch-plugin, xfce4-netload-plugin, xfce4-notes-plugin, xfce4-places-plugin, xfce4-power-manager, xfce4-quicklauncher-plugin,
 xfce4-screenshooter, xfce4-systemload-plugin, xfce4-taskmanager, xfce4-terminal, xfce4-verve-plugin, xfce4-volumed, xfce4-weather-plugin, 
xfce4-whiskermenu-plugin, xfce4-xkb-plugin, xfpanel-switch, xubuntu-community-wallpapers, xubuntu-docs, xul-ext-ubufox
```

I think that..

```
sudo apt install --no-install-recommends xubuntu-desktop
```

as it implies will not install the recommended packages.

There is also the xfce4 package which is considerably lighter.
```
apt-cache show xfce4
Depends: xfwm4 (>= 4.12.0), xfconf (>= 4.12.0), xfce4-settings (>= 4.12.0), xfce4-panel (>= 4.12.0), xfdesktop4 (>= 4.12.0), thunar (>= 1.6.6), gtk2-engines-xfce (>= 3.2.0),
 xfce4-session (>= 4.12.0), xfce4-appfinder (>= 4.12.0), xfce4-pulseaudio-plugin, orage (>= 4.12.0), libxfce4ui-utils (>= 4.12)
Recommends: xorg, desktop-base (>= 5.0.4), thunar-volman (>= 0.8.1), tango-icon-theme (>= 0.8.90), xfce4-notifyd
Suggests: xfce4-goodies, xfce4-power-manager (>= 1.4.0), gtk3-engines-xfce (>= 3.2.0)
Filename: pool/universe/x/xfce4/xfce4_4.12.3_all.deb
```

---

### Post by juntjoo2 on 2017-02-21
I don't quite understand what you said.  What do you know about what this "xubuntu desktop" is, and how did you know it was needed to run xfce since it wasn't mentioned in the guide I initially tried to install it from? I don't know what xfce4 is but if you were recommending it as something with less stuff in it I just "remove"d a bunch of things including libreoffice and thunderbird email. Thanks

---

### Post by speartip on 2017-02-21
Simply put Xubuntu is Ubuntus implementation of Xfce. Hence the X at the beginning. (K)ubuntu is kde. (L)ubuntu is LXDE etc...

---

### Post by juntjoo2 on 2017-02-21
actually, anyone know how to get the "remove" button to work?  I tried uninstalling libre office apps and thunderbird and suduko and other apps but apparently that remove button doesn't work.

edit: never mind. restart solved this

ah, thank you. So these are different "desktop environments" I take it.  I think I will try Kubuntu as x didn't appear to solve my problem...

would "[COLOR=#000000][FONT=&quot]sudo apt install kubuntu-desktop" install kubuntu? what about all those steps from the previously mentioned guide I took?  what did they do? Are there more than one method to install or was that guide wrong? Did it put things on my system that are just taking up space? Or were both methods required together?[/FONT][/COLOR]

---

### Post by toman92 on 2017-02-21
Yes > sudo apt-get install kubuntu-desktop should install kubuntu fine. All you did was add the repository xubuntu is in, updated your packages and installed xfce. You should always run > sudo apt-get update before installing any package, well I do anyway. I'm pretty new to Ubuntu but I think > sudo apt-get install xfce4 would have installed it without adding the repository. It doesn't make a difference though. This [link]("http://askubuntu.com/questions/116602/how-to-install-xfce-desktop-environment") shows some good examples and you should get the answers to any questions you have in there.
Hope it helps.

---

### Post by Impavidus on 2017-02-22
That guide was a bit old. Be careful when copying from random blogs. This guide instructed you to install xfce 4.10 from the xubuntu developers ppa. There's no need for that, you can simply use the default repositories and get xfce 4.12 already.

Xfce is the desktop environment. Xubuntu is the flavour of Ubuntu build around Xfce. If you install xfce4 on Ubuntu, you'll get the desktop environment. Logout and login to start it. If you install xubuntu-desktop you'll get the full xubuntu package, including xfce4 and a bunch of default applications, like libreoffice. You can also directly install Xubuntu instead of Ubuntu.

---

### Post by HermanAB on 2017-02-22
Ayup - Linux isn't Windows.  Don't install random cruft off the internet.  Use the software manager and default repositories.

---

