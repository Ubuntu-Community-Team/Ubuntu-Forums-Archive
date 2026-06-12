---
title: "Fully change from Kubuntu to Ubuntu?"
date: 2007-02-18
forum: General Help
---

### Post by guice on 2007-02-18
I had Kubuntu installed a long time ago as my original distribution. This was back before Dapper. When Dapper was released, I decided to convert to Ubuntu. I installed ubuntu-desktop and set the gdm to be the default manager.

However, I ran into a problem that just made itself apparent today. All this time, the system would always boot with the Kubuntu logo, thinking it was a Kubuntu system. This never has been a problem until I did an aptitude dist-upgrade the other day. It removed a bunch of files, many gnome related and I thought it must know what its doing.

I had a black out and was forced to reboot my system. Upon rebooting, I discovered just about anything Ubuntu related was reverted to Kubuntu. It was using kdm, not gdm, and none of my gnome apps were working right. 

I ran aptitude again, with install ubuntu-desktop and wouldn't you know, it's installing everything it removed earlier. 0.o

So ... now that I'm going through this process, again, to put back all my Ubuntu files, I want to know how do I 100% convert this box to Ubuntu so this will never happen again? The simple answer, of course, would be just to re-install the OS, but I really don't want to resort to that.

---

### Post by bapoumba on 2007-02-18
These links may help you out:
1- make sure ubuntu-desktop is installed:
[http://psychocats.net/ubuntu/gnome]("http://psychocats.net/ubuntu/gnome")
2- remove kubuntu-desktop:
[http://psychocats.net/ubuntu/puregnomedapper]("http://psychocats.net/ubuntu/puregnomedapper")
(the second link is for dapper only).

---

### Post by guice on 2007-02-18
Nah, that's just installing GNOME on Kubuntu. My problem is deep within the OS, between the lines, it's still saying it's Kubuntu and when I did the updates/removes and such, it removed ubuntu-desktop and all its components breaking a lot of things.

For example, I can say "aptitude remove gaim" and it'll remove ubuntu-desktop and everything ubuntu related....not a good thing. That's how everything broke.

I need to find out what's telling my system it's Kubuntu and convert it. It's even more obvious it thinks it's Kubuntu when I shut down or start up -- it always shows the Kubuntu screens.

Also, I don't want to remove Kubuntu-desktop -- I have apps that to rely on KDE backends. I just want my system to be "Offically Ubuntu" instead of "Kubuntu with GNOME."

---

### Post by bapoumba on 2007-02-19
> **guice said:**
> 
For example, I can say "aptitude remove gaim" and it'll remove ubuntu-desktop and everything ubuntu related....not a good thing. That's how everything broke.

ubuntu-desktop is a meta package that ties up the whole desktop packages via dependencies. Gaim is a dependency of ubuntu-desktop, if you remove gaim, then the dependencies to ubuntu-desktop are broken, and ubuntu-desktop gets removed.
```
~ $ aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: installed
Automatically installed: no
Version: 1.30
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 45.1k
Depends: acpi, acpi-support, acpid, alacarte, anacron, apmd, apport-gtk, avahi-daemon, bc, bug-buddy, cdparanoia, cdrecord, contact-lookup-applet, cupsys,
         cupsys-bsd, cupsys-client, cupsys-driver-gutenprint, dc, deskbar-applet, desktop-file-utils, diveintopython, doc-base, dvd+rw-tools, ekiga, eog,
         esound, evince, evolution, evolution-exchange, evolution-plugins, evolution-webcal, f-spot, file-roller, firefox, firefox-gnome-support, foo2zjs,
         foomatic-db, foomatic-db-engine, foomatic-db-hpijs, foomatic-filters, fortune-mod, **gaim,** gcalctool, gconf-editor, gdebi, gdm, gedit, gimp,
         gimp-print, gimp-python, gnome-about, gnome-app-install, gnome-applets, gnome-btdownload, gnome-control-center, gnome-cups-manager,
         gnome-icon-theme, gnome-keyring-manager, gnome-media, gnome-menus, gnome-netstatus-applet, gnome-nettool, gnome-panel, gnome-pilot-conduits,
         gnome-power-manager, gnome-session, gnome-spell, gnome-system-monitor, gnome-system-tools, gnome-terminal, gnome-themes, gnome-utils,
         gnome-volume-manager, gnome2-user-guide, gs-esp, gstreamer0.10-alsa, gstreamer0.10-esd, gstreamer0.10-plugins-base-apps, gthumb, gtk2-engines,
         gucharmap, hal, hal-device-manager, hotkey-setup, hwdb-client-gnome, landscape-client, language-selector, lftp, libgl1-mesa-glx, libglut3,
         libgnome2-perl, libgnomevfs2-bin, libgnomevfs2-extra, libpam-foreground, libpt-plugins-v4l, libpt-plugins-v4l2, libsasl2-modules, libstdc++5,
         libxp6, metacity, min12xxw, mkisofs, nautilus, nautilus-cd-burner, nautilus-sendto, notification-daemon, openoffice.org, openoffice.org-evolution,
         openoffice.org-gnome, pnm2ppa, powermanagement-interface, readahead, rhythmbox, rss-glx, screen, screensaver-default-images, scrollkeeper,
         serpentine, slocate, smbclient, sound-juicer, ssh-askpass-gnome, synaptic, tangerine-icon-theme, tango-icon-theme, tango-icon-theme-common, tomboy,
         totem, totem-mozilla, tsclient, ttf-bitstream-vera, ttf-dejavu, ttf-freefont, ubuntu-artwork, ubuntu-docs, ubuntu-sounds, unzip, update-notifier,
         usplash, usplash-theme-ubuntu, vino, wvdial, x-ttcidfont-conf, xkeyboard-config, xorg, xsane, xscreensaver-data, xscreensaver-gl, xterm,
         xvncviewer, yelp, zenity, zip
Recommends: bluez-cups, bluez-pin, bluez-utils, brltty, brltty-x11, example-content, gcc, gnome-accessibility-themes, gnome-games, gnome-mag, gnome-orca,
            gnome-screensaver, hplip, linux-headers-generic, make, onboard, powernowd, scim, scim-gtk2-immodule, ttf-arabeyes, ttf-arphic-ukai,
            ttf-arphic-uming, ttf-baekmuk, ttf-gentium, ttf-indic-fonts, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-mgopen,
            ttf-thai-tlwg, xcursor-themes
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system 
 
 **It is also used to help ensure proper upgrades, so it is recommended that it not be removed.**

```

---

### Post by guice on 2007-02-19
> **bapoumba said:**
> ubuntu-desktop is a meta package that ties up the whole desktop packages via dependencies. Gaim is a dependency of ubuntu-desktop, if you remove gaim, then the dependencies to ubuntu-desktop are broken, and ubuntu-desktop gets removed.

That I get. What I was trying to do is install a new version of gaim. Now, that its installed, I need to downgrade it cause of a bug in GAIM (I think it's gaim's bug): [https://launchpad.net/ubuntu/+source/gaim/+bug/82630](https://launchpad.net/ubuntu/+source/gaim/+bug/82630)

Running GAIM in sudo mode isn't exactly something I'd like to do. For starters, all my IM histories aren't being saved under my account. And it gives gaim a bit more permissions than I'd appreciate.

---

### Post by Foxmike on 2007-02-19
> **guice said:**
> Nah, that's just installing GNOME on Kubuntu. My problem is deep within the OS, between the lines, it's still saying it's Kubuntu and when I did the updates/removes and such, it removed ubuntu-desktop and all its components breaking a lot of things.

For example, I can say "aptitude remove gaim" and it'll remove ubuntu-desktop and everything ubuntu related....not a good thing. That's how everything broke.

I need to find out what's telling my system it's Kubuntu and convert it. It's even more obvious it thinks it's Kubuntu when I shut down or start up -- it always shows the Kubuntu screens.

Also, I don't want to remove Kubuntu-desktop -- I have apps that to rely on KDE backends. I just want my system to be "Offically Ubuntu" instead of "Kubuntu with GNOME."

Well, correct me if I'm wrong, but Ubuntu is "Ubuntu with Gnome" and Kubuntu is "Ubuntu with KDE", so It does not change anything if you install ubuntu-desktop over a Kubuntu install.

If you have your /home on a separate partition, I would suggest to re-install the whole thing that way you will be sure to get a clean install, with no broken apps.  

Thus, I don't think anything "tells" the system is "Kubuntu".  The screen you see when you boot or close your computer is a usplash screen, themable as the splash screen when you log in, or as the window borders, so this doesn't mean anything.

Hope it helps!

- FM

---

### Post by dday376 on 2007-02-23
Had a similar problem.  It's a very non-intuitive solution, at least the start-up/shut-down logos.  In synaptic, mark "ubuntu-artwork" for reinstallation.  That'll reset the system to show the Ubuntu logo during start-up/shut-down rather than Kubuntu.

If all else fails, I would mark "ubuntu-desktop" for reinstallation.  That should reset, and it should also preserve any cusomizations you've done.

Hope that helps!

[EDIT] I incorrectly stated to reinstall "ubuntu-artwork".  You will want to reinstall "usplash-theme-ubuntu" and that should clear up the splash issues you're having on start-up/shut-down.

---

### Post by spirilis on 2007-02-28
How about going the other way around?  I have an Ubuntu 6.06 AMD64 installation where I would like to start using KDE as if I had Kubuntu installed.  Is there a big "kde-desktop" package that installs the whole Taj Mahal for me, and any other "artwork" packages that need reinstallation to make it look like Kubuntu?

Thanks in advance!
-Eric

---

### Post by dday376 on 2007-04-14
> **spirilis said:**
> How about going the other way around?  I have an Ubuntu 6.06 AMD64 installation where I would like to start using KDE as if I had Kubuntu installed.  Is there a big "kde-desktop" package that installs the whole Taj Mahal for me, and any other "artwork" packages that need reinstallation to make it look like Kubuntu?

Thanks in advance!
-Eric

Yup.  It's kubuntu-desktop.

---

