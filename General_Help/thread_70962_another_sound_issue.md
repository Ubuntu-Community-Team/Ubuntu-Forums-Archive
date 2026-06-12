---
title: "another sound issue"
date: 2005-10-01
forum: General Help
---

### Post by cd root on 2005-10-01
I have a Yamaha XWave soundcard and i get no sound after the default Ubuntu install.

When I select Applications - Sound and Video - Volume Control

I get the error:

No Volume Control elements and/or devices found

When I select Applications - Sound and Video - Volume monitor

I get the error:

Cannot Connect to sound daemon. Please run 'esd' at command prompt

Subsequently, when running sudo esd at the command prompt

I get the error:

/dev/dsp: No such file or directory

Seems like I'm at a dead end. Any help would be great. Thanks

---

### Post by ultramancool on 2005-10-02
[QUOTE=cd root]I have a Yamaha XWave soundcard and i get no sound after the default Ubuntu install.
When I select Applications - Sound and Video - Volume Control
I get the error:
No Volume Control elements and/or devices found
When I select Applications - Sound and Video - Volume monitor
I get the error:
Cannot Connect to sound daemon. Please run 'esd' at command prompt
Subsequently, when running sudo esd at the command prompt
I get the error:
/dev/dsp: No such file or directory
Seems like I'm at a dead end. Any help would be great. Thanks[/QUOTE]

I'm not sure what kernel modules you would have to load for that sound card but, you must go to a console and:
modprobe (soundcardmodule)

---

