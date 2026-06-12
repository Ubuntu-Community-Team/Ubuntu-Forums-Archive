---
title: "Can't change desktop wallpaper"
date: 2008-06-03
forum: General Help
---

### Post by lars-5 on 2008-06-03
i don't know when the problem started, but recently when i attempt to change the desktop background in the appearance preference i can't select a wallpaper by clicking it, and can only navigate through my wallpapers by using the keyboard.

any suggestions?

---

### Post by PinkFloyd102489 on 2008-06-03
Open a terminal and input this:

```

gconf-editor

```

In the window that pops up, navigate to /apps/desktop/gnome/background and input the path to the picture file in picture_filename.

---

### Post by lars-5 on 2008-06-03
thanks for the reply, but that doesn't exactly solve the problem of not being able to use my mouse and click on a wallpaper in the preferences window to set it... all the buttons and tabs work, it just the box with my wallpapers that does nothing when i click on it.

edit: solved by today's update.

---

### Post by Ohwii on 2008-06-06
do you remember what you installed ? 

because that problem that you described is happening on my ubuntu.

any help 

ohwii

---

### Post by steppres on 2008-06-06
I'm experiencing the same problem here. I think it's due to a recent update of nautilus. I noticed if you click around randomly on the wallpaper you want, it will eventually select it. I'm just going to wait until the next batch of updates and see it it gets fixed.

---

### Post by Ohwii on 2008-06-06
is anyone also experiencing a slower opengl support because my screensaver for instance if very slow?

---

### Post by Jordanwb on 2008-06-18
I'm having the same problem too. I don't like the "Hardy" Heron background. Who comes up with these names?

---

### Post by sethd32 on 2008-06-18
I was experiencing this too, but it went away with the slew of updates that have been out the last few days.  Try updating and see if that does the trick.

---

### Post by Jordanwb on 2008-06-19
I have all the updates. Your serve.

---

### Post by Jordanwb on 2008-06-20
It would be very useful to know that the backgrounds cannot be in the jpeg format. I changed it from jpg to png in GIMP and it worked. :mad:

---

### Post by nickdbliss on 2008-06-21
I had the same problem but updating my system sorted out the problem. Cheers.

---

### Post by tcbopper on 2008-06-21
Same thing.....Just today....after a reboot....nothing installed...the background didn't "show up"..AND  ...my desktop isn't there either.  Unable to change the background.

---

### Post by tcbopper on 2008-06-21
That worked.....thanks

---

