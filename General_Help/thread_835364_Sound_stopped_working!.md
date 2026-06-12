---
title: "Sound stopped working!"
date: 2008-06-20
forum: General Help
---

### Post by bunny_basher on 2008-06-20
I just opened Rhythmbox and the sound was muted. So i clicked the sound thing at the top of my screen, which had been muted, and got this...

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Don't have a clue what is wrong, as it has worked for years!
It was straight after an update if that helps - probably not as I don't know what updated :p

Cheers for any help :)
Marcus

---

### Post by dracayr on 2008-06-20
hi,
did you update from gutsy to hardy? in hardy, sound is managed differently.

dracayr

---

### Post by bunny_basher on 2008-06-20
Updated to Hardy a while ago, but there were just a few updates yesterday  that i didnt read - and i just installed them:)

Marcus

---

### Post by bunny_basher on 2008-06-20
Just a little bump if I may!:p NO MUSIC IS DRIVING ME INSANE!

Marcus:)

---

### Post by bunny_basher on 2008-06-20
PLEASE HELP, ive tried many things, but it wont work :(

Marcus

---

### Post by Zorael on 2008-06-20
In a terminal:
```
$ aplay -l
```
If it says 'no soundcard found' or something along those lines, make sure that you have the **linux-generic** package installed. Tag it in Synaptic, Adept Manager, or through terminal alternatives.
```
$ sudo aptitude install linux-generic
```
Reboot your system afterwards for good measure.

---

### Post by bunny_basher on 2008-06-20
Dont work:( I did the ```
aplay -l
```again after, and it still says no soundcard found:(

Marcus

---

### Post by bunny_basher on 2008-06-20
Anyone help?

I dont want to go back to windows!:p

Marcus

---

