---
title: "tablet, desktop backround &amp; screen rotation"
date: 2008-03-21
forum: General Help
---

### Post by psyced on 2008-03-21
I'm using an x41 tablet in ubuntu 7.04. After setting up the acpi events ([see here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_on_a_ThinkPad_X41_Tablet")) for swivel down and up, I also wanted to change the desktop background when it swiveled so I added a gconf change in the up/down script.

When executing the script's from a terminal the background changes correctly, but when swiveling the background won't change.

**x41tsdown.sh*** - x41tsup.sh is the all the same, except for the bg image and the rotation*
```
echo 'Rotating screen...'
if [ "`/usr/bin/xrandr -o right -v | grep -i 'randr' | wc -l`" -ne "1" ]
then
    echo '!! Something went wrong...'
    export DISPLAY=":0.0"
    export XAUTHORITY=/var/lib/gdm/\:0.Xauth
    /bin/xset -display $DISPLAY dpms
    echo 'Trying to rotate again...'
    /usr/bin/xrandr -o right
fi
echo 'Rotating stylus...'
/usr/bin/xsetwacom set stylus rotate 1
echo 'Set bground...'
/usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename /home/timhow/bg_2.png
```

---

### Post by psyced on 2008-03-22
I also redid the acpi event files (x41t-swivel-down & x41t-swivel-up) and didnt do the chmod or chown parts, because I thought it would be trying to set root's background image.

Still stuck!

---

### Post by psyced on 2008-03-22
I am so lost with this, surely there is someone out there that can help...

---

### Post by psyced on 2008-03-27
no one?

---

### Post by psyced on 2008-03-28
Can I atleast get someone to tell me its against the rules to bump over and over and over and over and over and over and over and over and over and over and over and over and over......?

---

### Post by psyced on 2008-04-26
hi

---

