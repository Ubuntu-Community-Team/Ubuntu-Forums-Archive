---
title: "Ristretto skips pictures"
date: 2016-05-11
forum: General Help
---

### Post by SamInside on 2016-05-11
I use *Xubuntu 14.04.4 LTS trusty*.
I have a folder full of images, all PNG.
I click on a random one.
I press the "&#8594;" button or the relative keyboard key to watch the next pictures, but Ristretto skips some of them [s]with no recognizable pattern/reason.[/s] because it reads first uppercase letters then lowercase: see post [http://ubuntuforums.org/showthread.php?t=2324128&p=13488158#post13488158](http://ubuntuforums.org/showthread.php?t=2324128&p=13488158#post13488158)

---

### Post by vasa1 on 2016-05-11
If you make a note of which ones are skipped, are the same ones always skipped?
Does any other image viewer show all the images? Have you tried with Mirage?

---

### Post by ajgreeny on 2016-05-11
I have found ristretto to be very unpredictable in the past as well, so have changed the default application to view images, and removed ristretto completely from my machine.

However more recently I have found it to be much better so leave it installed and just view with something else if necessary; I like eog, but there is a mass of options for you to use.  I have not personally had any problems with it for a very long time now.

It may also be worth trying removal or renaming of the hidden ~/.config/ristretto folder in your home to see if that improves its abilities.

---

### Post by SamInside on 2016-05-12
Ok, I got it. It doesn't skip the images, it's just that it processes first uppercase letters and then lowercase, basically it orders the files respecting 100% the ASCII table. Problem is that Thunar doesn't do that. So it's a kind of an incompatibility between the file manager and Ristretto.
I guess it needs a feature: in "Preferences" there should be something to choose the ordering method or which file manager you use.

---

### Post by ajgreeny on 2016-05-12
I am not using my Xubuntu box at the moment so do not have that hidden ristretto config file to check but you could look to see what is in the file in the config folder. I can not remember exactly what preferences are mentioned in the file but maybe there is something you can find that lets you change the sort method.

Worth a good look, I think.

---

### Post by Dennis N on 2016-05-12
Ristretto on my Xubuntu 16.04 disregards case when browsing through a collection of pictures of mixed upper and lower case, so must be a setting somewhere? I don't see anything relevant in the Ristretto preferences.

---

### Post by SamInside on 2016-05-13
> **ajgreeny said:**
> I can not remember exactly what preferences are mentioned in the file but maybe there is something you can find that lets you change the sort method.
Any interesting things I see are:
```
; (gtk_accel_path "<Actions>/RsttoWindow/sorting-menu" "")
[...]
; (gtk_accel_path "<Actions>/RsttoWindow/sort-filename" "")

```
that I wouldn't know how to edit.

> **Dennis N said:**
> Ristretto on my Xubuntu 16.04 disregards case  when browsing through a collection of pictures of mixed upper and lower  case
Hrmmm... weird. As you said, no relevant setting on "Preferences" so I don't know. I have *14.04.4 LTS trusty*.

[SIZE=1]BTW I mailed the developer, you never know...


[/SIZE]

---

