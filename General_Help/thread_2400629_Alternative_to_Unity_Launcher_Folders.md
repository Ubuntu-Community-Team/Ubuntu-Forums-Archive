---
title: "Alternative to Unity Launcher Folders ?"
date: 2018-09-08
forum: General Help
---

### Post by drpeppercan on 2018-09-08
Can anyone suggest a similar solution for Ubuntu 18.04?

I am running out of space for my favourites in the left vertical panel.

Thanks

---

### Post by tea for one on 2018-09-08
Are you familiar with gnome extensions? If not, here is a suggestion:-

[https://extensions.gnome.org/extension/307/dash-to-dock/](https://extensions.gnome.org/extension/307/dash-to-dock/)

---

### Post by vanadium on 2018-09-08
I am not aware of a possibility similar to Unity launchers. However, you are probably defeating the benefit of launchers. If you are having too much icons, the efficiency of quickly launching your favourites vanishes. You will find them equally fast in the applications overview than in an overcrowded dock. That is, of course, just my opinion.

You may consider the possibility to create folders in the Applications Overview. For example, we currently a "Utilities" group. Gnome Shell unfortunately does not expose an easy way to organize such groups by ourselves, but with an extension like [Appfolders manager](https://extensions.gnome.org/extension/1217/appfolders-manager/) you can easily create your own groups. As such, you could create groups there for favourites you would otherwise have relocated into Ubuntu launchers. If you start the name of these groups with numbers, they will show on the top row of the application overview. You then have access to these on three clicks, one on the "Show Applications" icon in the dock, then one to open the group, then the application (that is one more click than with Unity folders, I know, but it will 1) keep your dock uncluttered for these few programmes that you use all the time. 2) facilitate management of your running tasks through the dock).
 
@tea for one Dash to Dock will not help there. The standard dock in Ubuntu is essentially Dash to Dock.

---

### Post by monkeybrain20122 on 2018-09-09
Instead of hunting around random gnome extensions you can just install unity

```
[FONT=Ubuntu]sudo apt install ubuntu-unity-desktop

[/FONT]
```

Choose lighdm as default

reboot, and log into unity, that's it (it pulls in some packages like youtube-dl, just uninstall them if you don't need them. I was told not to use the "[FONT=Ubuntu] --no-install-recommends" option[/FONT])

If use touchpad
```

sudo apt install xserver-xorg-input-synaptics
```

have been using unity on 18.04 since beta, it is much smoother and much more responsive than gnome shell.

---

### Post by again? on 2018-09-09
Another option is to create quicklist menus and group similar apps.
I create quicklist items for vivaldi browser to launch other browsers and incognito modes.

Copy a .desktop launcher from /usr/share/applications to ~/.local/share/applications
Launchers in ~/.local/share/applications will override corresponding ones in /usr/share/applications
Then edit the copy to add your own right click menus.

eg using vivaldi-snapshot.
```
cp /usr/share/applications/vivaldi-snapshot.desktop ~/.local/share/applications/
```

Then edit the copy
```
gedit ~/.local/share/applications/vivaldi-snapshot.desktop
```

Add to existing Actions or create new.
```
[Desktop Entry]
Version=1.0
Name=Vivaldi (snapshot)
# Only KDE 4 seems to use GenericName, so we reuse the KDE strings.
# From Ubuntu's language-pack-kde-XX-base packages, version 9.04-20090413.
GenericName=Web Browser
# Not translated in KDE, from Epiphany 2.26.1-0ubuntu1.
# Gnome and KDE 3 uses Comment.
Comment=Access the Internet
Exec=/usr/bin/vivaldi-snapshot --start-maximized %U
Terminal=false
Icon=/home/glen/Pictures/icons/vivaldi-snapshot2.png
Type=Application
Categories=Network;WebBrowser;
MimeType=x-scheme-handler/unknown;x-scheme-handler/about;text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
Name[en_AU]=Vivaldi Snapshot

Actions=[COLOR="#FF0000"]incognito[/COLOR];[COLOR="#0000FF"]fresh[/COLOR];vivaldi-stable;firefox;firefox-private;chrome;chrome-private;opera;

[Desktop Action [COLOR="#FF0000"]incognito[/COLOR]]
Name=Vivaldi-snapshot (incognito)
Exec=vivaldi-snapshot --incognito

[Desktop Action [COLOR="#0000FF"]fresh[/COLOR]]
Name=Vivaldi-snapshot (test profile)
Exec=/home/glen/scripts/vivaldi-snapshot_fresh-profile.sh

[Desktop Action vivaldi-stable]
Name=Vivaldi-stable
Exec=/usr/bin/vivaldi-stable

[Desktop Action firefox]
Name=Firefox
Exec=/usr/bin/firefox

[Desktop Action firefox-private]
Name=Firefox Private Window
Exec=/usr/bin/firefox --private

[Desktop Action chrome]
Name=Chrome
Exec=/usr/bin/google-chrome-beta

[Desktop Action chrome-private]
Name=Chrome Incognito
Exec=/usr/bin/google-chrome-beta --incognito

[Desktop Action opera]
Name=Opera Mail
Exec=env GTK2_RC_FILES=/usr/share/themes/Industrial/gtk-2.0/gtkrc /usr/bin/opera

```

The entry in "Actions=[COLOR="#696969"]xxxx[/COLOR]" must match the name in the "[Desktop Action [COLOR="#696969"]xxxx[/COLOR]] heading
and determines which Desktop Actions are shown and their menu display order. 
Attached pic is from xfce using plank dock but gnome-shell or unity docks will show similar.

---

### Post by drpeppercan on 2018-09-09
Wow!
You guys are amazing!

Thank you so much for all this info! Now I have plenty to try and explore! There are some great ideas here to try.

---

