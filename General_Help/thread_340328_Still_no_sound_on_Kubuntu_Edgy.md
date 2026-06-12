---
title: "Still no sound on Kubuntu Edgy"
date: 2007-01-17
forum: General Help
---

### Post by Rhapsody on 2007-01-17
I've recently upgraded to Kubuntu Edgy, and I've somehow managed to lose all sound in the process. I can get sound from a Kubuntu Edgy live CD, so I know that it's something about this install that's made the sound stop, but I haven't a clue what. My sound card is a Sound Blaster Audigy.

I've currently not had any sound from this system for more than a week and I've managed to get absolutely no help on this.

---

### Post by anaconda on 2007-01-17
Here is a good sound problem solutions guide that I used recently.
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)


My problem was solved by this:
> A very common cause for a user to not have sound is not having his/her username in the /etc/group
I actually didn't have the rights to use my soundcard!! Otherwice it was working properly :)
 
Just brought this up, because if you have the same problem, then you should know that there is a mistake in the above instruction eg:
```
audio:x:29:root:moocow
```
should read:
```
audio:x:29:root,moocow
```
so "," instead of ":"

---

### Post by Rhapsody on 2007-01-17
Nope, definitely not that. The line I found in /etc/group was exactly what I expected. I've also tried the "aplay -l" command (my sound card was detected), tried alsamixer (everything was fine) and even tried reinstalling the ALSA drivers (still no sound).

My sound card is definitely working, Kubuntu definitely detects it, it's definitely not muted, and the drivers seem to be OK too. Yet despite all that, I'm **still** getting no sound!

---

### Post by Homie Bongo on 2007-01-17
I might have the same problem. My sound on Audugy had been working until sometime yesterday. It was all okay but since then it hasn't produced a tone. I thought I messed something up when I was playing with Beryl and some window managers, but it shouldn't cause sound problems.

My problem isn't with groups either: I am in the sound group (and other 'administrator' groups) and more importantly before anybody is logged in GDM plays sound, but not anymore. I also tried tips from this great guide: [Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards(...)]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching")
 but so far nothing plays! :(

I'll stay tuned

---

### Post by Rhapsody on 2007-01-17
My problems started simply from upgrading. I've never had sound problems with Breezy Badger or Dapper Drake, and I still think of compositing window managers as a gimmick for now, so I've avoided them.

This really is a mysterious problem.

---

### Post by MrE on 2007-01-30
I have the same problem here and can't seem to find a solution anywhere.

I'm running Kubuntu 6.10

---

### Post by mstrello on 2007-02-04
Sorry for the question, but do you check the PCM channel (using kmix or alsamixer)?
I was a couple of hours without sound when I installed Edgy for this stupid reason :) 

Regards,
-- 
Mauricio.

---

