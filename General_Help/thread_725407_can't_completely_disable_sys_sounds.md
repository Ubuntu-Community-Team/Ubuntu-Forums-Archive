---
title: "can't completely disable sys sounds"
date: 2008-03-15
forum: General Help
---

### Post by logos34 on 2008-03-15
How do you turn off all gnome system sound effects, EXCEPT music playback?

I've done >system>prefs>sounds>unchecked ESD server, and set all sound effects boxes to "no sound".  Still I get that damn "boink" everytime I save a webpage (and if I choose save complete page, I get "boink, boink, boink, boink, boink, boink..." for every link on the page.  Driving me nuts! Neither logging out/in helps, nor reboot.

---

### Post by Bubba64 on 2008-03-15
system-preferences-sound-soundtab

---

### Post by logos34 on 2008-03-15
> **Bubba64 said:**
> system-preferences-sound-soundtab

That's what I tried...ESD is off and the dropdown menus are set to "no sound".  

Maybe I shoud go muck around in gconf-editor or something.  Gotta be a setting there somewhere. What am I overlooking?

---

### Post by Bubba64 on 2008-03-15
I have found that the no sound has to be set on each of the listed system sounds for it to actually work, you have probably tried that,  I looked around for more notification sound controls,  it seems that there is another place I just don't remember where. If I find an answer you will be the first to know. You could also put a sound that is not installed in the place of the boink boink in sound control in the past when I actually wanted my computer to boink at me when I searched the sounds database some were not there.

---

### Post by pointone on 2008-03-15
If it's the PC speaker making sounds, you can disable it with "sudo rmmod pcspkr".

---

### Post by logos34 on 2008-03-15
> **pointone said:**
> If it's the PC speaker making sounds, you can disable it with "sudo rmmod pcspkr".

That didn't work either.  The module is gone, but still the sound. Also, it's not a generic sound/beep, it's one of the gnome sounds, click, boink, something or other.  

I set all the drop down menus to "no sound' on prefs, logged back in, to no avail. 

It's really annoying because I can't listen to music and download pages in peace.

---

### Post by logos34 on 2008-03-19
bump

Ideas anyone?  There has got to be a way to disable the system sounds in gnome and still hear music

---

### Post by logos34 on 2008-03-20
another bump

---

