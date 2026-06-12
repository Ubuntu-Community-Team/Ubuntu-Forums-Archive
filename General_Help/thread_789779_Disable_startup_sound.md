---
title: "Disable startup sound"
date: 2008-05-10
forum: General Help
---

### Post by Ryandor on 2008-05-10
Typically, I see threads in here on trying to get sound working, however mine appears to work perfect, to a flaw...

I've disabled the "Login Successful" sound in System -> Administration -> Login Window -> Accessibility, however, it still makes the login.wav sound when logging in. Other settings in the Login Window settings work (changing the login screen, for example).

Is there something I'm missing? Or is there an alternative way to disable it? (Other than deleting the offending wav file)

Thanks,

Ryandor

---

### Post by grannyw on 2008-05-10
I'm not sure,but maybe you sould try to check if it possible to do through "set-up manager"

---

### Post by dnairb on 2008-05-10
System -> Preferences -> Sound -> Sounds tab

Log in sound at the bottom

---

### Post by Ryandor on 2008-05-10
No joy.. 
I'm not sure how to get to set-up manager (missing the obvious?)
System -> Preferences -> Sound -> Sounds tab: Changed the setting, but no change.

This is really getting annoying :(

FYI: Running Ubuntu Hardy 8.04. If memory serves, I don't think I've ever been able to disable the login sound on any ubuntu install.

-Ryandor

---

### Post by drs305 on 2008-05-10
So in System, Preferences, Sound, Sounds - for Log in you have "No sound" ?
You can also uncheck the Play System Sounds at the top of the same screen. I have never used system sounds and don't miss them. If it annoys you, you could probably do without them all ;)

---

### Post by Ryandor on 2008-05-10
The weird thing is, I've not heard any system sounds at all anyway. Other than the login sound, the only sound I've heard is a system (motherboard) beep on the "ready to login" screen.
I've tested sound, and regular mp3's and movies work just fine.

All things considered it's not that important. I'm too busy moving files around at this point. Converting my old Windows ntfs drives to ext3. It takes forever to move ntfs files...

-Ryandor

---

### Post by vikramaditya on 2008-05-16
lol that startup sound makes me jump everytime :) just disabled all system sounds thanks!

**EDIT** must also go system/admin/login window/accessibility tab & under "sounds" uncheck "login screen ready"

---

### Post by Franko30 on 2008-05-23
> **vikramaditya said:**
> 
**EDIT** must also go system/admin/login window/accessibility tab & under "sounds" uncheck "login screen ready"

Hi there,

many thanks - that's what I was searching for like crazy! But it's not always easy when the setup is German, so searching for "Anmeldefenster" wouldn't exactly find the correct posts. ;-)

[B]Finally I can disable this annoying drumroll at the login screen during startup.
[/B]:popcorn:

This was especially annoying, as the volume settings won't stick anymore since I'm using Hardy 8.04, maybe thanks to Pulse audio - didn't find a solution in a whole evening of forum search. So I always had a drumroll at maximum volume at startup. Wouldn't dare to startup my laptop on a train anymore...

Thanks again

Franko30

---

### Post by Bott on 2008-05-26
I can't get that System>Preferences>Sound way to get anything other than the Ubuntu login and logout wavs to play, but it does turn them off for me.  I think you can uninstall the ubuntu-sounds in Synaptic Package Manger and get rid of it.  You can then reinstall the package later if you'd like it back.  You could make backup copies of the wav files in /usr/share/sounds and then delete them.

---

### Post by airjaw on 2008-12-05
The startup sound after I login still plays for me, even though I disabled both the login drum and the startup sound after logging in.

I think this is probably a bug.

---

