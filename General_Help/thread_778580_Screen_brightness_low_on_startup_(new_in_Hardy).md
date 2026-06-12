---
title: "Screen brightness low on startup (new in Hardy)"
date: 2008-05-02
forum: General Help
---

### Post by klaasvanschelven on 2008-05-02
Hi


I've "upgraded" (reinstalled from scratch) to hardy and am now experiencing a number of problems. One of them is this:

On startup my laptop screen is extremely dark. This can be easily fixed by pressing the appropriate Fn combination, but having this on every startup is still annoying. Any ideas how this is 1] introduced in Hardy and 2] solvable? Thanks!

---

### Post by g_damian on 2008-05-02
[http://ubuntuforums.org/showthread.php?p=4861714#post4861714]("http://ubuntuforums.org/showthread.php?p=4861714#post4861714")

> solution for startup brigtness:
[LIST=1]
[*]grab my script from [http://dmn.jogger.pl/2008/05/02/ubuntu-8-04-i-jasnosc-lcd-rozwiazanie/]("http://dmn.jogger.pl/2008/05/02/ubuntu-8-04-i-jasnosc-lcd-rozwiazanie/")
[*]save it
[*]check if line "DIR=..." is good for you, customize it
[*]add path to the script to /etc/rc.local before "exit 0"
[*]now startup brigtness is that from top of the script. you can change it if you want
[/LIST]
**BUT:** laptop keys doesn't work when you do this. to modify brightness go to terminal and type:
```
sudo /path/to/script x
```
where *x* is brightness, usually from 0 (min) to 13 or 15 (max).

---

### Post by klaasvanschelven on 2008-05-02
Thanks g_damian

Any idea why this doesn't work anymore (or rather: differently) since Hardy? And who I should tell / file a bug so that people including don't run into it in the next Ubuntu?

---

### Post by mcurran on 2009-03-22
Strangely, this problem did not occur with my laptop and the default kernels for either Hardy or Intrepid, but once I upgraded my kernel to 2.6.27-13; my computer would start with the LCD at about 20% brightness.  I am reluctant to use solution above, because I don't want to break the Fn+F5 or Fn+F6 key combination/bindings that are already configured correctly and or the whole acpi key functions for lapsus or asusacpi or whatever, but if anyone has any other ideas; please share.

---

### Post by davo11 on 2009-03-22
in the gnome panel, have you tried right clicking the battery icon, select preferences and you can set the brightness from there.

---

### Post by BelaC on 2009-03-22
> **davo11 said:**
> in the gnome panel, have you tried right clicking the battery icon, select preferences and you can set the brightness from there.

Sorry for disturb -and for my english too- I just try to find solution for my "similar" problem
I tried to set brightness over there but doesn't work -on an another forum I got an advice as I need to install Kpowersave- after I move brightness pointer fading back my screen and over my Fn keys also I have no any change.

I'm not remember exactly but running Live version -before install- I haven't this trouble. Now I run Xubuntu 8.1 on a laptop.

Have somebody any advice? (I'm newbie in Linux with some experience)

---

