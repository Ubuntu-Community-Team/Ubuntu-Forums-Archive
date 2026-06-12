---
title: "gnome-tweak-tool cannot start on ubuntu budgie 17.04"
date: 2017-03-31
forum: General Help
---

### Post by 243750496 on 2017-03-31
atc@ATC:~$ gnome-tweak-tool
WARNING : Shell not installed or running
atc@ATC:~$ sudo gnome-tweak-tool
WARNING : Shell not installed or running

gnome-tweak-tool version 3.24


more addition:
i had installed freshly just before this fresh install, it working smoothly but i haven't check the version of gnome-tweak-tool at that time, so maybe it's a new version bug? or something else i did wrong at this time?

---

### Post by lisati on 2017-03-31
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by akopacsi2 on 2017-03-31
Can you see the icon of tweak tool within the GUI? Do you need unity-tweak-tool or gnome-tweak-tool?

---

### Post by QIII on 2017-03-31
Sorry to move this again...

Ubuntu Budgie is an official flavor of Ubuntu starting with 17.04.  Since we have stopped moving 17.04 to development, we might as well leave this one in the Ubuntu support forums.

Cheers!

---

### Post by 243750496 on 2017-03-31
> **akopacsi2 said:**
> Can you see the icon of tweak tool within the GUI? Do you need unity-tweak-tool or gnome-tweak-tool?
Saw the icon show up then disappeared in 1min 


Only icon no window show up

```
WARNING : Shell not installed or running
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 279, in __init__
    raise Exception("Shell not running or DBus service not available")
Exception: Shell not running or DBus service not available
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/app.py", line 41, in do_activate
    self.win = Window(self, model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 58, in __init__
    self._model.load_tweaks(self)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 126, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 335, in <module>
    ShellExtensionTweakGroup(),
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 309, in __init__
    shell._settings.bind("disable-user-extensions", self.titlebar_widget,
AttributeError: 'NoneType' object has no attribute '_settings'
```

---

### Post by tea for one on 2017-04-01
> **243750496 said:**
> atc@ATC:~$ gnome-tweak-tool
WARNING : Shell not installed or running
atc@ATC:~$ sudo gnome-tweak-tool
WARNING : Shell not installed or running

Ubuntu Budgie uses the Budgie interface therefore gnome-tweak tool would be little use to you.

Ubuntu-GNOME uses the gnome shell interface and then gnome-tweak-tool is a very useful utility.

You have to have gnome-shell installed to use gnome-tweak-tool

---

### Post by 243750496 on 2017-04-01
> **tea for one said:**
> Ubuntu Budgie uses the Budgie interface therefore gnome-tweak tool would be little use to you.

Ubuntu-GNOME uses the gnome shell interface and then gnome-tweak-tool is a very useful utility.

You have to have gnome-shell installed to use gnome-tweak-tool


So the  solution is? Whether the tweak  tool  can't  be used  on  budgie or i need  to  install gnome  shell.
And the step  of  install gnome shell is?


Thx in adv

---

### Post by tea for one on 2017-04-01
Ubuntu Budgie is a new distribution and I do not know whether there will be any conflict if you install gnome-shell and gnome-tweak tool.

Please make sure that you have backed up your personal data.

If you wish to experiment with Ubuntu Budgie and gnome-shell then:-

```
sudo apt install gnome-shell
```

```
sudo apt install gnome-tweak-tool
```

If you are given the option to alter the welcome page (lightdm or gdm3), it would be better to remain with the default Budgie welcome (I assume that it is lightdm)

I know that gdm3 does not function correctly on top of an Ubuntu (with unity) system.

A _better_ option would be to back up your data and install Ubuntu-GNOME.

---

### Post by 243750496 on 2017-04-01
> **tea for one said:**
> Ubuntu Budgie is a new distribution and I do not know whether there will be any conflict if you install gnome-shell and gnome-tweak tool.

Please make sure that you have backed up your personal data.

If you wish to experiment with Ubuntu Budgie and gnome-shell then:-

```
sudo apt install gnome-shell
```

```
sudo apt install gnome-tweak-tool
```

If you are given the option to alter the welcome page (lightdm or gdm3), it would be better to remain with the default Budgie welcome (I assume that it is lightdm)

I know that gdm3 does not function correctly on top of an Ubuntu (with unity) system.

A _better_ option would be to back up your data and install Ubuntu-GNOME.



gnome shell is already  the newest version 3.24

&#65288;Already installed &#65289;

---

### Post by tea for one on 2017-04-02
Have you installed gnome-tweak-tool?

Have you successfully logged into a Gnome session?

---

### Post by 243750496 on 2017-04-03
> **tea for one said:**
> Have you installed gnome-tweak-tool?

Have you successfully logged into a Gnome session?


Gnome shell and gnome tweak tool both installed 
But my desktop is Ubuntu budgie not gnome  but serveral months ago it working  fine (I mean the  tweak  tool )

---

### Post by tea for one on 2017-04-03
I am confused.

You are stating that gnome-tweak-tool worked fine in an Ubuntu Budgie session?

Nevertheless, please log in to a gnome session, open a terminal and enter the following:-

```
gnome-tweak-tool
```

Kindly post the error messages (if any)

---

### Post by davidmohammed on 2017-04-03
A fix for gnome-tweak-tool was applied in the last couple of hours.  Do a normal update and upgrade and gnome-tweak-tool will now open correctly in Ubuntu Budgie/Unity and other GNOME based environments.

---

### Post by tea for one on 2017-04-03
> **davidmohammed said:**
> A fix for gnome-tweak-tool was applied in the last couple of hours.  Do a normal update and upgrade and gnome-tweak-tool will now open correctly in Ubuntu Budgie/Unity and other GNOME based environments.

I must admit that I am surprised that gnome-tweak-tool functioned on a Budgie interface.

I was under the impression that each user interface had a specific utility to fine tune the settings.

Anyway, hopefully the OP will have read your post and managed to get back on track.

Kind regards

---

