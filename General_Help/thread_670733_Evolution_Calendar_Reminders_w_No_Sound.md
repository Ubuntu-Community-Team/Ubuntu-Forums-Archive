---
title: "Evolution Calendar Reminders w/ No Sound"
date: 2008-01-17
forum: General Help
---

### Post by r.lopez.negrete on 2008-01-17
Hi All,

I have been using Evolution Calendar for a while now without any problems. Today I realized that even though I set up reminders to play sounds (specific wav files I chose), I haven't heard them at all. I even tested a couple, and I could hear nothing. The popups work fine, and the sound alarms in the mail component work fine too. It's just the calendar notifier that is not being able to play sounds.

Does anybody know how to start locating the problem. I still haven't found a way to possibly diagnose it. 

Any help will be very appreciated.

Thanks all,
 rodrigo

---

### Post by dcstar on 2008-01-18
> **r.lopez.negrete said:**
> Hi All,

I have been using Evolution Calendar for a while now without any problems. Today I realized that even though I set up reminders to play sounds (specific wav files I chose), I haven't heard them at all. I even tested a couple, and I could hear nothing. The popups work fine, and the sound alarms in the mail component work fine too. It's just the calendar notifier that is not being able to play sounds.

Does anybody know how to start locating the problem. I still haven't found a way to possibly diagnose it. 
......

It seems that it is a bug (on my system I can hear the PC speaker beep), you can use Evolution to report it.

---

### Post by lubeck on 2008-01-24
I have exactly the same issue, except I do notice that the Calendar alarm does activate the little computer speaker (not the .wav file I have specified) and it beeps once.  I have been looking and cannot find fix or anyone else with the issue.  Let me know via private note if you find anything.  Weird as heck that no one else has fixed.

---

### Post by GMachine_24 on 2008-03-11
I have the same problem and if anyone finds a solution please POST IT HERE instead it letting people know via private chat as it is a widespread problem that, I'm sure, most Evolution users are interested in fixing.

Thanks.

gm

---

### Post by frogotronic on 2008-03-18
> **r.lopez.negrete said:**
> Hi All,

I have been using Evolution Calendar for a while now without any problems. Today I realized that even though I set up reminders to play sounds (specific wav files I chose), I haven't heard them at all. I even tested a couple, and I could hear nothing. The popups work fine, and the sound alarms in the mail component work fine too. It's just the calendar notifier that is not being able to play sounds.

Does anybody know how to start locating the problem. I still haven't found a way to possibly diagnose it. 

Any help will be very appreciated.

Thanks all,
 rodrigo

How did you get the mail *.wav sounds to work?   Where did you place (what directory) the *wav files?

- CH

---

### Post by analystscouch on 2008-03-31
I have a similar problem. On my desktop when new mail arrives I hear the PC beep instead of the wav file. On my laptop I hear the wav file. Both are recent clean installs of the hardy beta with all updates installed.

---

### Post by ACGarland on 2008-04-09
I'm also seeing this problem: alarms are completely silent in evolution -- no matter whether I specify a custom sound or I launch a custom program (aplay with a sound file). Hard to believe a package which serves up reminders for lots of people could be released without basic sound capabilities working.  (My laptop doesn't even make a 'beep' that others have mentioned.)  Not very helpful as a reminder :(

---

### Post by MarnixV on 2008-05-20
Same problem here: popup in bottom right corner, then little icon in system tray. No sound at all.

Running a fresh 8.04 installation, on a Dell latitude D830 laptop.

Hoping for a solution, because without sound, I'm missing apointments... :)

---

### Post by r.lopez.negrete on 2008-05-20
This is a possible work around.

OK here's what I have been doing that works for me. I add a customized alarm, but I select to run a program. For the program you can select mplayer, aplay, play, whatever you prefer, and the arguments should be the location of the file you want to use as an alarm.

Program:   aplay
Arguments: /usr/share/sounds/warning.wav

The first time it does this it will send a warning and not play the sound, but if you tell it to not ask again it should work for the rest.

best,
 Rodrigo

---

