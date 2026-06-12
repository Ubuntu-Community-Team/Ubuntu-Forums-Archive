---
title: "Double Skype icon (one not working) in Dash"
date: 2018-09-12
forum: General Help
---

### Post by carlo8 on 2018-09-12
Hi everybody,
I'm running Ubuntu 16.04 and I have a problem with Skype.
I installed it from the Software Center, then removed it and reinstalled it from Synaptic Package Manager.

Now I have two Skype icons in the dash. One of them works, but the other one has a question mark over it and doesn't do anything.
I seemed to understand I could try to modify the Skype .desktop file, but I couldn't find it in the '/usr/share/skypeforlinux' folder.
Any suggestions?



P.S. It is kinda off-topic, but why programs installed via the Softwate Center don't show up in the Package Manager and viceversa? Maybe it's just me, but I find it confusing! :confused:

---

### Post by carlo8 on 2018-09-17
Hi, doesn't anyone have idea? :(
Should the thread better be moved to another section, maybe?

---

### Post by mc4man on 2018-09-17
Maybe the first skype was a snap, that wouldn't show in synaptic. To ck. run
snap list

---

### Post by carlo8 on 2018-09-17
This is the output, no Skype


```

[FONT=Verdana]Name        Version                             Rev     Tracking     Publisher         Notes[/FONT]
[FONT=Verdana]core           16-2.35                             5328   stable         canonical&#10003;      core[/FONT]
[FONT=Verdana]spotify        1.0.89.313.g34a58dea-5 21        stable         spotify&#10003;             -[/FONT]

```

---

### Post by mc4man on 2018-09-17
See what this returns, post in a code box. (assuming still having 2 icons  & the default Ubuntu, ie. unity & compiz
```
gsettings get com.canonical.Unity.Launcher favorites
```

---

### Post by carlo8 on 2018-09-18
This is the output


```
['application://chromium-browser.desktop', 'application://org.gnome.Nautilus.desktop', 'application://org.gnome.Software.desktop', 'application://gedit.desktop', 'application://gnome-terminal.desktop', 'application://libreoffice-startcenter.desktop', 'application://texstudio.desktop', 'application://synaptic.desktop', 'application://unity-control-center.desktop', 'application://deluge.desktop', 'application://gnome-calculator.desktop', 'application://xmaxima.desktop', 'application://update-manager.desktop', 'application://pcsx.desktop', 'application://vlc.desktop', 'unity://running-apps', 'application://homebank.desktop', 'application://spotify_spotify.desktop', 'application://skypeforlinux.desktop', 'unity://desktop-icon', 'unity://expo-icon', 'unity://devices']
```


Just, as far as I can see, these are the programs locked in the Launcher.
Just in case I didn't explain my problem clearly, the two Skype icons (yes, they are still here, and one has still the question mark icon and is not working) are in the Dash.

---

