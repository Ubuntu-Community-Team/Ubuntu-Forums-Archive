---
title: "Nautilus doesnt open after &quot;nautilus -q&quot; was ran from terminal"
date: 2016-08-09
forum: General Help
---

### Post by goodelyfe on 2016-08-09
File explorer/browser does NOT open after i entered > nautilus -q

furthermore, it broke my variety app? 

Just thought i'd mention that because everything was working fine now i cant even switch my wallpapers.



I tried purge, reinstall of nautilus as well as ubuntu desktop.... no cigar



16.04

---

### Post by goodelyfe on 2016-08-09
more backdrop: 

i was installing pushbullet indicator? and wanted to restart nautilus. Obviously a bad idea? 

my output was something as follows:

```
sys:1: PyGIWarning: Nautilus was imported without specifying a version first. Use gi.require_version('Nautilus', '3.0') before import to ensure that the right version gets loaded.No module named requests



```

stuff saved to the desktop is 'gone' (from visible desktop) and i cannot change wallpaper..... Variety does change screensaver/login screen wallpaper?

---

### Post by CantankRus on 2016-08-09
Try a reboot.
Nautilus draws the desktop so if not running the desktop will behave as you stated.

---

### Post by goodelyfe on 2016-08-10
reboot definitely doesnt fix it. still can not open file explorer

---

### Post by CantankRus on 2016-08-11
> **goodelyfe said:**
> reboot definitely doesnt fix it. still can not open file explorer
What did you do to install "pushbullet indicator"?
Are you using ppas?

---

### Post by goodelyfe on 2016-08-11
indeed!

i thought about that afterwards?!?!!???

atareao/pushbullet

---

### Post by mc4man on 2016-08-11
Can you open a terminal?
(- don't see where pushbullet itself would be an issue or even in conjunction  with variety though variety, or lack of, may be behind your current issue

---

### Post by CantankRus on 2016-08-11
I can install pushbullet from the ppa without issue.
I see the error message in your first post whether pushbullet is installed or not.
I think the error message is related to python-nautilus for python extensions but nautilus should still start.

---

### Post by goodelyfe on 2016-08-11
> **mc4man said:**
> Can you open a terminal?
(- don't see where pushbullet itself would be an issue or even in conjunction  with variety though variety, or lack of, may be behind your current issue


yea i cant see why it would be an issue either



it only gave me an issue when i tried to restart nautilus (nautilus -q)


i can open a terminal and caja but i still cannot open/change wallpaper/variety program nor open nautilus/file explorer

---

### Post by mc4man on 2016-08-11
What happens with this command?
```
gtk-launch nautilus
```

Note: nautilus -q stops (quits) nautilus, does not 'restart nautilus'

---

### Post by goodelyfe on 2016-08-13
> **mc4man said:**
> What happens with this command?
```
gtk-launch nautilus
```

Note: nautilus -q stops (quits) nautilus, does not 'restart nautilus'


yea my fault, i didnt mean to imply it did....


i got the same output

```
sys:1: PyGIWarning: Nautilus was imported without specifying a version first. Use gi.require_version('Nautilus', '3.0') before import to ensure that the right version gets loaded.No module named requests



```

---

### Post by mc4man on 2016-08-13
Sure seems to be something you've added that affects nautilus, variety obviously would, have you any nautilus-python extensions installed?
I'd likely disable or remove variety & any .cache, .config, or .local  files associated with it including the autostart .desktop

Does this open a nautilus window?
```
nautilus --new-window
```

---

### Post by goodelyfe on 2016-08-14
nope gives same output


and i dont think i've added any python extensions that caused it to stop working....at least not that i can remember!

thanks for the help!

---

### Post by mc4man on 2016-08-14
Then I'd for the moment get rid of variety (if not already?
Also - log into a guest session & see if nautilus works.

---

### Post by goodelyfe on 2016-08-14
logged in guest, no cigar....

infact....the desktop was black lol. also when i clicked unity? (start button?) backdrop was black as well


clicked on file explorer on the left, no cigar!!!

fired up a terminal window, no cigar!!!! same output.

baffled lol what gives!!!!

---

### Post by mc4man on 2016-08-14
baffled is a good description..
Back on your user does this change the background?
```
gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/warty-final-ubuntu.png
```

---

### Post by tsjswimmer on 2016-08-14
Have you tried removing this push indicator? If not, perhaps doing so will fix the problem.

If nautilus refuses to play nice, perhaps you could replace it with a Gnome-friendly version of Nemo. See [here]("http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html") for more instructions.

---

