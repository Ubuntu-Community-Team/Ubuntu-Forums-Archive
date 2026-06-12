---
title: "No sound on my computer"
date: 2019-01-12
forum: General Help
---

### Post by sylvain.gut on 2019-01-12
Hy everyone, I just installed Ubuntu on my computer (deleting W10) and this one is now silenced... ^^

I searched on many forums and subjects but everything I already tried didn't work at all...

The speakers and jack port aren't working and here are the error messages I get:

sylvain@sylvain-EZbook:~$ pulseaudio
W: [pulseaudio] pid.c: Stale PID file, overwriting.
Killed

sylvain@sylvain-EZbook:~$ pulseaudio --start
E: [pulseaudio] main.c: Daemon startup failed.

on alsamixer, I have nothing by default and when I go to the second sound card, I can't increase sound on the headphone and speaker, this one is blocked at the value of 0.

If anyone have an idea, thank you very much! :-)

---

### Post by Frogs Hair on 2019-01-12
Hello

Post the the output of the following command in code tags  which will identify the sound card/device this aid those trying to help.
```
/sbin/lsmod | grep snd
```

Code Tags:

Copy and paste the text from the terminal in the reply window, highlight, and select the # symbol.

---

