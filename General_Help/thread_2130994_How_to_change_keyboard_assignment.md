---
title: "How to change keyboard assignment?"
date: 2013-03-31
forum: General Help
---

### Post by oxf on 2013-03-31
A quick question..

Is the key assignment, i.e which keys on the keyboard are assigned to a particular letter etc controlled by the bios or by the opperating system? I believe it is the OS?

In which case how do I change it? I have an essentially dead key (left shift) and since there's another key nearby that's not used (the windows key) I thought I'd reassign it to that and get a bit more life out of this laptop.

The laptop is a Compaq Presario M2000 but I suspect that makes no difference.

Thanks

---

### Post by schragge on 2013-03-31
Make a file, say *~/.xmodmaprc* containing the following:
```

remove Shift = Shift_L
remove Mod4 = Super_L
keysym Super_L = Shift_L
keysym Shift_L = Super_L
add Mod4 = Super_L
add Shift = Shift_L

``` and execute the following in a terminal:
```

xmodmap ~/.xmodmaprc

``` If this works as expected, add the command above to *~/.xsessionrc*

---

### Post by oxf on 2013-04-01
Thanks for the reply. A couple of points..

1. /.xsessionrc  doesn't seem to exist, at least I can't find it where you suggested, so wheres it located :confused:

2. Is there an already existing file that controls the keyboard map that could be edited, i.e something that would be easy to change any key assignments should I want to in the future?

Thanks

Katya

---

### Post by schragge on 2013-04-01
> **oxf said:**
> 1. /.xsessionrc  doesn't seem to exist, at least I can't find it where you suggested, so wheres it locatedYes, the file doesn't exist, it should be created from scratch. Also, note [COLOR=#FF0000]~[/COLOR] in *[COLOR=#FF0000]~[/COLOR]/.xsessionrc* It should be located in your home folder. You can do it like this in terminal:
```

cat<<EOF >~/.xmodmaprc
remove Shift = Shift_L
remove Mod4 = Super_L
keysym Super_L = Shift_L
keysym Shift_L = Super_L
add Mod4 = Super_L
add Shift = Shift_L
EOF
echo xmodmap ~/.xmodmaprc >~/.xsessionrc

```

> 2. Is there an already existing file that controls the keyboard map that could be edited, i.e something that would be easy to change any key assignments should I want to in the future?Sure, the files are under */usr/share/X11/xkb*. Configuration is described [here]("http://pascal.tsu.ru/en/xkb/setup.html") and [here]("http://www.charvolant.org/%7Edoug/xkb/html/"). You'll see your current settings in the output of ```
setxkbmap -query
```.

---

### Post by oxf on 2013-04-01
OK thanks for all that. Not so difficult when you know how!. 
I've now reassigned that key.

---

### Post by jackclarck on 2013-04-02
All the keys are very useful, i'm also looking for these keys so its also very much much helpful for me .Thanks

---

