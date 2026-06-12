---
title: "Gnome issues"
date: 2008-06-18
forum: General Help
---

### Post by sgreimer on 2008-06-18
Hi, I just updated Hardy to the latest kernel which broke my Nvidia config. So I booted into the previous kernel version 2.6.24-18 and I am experiencing Gnome issues.

My theme changed to some sort of default. If I change the theme, nothing happens but going back to Preferences -> Appearance the theme I picked is still selected.

Also, my background image disappeared and if I attempt to change it, only the background color will change and no image is set.

Any ideas? I don't know what log file would report these sorts of issues.
Thanks

---

### Post by bubba_169 on 2008-06-18
I'm sure I got an error message pop up before, something about the gnome-settings-daemon not running, then after that I got bugs similar to yours! Don't know if that can help you...

---

### Post by sgreimer on 2008-06-18
I had a message earlier saying that my gnome-power-manager had configuration errors. but I solved that by reinstalling.

I've also tried re-installing ubuntu-desktop but no luck.

---

### Post by cdtech on 2008-06-18
Did you try:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)

While your in the kernel...

---

### Post by sgreimer on 2008-06-18
Good idea, but I get "already the newest version"

---

### Post by sgreimer on 2008-06-19
I solved some of the issues by reinstalling gnome-settings-daemon, however, 2 issues still remain.

1. Changing the mouse acceleration through gnome doesn't work. It just goes really slow and if I move the slider it doesn't do anything.

2. My desktop background doesn't show. Just the set background color.

I'm guessing there's another gnome piece to try reinstalling.
Has anybody experienced this before?

---

### Post by sgreimer on 2008-06-19
I just solved it. I found a solution here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446212](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446212)

Turns out all my gconf settings had disappeared from a bad update. Re-registering did the trick. 

# rm -f /var/lib/gconf/defaults/*
# gconf-schemas --register $(ls /usr/share/gconf/schemas)

---

### Post by Ignat on 2008-06-26
Wow! This solution:

# rm -f /var/lib/gconf/defaults/*
# gconf-schemas --register $(ls /usr/share/gconf/schemas)

solved a bunch of problems I was having:

1. Error messages about Gnome Power Manager defaults
2. Could not get any images as desktop backgrounds, only colors.
3. Lost all the normal controls on window titlebars.

This fixed all these problems at once. Thanks!

---

