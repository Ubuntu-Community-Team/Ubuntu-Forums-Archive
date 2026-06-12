---
title: "Missing 'Appearance' option in Settings"
date: 2022-08-25
forum: General Help
---

### Post by 0cs935-bill on 2022-08-25
Did an in-situ upgrade from a fully patched V20.04LTS to V22.04.1LTS and everything appears to work as expected except there's no **Appearance** option in the Settings app. I wanted to change the location of the Dock to left but there's no way to do it from within the Settings app. I use the 'Gnome' login time option because I prefer how the UI functions versus the 'Ubuntu' flavor.

I believe this has to do with the choice of using the "Gnome" login time option.

[COLOR=#000000]I found what looks like the proper key/value pair in dconf Editor and changed 'BOTTOM' to 'LEFT', rebooted and it didn't change anything.[/COLOR]
[COLOR=#000000]I double checked in dconf Editor after the reboot and it says 'LEFT' but the dock is still at the bottom.

[/COLOR]bill@bill ~$ apt show ubuntu-settings
Package: ubuntu-settings
Version: 22.04.6
Priority: optional
Section: x11
Origin: Ubuntu
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 41.0 kB
Depends: dconf-gsettings-backend | gsettings-backend, gnome-control-center-data, gsettings-desktop-schemas (>= 40), libglib2.0-bin (>= 2.53.4-3ubuntu1~)
Task: ubuntu-desktop-minimal, ubuntu-desktop, ubuntukylin-desktop
Download-Size: 6,508 B
APT-Manual-Installed: no
APT-Sources: [http://hn.archive.ubuntu.com/ubuntu](http://hn.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
Description: default settings for the Ubuntu desktop
 This package contains the default settings used by Ubuntu.

Another thread suggested using [COLOR=#000000]Ubuntu Desktop>Position on Screen and select left inside the Settings app, but there is no Ubuntu Desktop option in the Settings app.[/COLOR]

Anyone else missing the **Appearance** option in Settings?

---

### Post by deadflowr on 2022-08-25
Appearance setting is part of gnome-control-center.

> I believe this has to do with the choice of using the "Gnome" login time option.

Correct.
The Appearance desktop file /usr/share/applications/gnome-ubuntu-panel.desktop
shows an entry for OnlyShowIn=ubuntu, meaning it only shows in the Ubuntu login session.

---

### Post by grahammechanical on 2022-08-25
To change the location of the dock on Ubuntu 22.04 try opening Ubuntu Desktop. I get three options: Left, Bottom & Right. I also get an Appearance setting. I can choose the Style: Light or Dark. Colours and the Background image.

Regards

---

### Post by 0cs935-bill on 2022-08-25
deadflowr: Thanks for figuring out why it doesn't appear. I didn't realize that .desktop files were used for options within apps.

Should I assume that tinkering with that setting to remove the restriction will give me access to move the dock or should I assume that the tinkering will hose over the UI? I have an expensive licensed app on my box that makes experimentation dangerous and so far my box is the only V22 I have access to.

---

### Post by Dennis N on 2022-08-25
> **0cs935-bill said:**
> deadflowr: Thanks for figuring out why it doesn't appear. I didn't realize that .desktop files were used for options within apps.

Should I assume that tinkering with that setting to remove the restriction will give me access to move the dock or should I assume that the tinkering will hose over the UI? I have an expensive licensed app on my box that makes experimentation dangerous and so far my box is the only V22 I have access to.

You can launch "Appearance" dialog from the terminal:
```
dmn@Sydney-vm:~$ gnome-control-center ubuntu
```
It works, but I use standard Ubuntu. Since you mentioned log in as Gnome, is that what they call Gnome Classic? You will have try and see if it appears for that.

---

### Post by 0cs935-bill on 2022-08-25
Dennis N: Reading the [COLOR=#000000][FONT=&quot]gnome-control-center.desktop file indicates no passed parameters to the app. It probably figures out what to display internally somehow. I tried passing 'gnome' and 'ubuntu' but got the same response.[/FONT][/COLOR]

---

### Post by tea for one on 2022-08-26
> **deadflowr said:**
> The Appearance desktop file /usr/share/applications/gnome-ubuntu-panel.desktop
shows an entry for OnlyShowIn=ubuntu, meaning it only shows in the Ubuntu login session.

Having read this, I experimented with the login sessions in Ubuntu 22.04:-

Gnome Classic (both Wayland and Xorg) - The Appearance setting is unavailable
Ubuntu (both Wayland and Xorg) - The Appearance setting is available

From a previous thread [https://ubuntuforums.org/showthread.php?t=2478275&page=5](https://ubuntuforums.org/showthread.php?t=2478275&page=5), the OP has installed a package [COLOR="#0000FF"](BricsCAD)[/COLOR] which [COLOR="#0000FF"]is very finicky about its environment[/COLOR], but hopefully, he can try an Ubuntu session and see if Appearance is visible in the Settings?

---

### Post by 0cs935-bill on 2022-08-26
tea for one: Yes, it is available and I can manipulate it but the effects don't carry over. That was one of the first things I tried. Thereafter when I used dconf Editor to manually alter what I suspect are the controlling key/value pairs and nothing happened, that caused me to think that the system is purposely not listening to that setting.

I stumbled over threads on other sites where people are complaining about the problem but so far no one has discovered a solution. It may not exist.

---

### Post by vanadium on 2022-08-26
Use dconf-editor or a gsettings command to change the position of the dock (/org/gnome/shell/extensions/dash-to-dock/).

---

### Post by 0cs935-bill on 2022-08-26
I changed [COLOR=#000000]/org/gnome/shell/extensions/dash-to-dock/dock-position from "BOTTOM' to 'LEFT' and it has no effect immediately or after a reboot. I checked after the reboot and the change to 'LEFT' was made but does nothing.[/COLOR]

---

### Post by tea for one on 2022-08-26
> **0cs935-bill said:**
> tea for one: Yes, it is available and I can manipulate it but the effects don't carry over.
if you use Appearance to change a theme, does it work OK?

---

### Post by 0cs935-bill on 2022-08-26
tea for one: I tried that also and no success. I suspect that the controlling code under my setup isn't looking at the usual suspects in the scheme / registry / whatever its called. It's either intentional or someone made a boo boo.

---

### Post by tea for one on 2022-08-26
Yes, something is misbehaving somewhere?

Using dconf editor, can you look at /org/gnome/desktop/interface/gtk-theme

What is the Default and Current Value?

---

### Post by Dennis N on 2022-08-26
Would you clarify which dock you are using? Ubuntu Dock or Dash to Dock? Dash to Dock shows as "unsupported" in Extensions Manager in 22.04. An alternative to both is Plank, which has themes and is very configurable. I use it instead of Ubuntu Dock on 22.04. Screenshots atttached.

---

### Post by 0cs935-bill on 2022-08-26
tea for one: I changed my theme to Yaru-red and that's what that item says. Everything in that area makes no mention of where the dock should be. I changed font size and other options using the settings app and those changes show up in .../interface

Dennis N: I'm referring to your vertical set of icons. Mine were vertical under V20.04 and the in-situ upgrade plus selecting the 'Gnome' login option gave me the horizontal equivalent. My Gnome extensions have nothing to do with Dock turned on.

---

### Post by vanadium on 2022-08-26
> **0cs935-bill said:**
> I changed [COLOR=#000000]/org/gnome/shell/extensions/dash-to-dock/dock-position from "BOTTOM' to 'LEFT' and it has no effect immediately or after a reboot. I checked after the reboot and the change to 'LEFT' was made but does nothing.[/COLOR]
What do you mean by "does nothing"? Dock frozen or something?

---

### Post by 0cs935-bill on 2022-08-26
vanadium: It has no effect at all. It's as though I never changed anything. Everything runs after as it did before.

---

### Post by vanadium on 2022-08-28
Strange. I have no problem changing the position of the Ubuntu Dock in a Gnome session using dconf-editor. Can you confirm that 
```

gsettings get org.gnome.shell.extensions.dash-to-dock dock-position

```
returns 'BOTTOM'?

---

### Post by 0cs935-bill on 2022-08-28
vanadium:
bill@bill ~$ gsettings get org.gnome.shell.extensions.dash-to-dock dock-position'BOTTOM'
I ran dconf Editor and changed the setting to 'LEFT'
bill@bill ~$ gsettings get org.gnome.shell.extensions.dash-to-dock dock-position
'LEFT'



I rebooted the box with a power off and on.
bill@bill ~$ gsettings get org.gnome.shell.extensions.dash-to-dock dock-position
'LEFT'
The icons are still on the bottom. It's not listening to that setting.


I then uninstalled the Dash to Dock extension, rebooted the box, no change, and installed the dash to dock extension.
Now it works. I had to kill the extension and reinstall it to make it function.

---

