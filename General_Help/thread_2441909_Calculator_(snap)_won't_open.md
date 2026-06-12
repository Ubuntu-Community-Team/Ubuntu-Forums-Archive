---
title: "Calculator (snap) won't open"
date: 2020-04-27
forum: General Help
---

### Post by apg6xswhjc on 2020-04-27
Only noticed this the past week or so.

I'm running 19.10 (fully updated), and the calculator is installed as a snap. 

If I try to launch calculator, nothing happens. From the terminal, I get:

```
/snap/gnome-calculator/730/usr/bin/gnome-calculator: error while loading shared libraries: libgtk-3.so.0: cannot open shared object file: No such file or directory

```

How can I fix this?

Thanks

---

### Post by DuckHook on 2020-04-27
:confused:

Why do you have the snap version of calculator?

If you want a standard install then do:
```
sudo snap remove --purge gnome-calculator
```
```
sudo apt install gnome-calculator
```

The calculator should be treated as a system utility, not a snap.

---

### Post by Dennis N on 2020-04-27
Try refreshing the snap packages. One of your libraries may not be the latest.

```
snap refresh
```

---

### Post by Frogs Hair on 2020-04-27
Gnome-calculator and gnome themes were snap by default on 18.04+ and calculator is now back to .deb on 20.04. ```
snap list 
```

---

### Post by apg6xswhjc on 2020-04-27
As said above, the snap calculator was default standard for my initial install 19.04 and current 19.10 install.

snap refresh says All snaps up to date.

snap list:

```

Name                  Version                     Rev   Tracking         Publisher           Notes
acestreamplayer       3.1.49-snap2                10    latest/stable    vs                  -
blender               2.82a                       37    latest/stable    blenderfoundation&#10003;  classic
core                  16-2.44.3                   9066  latest/stable    canonical&#10003;          core
core18                20200311                    1705  latest/stable    canonical&#10003;          base
gimp                  2.10.18                     252   latest/stable    snapcrafters        -
gnome-3-28-1804       3.28.0-16-g27c9498.27c9498  116   latest/stable/…  canonical&#10003;          -
gnome-calculator      3.36.0+git4.51b0dc05        730   latest/stable/…  canonical&#10003;          -
gnome-characters      v3.32.1+git4.e06f0b2        495   latest/stable/…  canonical&#10003;          -
gnome-logs            3.34.0                      93    latest/stable/…  canonical&#10003;          -
gnome-system-monitor  3.32.0-27-g32ed970e06       135   latest/stable/…  canonical&#10003;          -
gtk-common-themes     0.1-36-gc75f853             1506  latest/stable/…  canonical&#10003;          -
gtk2-common-themes    0.1                         9     latest/stable    canonical&#10003;          -
libreoffice           6.4.3.2                     177   latest/stable    canonical&#10003;          -

```

gimp and libreoffice work OK.

---

### Post by Dennis N on 2020-04-27
Try reverting to the previous version:
```
snap revert gnome-calculator
```
Also, I have **gnome-3-34-1804** which your list does not show. You could install that and see if it's needed. We do have the same Calculator revision (REV) 730.

---

### Post by DuckHook on 2020-04-27
> **Frogs Hair said:**
> Gnome-calculator and gnome themes were snap by default on 18.04+ and calculator is now back to .deb on 20.04. ```
snap list 
```
Thanks for the clarification. As one who sticks to LTS releases, I wasn't aware of this. Sometimes, these development decisions just leave me shaking my head.

---

### Post by apg6xswhjc on 2020-04-27
> **Dennis N said:**
> Try reverting to the previous version:
```
snap revert gnome-calculator
```
Also, I have **gnome-3-34-1804** which your list does not show. You could install that and see if it's needed. We do have the same Calculator revision (REV) 730.

Wait, what?

So I've got 3.28 installed via snap and it doesn't update itself to later versions?

Now I'm confused:

gnome-shell --version shows:

GNOME Shell 3.34.3

:(

---

### Post by Dennis N on 2020-04-28
> **apg6xswhjc said:**
> Wait, what? So I've got 3.28 installed via snap and it doesn't update itself to later versions? Now I'm confused:
gnome-shell --version shows:
GNOME Shell 3.34.3
:(
You would only have the 'newer' one (gnome-3-34-1804) if some snap you install uses it. I wouldn't infer any connection of those numbers to a gnome shell version. Just a coincidence. Anyway, If it doesn't help, then I'd just remove the snap version of Gnome Calculator and install the package from the Ubuntu repository. 

And as far as I know, there's no command to tell us which supporting packages each snap application needs. Those should all be installed along with the snap applications.

---

### Post by apg6xswhjc on 2020-04-28
Just for my own curiosity, I snap remove'd gnome-calculator, then did a snap install gnome-calculator. And after waiting ages for it to install while at "Automatically connect eligible plugs and slots" it finally completed. And calculator now works.

Guess what snap list showed? Only change from previous was that gnome-3-34-1804 had been installed! :rolleyes:

So I assume there had been an update to the gnome-calculator snap that did not correctly check what version of gnome was required as well.

One thing you mentioned that I'd like to verify:

Is there really no way to tell dependencies between snap packages? 

Eg if gnome-3-28 snap that I still have installed was only required by gnome-calculator snap, I'd like to remove that. But how can I check the dependencies of/for gnome-3-28 snap?

TIA

---

### Post by Dennis N on 2020-04-29
Thanks for the update. I would agree with your analysis - the Calculator originally worked with the gnome-3-28-1804, then got updated, but the newer library wasn't installed with the update. I could have gotten the needed gnome-3-34-1804 when installing another snap. That could be why I never had your problem. I also have both the 28 and 34 versions installed.

> Is there really no way to tell dependencies between snap packages? Eg if gnome-3-28 snap that I still have installed was only required by gnome-calculator snap, I'd like to remove that. But how can I check the dependencies of/for gnome-3-28 snap?
 
Not that I have found. If you discover how, post it here please.

---

### Post by apg6xswhjc on 2020-04-29
Speech. 

I have *NO SPEECH*.

I thought snap was a system that is supposed to address 'dependency hell'. But it has a system that supports dependencies, yet cannot even identify parents, children or orphans???

Please tell me I'm wrong and am a noob?

---

### Post by DuckHook on 2020-04-29
I wouldn't go so far as to say you are "wrong", and only you can tell us if you are a noob. :)

However:

[list=1]
[*]All apps have dependencies. Snaps just disconnect theirs from the system's so that you can have two otherwise incompatible dependencies happily co-existing. That's the theory at any rate.
[*]They also allow apps to be updated quickly by their own developers without having to depend on the distro maintainers to get around to it, which is infrequently at best.
[*]But even the best devs make mistakes. C'est la vie.
[*]That said, why is something as primitive and unchanging as a calculator app being pushed out as a Snap? This is simply feature creep and makes no sense.
[/list]

---

### Post by apg6xswhjc on 2020-04-29
OK, I'm gonna have to tap out on this snap stuff before I lose it.

Marking as solved. In summary:


[LIST]
[*]Uninstall and then reinstall snap
[*]Uninstall snap and install via apt
[/LIST]
 
are the two easiest solutions. And Ubuntu is moving away from snap for things as critical as calculator from 20.04, so that gives an indication on what the best of these solutions is.

Thanks to everyone for their help

---

