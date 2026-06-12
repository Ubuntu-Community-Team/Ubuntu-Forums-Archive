---
title: "How to add keyboard shortcuts in Lubuntu 16.04"
date: 2018-06-04
forum: General Help
---

### Post by John_Patrick_Mason on 2018-06-04
I have two computers at home; one with Ubuntu installed, and another with Lubuntu. Unfortunately, some of the shortcuts in Ubuntu that I've grown accustomed to are different/missing in Lubuntu.
These are the shortcuts that I'd like to add to Lubuntu:
Ctrl+Super+Up = maximize window
Ctrl+Super+Down = minimize window
Ctrl+Super+Left = half-sized window to the left
Ctrl+Super+Right = half-sized window to the right

In particular, I'd like to know if there's a simple way I can edit the ~/.config/openbox/lubuntu-rc.xml file.

Thanks in advance.

---

### Post by again? on 2018-06-04
You can manually edit lubuntu-rc.xml in your text editor or you can use obkey.
See [**THIS**]("https://ubuntuforums.org/showthread.php?t=2246932&p=13142181#post13142181") post.
Have a look at the attached mp4 of that post.

By default obkey opens ~/.config/openbox/rc.xml
If your using Lubuntu you will want to open ~/.config/openbox/lubuntu-rc.xml to edit. (check your actual path)
ie append path to rc.xml to obkey start command.
```
[COLOR="#696969"]/path/to/[/COLOR]obkey ~/.config/openbox/lubuntu-rc.xml
```

****Whatever you do make a backup of lubuntu-rc.xml first.**

---

### Post by nlee2 on 2018-06-04
These packages are in lubuntu 18.04. You may need to install ppa:lubuntu-dev/lubuntu-daily for 16.04

lxhotkey-gtk - LXHotkey keyboard shortcuts configurator (GTK+ GUI plugin)
lxhotkey-plugin-openbox - LXHotkey keyboard shortcuts configurator (Openbox support plugin)

---

### Post by John_Patrick_Mason on 2018-06-05
> **guber2 said:**
> You can manually edit lubuntu-rc.xml in your text editor or you can use obkey.
See [**THIS**]("https://ubuntuforums.org/showthread.php?t=2246932&p=13142181#post13142181") post.
Have a look at the attached mp4 of that post.

By default obkey opens ~/.config/openbox/rc.xml
If your using Lubuntu you will want to open ~/.config/openbox/lubuntu-rc.xml to edit. (check your actual path)
ie append path to rc.xml to obkey start command.
```
[COLOR=#696969]/path/to/[/COLOR]obkey ~/.config/openbox/lubuntu-rc.xml
```

****Whatever you do make a backup of lubuntu-rc.xml first.**

OK, I downloaded and installed obkey.
Initially, I was reluctant to install obkey because I wanted to avoid cluttering my system with unnecessary junk since I'm working on especially weak hardware. It's only after I opened the ~/.config/openbox/rc.xml file manually that I realized the file was written in XML, which I'm unable to read, thereby making obkey a necessary part of the solution.
I managed to replicate Ubuntu's behavior on my Lubuntu system for the Ctrl+Super+Up, Ctrl+Super+Left, and Ctrl+Super+Right shortcuts, but I can't figure out which actions are necessary in obkey to get the same behavior on my Lubuntu system as on my Ubuntu system, when typing Ctrl+Super+Down. I'd like for the terminal window to automatically move to the top left corner, back to its original size, I'm just not sure how to proceed using obkey. Any ideas?

---

### Post by again? on 2018-06-05
Choose as the action "UnmaximizeFull".
Returns window to size and position before being maximized.

---

### Post by John_Patrick_Mason on 2018-06-06
> **guber2 said:**
> Choose as the action "UnmaximizeFull".
Returns window to size and position before being maximized.

I tried that already. It works if I type Ctrl+Super+Up and then Ctrl+Super+Down, but if I type Ctrl+Super+Right or Ctrl+Super+Left and then Ctrl+Super+Down, the terminal window will occupy the left or right side of the screen. If I type Ctrl+Super+Right or Ctrl+Super+Left, then Ctrl+Super+Up to maximize the window, and then Ctrl+Super+Down, the terminal window will still occupy the right or left half of the screen with no way to return the window to its original size. I don't know what to do.

---

### Post by again? on 2018-06-06
What actions do you use for your Ctrl+Super+Right and Ctrl+Super+Left keys?
Gotta take the dog for a walk.
I'll have a look in an openbox session when I get back in about an hour.

Have a solution in mind using wmctrl.

---

### Post by again? on 2018-06-06
It works here when the tiling keybinds include a "MaximizeVert" action.

---

### Post by HermanAB on 2018-06-06
I've been using Autokey for many years.

---

