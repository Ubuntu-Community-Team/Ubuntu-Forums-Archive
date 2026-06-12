---
title: "Sound in only one program at a time"
date: 2008-06-03
forum: General Help
---

### Post by TWO on 2008-06-03
Is there anyone who knows how to solve the problem of only being able to use one program with sound at one time?

It's not that I want two programs playing sound at the same time, it's just that it starts to become a little troublesome when say I have TuxGuitar open then I want to open Songbird to listen to a track and I have to shut one program done to allow the other to play sound. It's a problem that often effects VLC as well.

It was a pretty annoying problem under Kubuntu, in that every other moment, if you had multiple programs open, it was asking you to shut down one sound server or another. 

Under Ubuntu, it's equally as annoying, but there aren't any requests to shut down one sound server or another...

Any advice would be greatly appreciated.

Many Thanks

TWO

---

### Post by daleus on 2008-06-03
Go to System - Preferences - Sound and make it so every dropdown next to the "test" buttons all say "Alsa"

This works for me, allows me to use Teamspeak + firefox + Amarok + vlc, without one program taking over.

---

### Post by TWO on 2008-06-05
> **daleus said:**
> Go to System - Preferences - Sound and make it so every dropdown next to the "test" buttons all say "Alsa"

This works for me, allows me to use Teamspeak + firefox + Amarok + vlc, without one program taking over.

Bah! It doesn't seem to work for me! When I open Skype with another program using sound it tells me that there are Audio problems... :confused:

Anyone know where to go from here?

Thanks

TWO

---

### Post by Plasma_NZ on 2008-06-05
> **TWO said:**
> Bah! It doesn't seem to work for me! When I open Skype with another program using sound it tells me that there are Audio problems... :confused:

Anyone know where to go from here?

Thanks

TWO

goto menu > system > preferences > Sound - choose the "Sound" tab and untick ESD.. also set all sound devices to alsa.. reboot my be required to fix your problem :)

---

### Post by TWO on 2008-06-05
> **Plasma_NZ said:**
> goto menu > system > preferences > Sound - choose the "Sound" tab and untick ESD.. also set all sound devices to alsa.. reboot my be required to fix your problem :)

Deary me! It's not having any of it. Not a difference, still only allowing one program to use sound at a time and what's more, doing that seems to stop system sounds as well...

That can't be right?

:confused:

TWO

P.S Saying that, I've known this no other way! But I think by now more than one program should be able to use sound at the same time!

---

### Post by ayampanggang on 2008-06-05
i've just faced this problem and post this a few hours ago and that ESD and Alsa switch thing fixes mine. 

Did you use gutsy before you use hardy (you're using hardy arent you?). If so did it occur to you while in gutsy?

---

### Post by TWO on 2008-06-05
> **ayampanggang said:**
> i've just faced this problem and post this a few hours ago and that ESD and Alsa switch thing fixes mine. 

Did you use gutsy before you use hardy (you're using hardy arent you?). If so did it occur to you while in gutsy?

Yeah, I used Gutsy before I used Hardy and I remember sound not working in one thing whilst it did in another. Certainly as far as Kubuntu was concerned anyway as I switched to that for a while. 

I changed everything to ALSA and unchecked ESD, rebooted and still found that multiple programs couldn't play sound simultaneously...

:confused:

TWO

---

