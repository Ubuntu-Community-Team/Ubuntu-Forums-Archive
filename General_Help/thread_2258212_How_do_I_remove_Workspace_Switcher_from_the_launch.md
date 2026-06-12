---
title: "How do I remove Workspace Switcher from the launcher?"
date: 2014-12-25
forum: General Help
---

### Post by petermartin2 on 2014-12-25
I use Workspace Switcher with key shortcut and don't want it on the workspace switcher. This is driving me insane because I know that before my reinstall I had WS on but not in the launcher and I have no recollection that it would be such a mess getting rid of it.

So far I've tried:
a) dragging it to the dust bin (completely disables the WS)
b) command lines
```
gsettings get com.canonical.Unity.Launcher favorites
gsettings set com.canonical.Unity.Launcher favorites "['application://nautilus.desktop', 'application://chromium-browser.desktop', 'application://ubuntu-software-center.desktop', 'application://ubuntuone-installer.desktop', 'application://ubuntu-amazon-default.desktop', 'application://UbuntuOneMusiconeubuntucom.desktop', 'application://gnome-control-center.desktop', 'unity://running-apps', 'unity://devices']"`.
```
c) editing /usr/share/unity-2d/shell/launcher/Launcher.qml (the name was not provided by any files)

What's next? Really want to get rid of it from the launcher...

---

### Post by kerry_s on 2014-12-25
if i remember right its in the gui tweak tool. just uncheck the box for work space switcher

---

### Post by petermartin2 on 2014-12-25
According to [this]("http://ubuntuguide.net/remove-workspace-switcher-from-unity-launchervia-ppa-in-ubuntu-11-10") page you have to "hack" the source code to remove it from the launcher and still be able to use it with shortcut but I'm positive I had it as a shortcut but not on the launcher before the installation, is there some new way for 14.04 or 14.10 to do this in a simple way? I'm new to ubuntu and don't see myself "hacking" source code..

---

### Post by petermartin2 on 2014-12-25
> **kerry_s said:**
> if i remember right its in the gui tweak tool. just uncheck the box for work space switcher

What is gui tweak tool? is it what appears as unity tweak tool or ubuntu tweak I've got both and I can not find any box there that disables it in the launcher but keeps it as a keyboard shortcut which field would that checkbox be in, would you mind looking? I can't find gui tweak tool in ubuntu software center

There appears to be no such option in Unity Tweak tool or Ubuntu Tweak I've looked through them many many times because I thought this was where I did it also. I've disabled the workspace switcher altogether now (this you can do in unity tweak tool) but what I really want to do is to remove it from the launcher only and keep using it with keyboard shortcut. If anyone has a solution I'd be happy to hear it!

---

### Post by buzzingrobot on 2014-12-25
It's in System Settings, in Appearance. At least, that's where it's enabled and, presumably, disabled.

---

### Post by petermartin2 on 2014-12-25
> **buzzingrobot said:**
> It's in System Settings, in Appearance. At least, that's where it's enabled and, presumably, disabled.

I'm not looking to disable it I'm looking to remove the shortcut from the launcher without disabling it. I know that it can be disabled and enabled in appearance

---

### Post by buzzingrobot on 2014-12-25
> **petermartin2 said:**
> I'm not looking to disable it I'm looking to remove the shortcut from the launcher without disabling it. I know that it can be disabled and enabled in appearance

It's a Compiz function.  You might install compizconfig-settings-manager and take a look around there. Carefully; it's easy to break Unity doing that.

---

### Post by petermartin2 on 2014-12-25
> **buzzingrobot said:**
> It's a Compiz function.  You might install compizconfig-settings-manager and take a look around there. Carefully; it's easy to break Unity doing that.

That explains it. I haven't got compiz to function properly with my video card

---

### Post by mc4man on 2014-12-25
If you're using an ubuntu session (unity) then compiz is functioning "properly" or at least good enough.
As far as having workspaces enabled & no ws icon (expo) you just remove it from com.canonical.Unity.Launcher favorites
Maybe you didn't enter correctly, what you posted in code box above is 'wrong' ( no [COLOR="#FF0000"]`[/COLOR]

What does this show ?
```
gsettings get com.canonical.Unity.Launcher favorites
```
Ex. in screen, obviously I have workspaces enabled but removed the launcher icon
(- which I'll put back because while I don't use much it does show me which ws I'm on.

---

### Post by CantankRus on 2014-12-25
Edit: mc4man already said this but I think that's why not working
Your **gsettings set** command in your first post is incorrect. Your command ends with a backtick and fullstop.
```
......, 'unity://devices']"[COLOR="#FF0000"]**`.**[/COLOR]
```
Remove and try again.

---

### Post by petermartin2 on 2014-12-26
> **CantankRus said:**
> Edit: mc4man already said this but I think that's why not working
Your **gsettings set** command in your first post is incorrect. Your command ends with a backtick and fullstop.
```
......, 'unity://devices']"[COLOR=#FF0000]**`.**[/COLOR]
```
Remove and try again.

This solved it, thanks!

---

### Post by petermartin2 on 2014-12-29
I've reinstalled Ubuntu due to issues with graphics and now I can't remove the workspace switcher again. The command lines are no longer working so I would be grateful for advise if someone knows how to remove the workspace switcher from the launcher but keep it working with key shortcut

Thanks

---

### Post by CantankRus on 2014-12-29
What's your output from....
```
gsettings get com.canonical.Unity.Launcher favorites
```

---

### Post by petermartin2 on 2014-12-29
> **CantankRus said:**
> What's your output from....
```
gsettings get com.canonical.Unity.Launcher favorites
```

['application://nautilus.desktop', 'application://firefox.desktop', 'application://libreoffice-calc.desktop', 'unity://running-apps', 'unity://expo-icon', 'unity://devices']

---

### Post by CantankRus on 2014-12-29
To remove Workspace Switcher, run...
```
gsettings set com.canonical.Unity.Launcher favorites [COLOR="#FF8C00"]**"**[/COLOR]['application://nautilus.desktop', 'application://firefox.desktop', 'application://libreoffice-calc.desktop', 'unity://running-apps', 'unity://devices'][COLOR="#FF8C00"]**"**[/COLOR]
```

You just remove the **'unity://expo-icon'** item from your **gsettings [COLOR="#FF0000"]get[/COLOR] com.canonical.Unity.Launcher favorites** output
and then use the **gsettings [COLOR="#FF0000"]set[/COLOR] com.canonical.Unity.Launcher favorites** command, enclosing the new value in [COLOR="#FF8C00"]**double quotes**[/COLOR].

---

### Post by petermartin2 on 2014-12-30
> **CantankRus said:**
> To remove Workspace Switcher, run...
```
gsettings set com.canonical.Unity.Launcher favorites [COLOR=#FF8C00]**"**[/COLOR]['application://nautilus.desktop', 'application://firefox.desktop', 'application://libreoffice-calc.desktop', 'unity://running-apps', 'unity://devices'][COLOR=#FF8C00]**"**[/COLOR]
```

You just remove the **'unity://expo-icon'** item from your **gsettings [COLOR=#FF0000]get[/COLOR] com.canonical.Unity.Launcher favorites** output
and then use the **gsettings [COLOR=#FF0000]set[/COLOR] com.canonical.Unity.Launcher favorites** command, enclosing the new value in [COLOR=#FF8C00]**double quotes**[/COLOR].

Thanks a bunch.

---

