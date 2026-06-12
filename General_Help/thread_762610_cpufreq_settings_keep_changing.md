---
title: "cpufreq settings keep changing"
date: 2008-04-22
forum: General Help
---

### Post by oloapota on 2008-04-22
2nd EDIT: I solved the problem, if you need to know how I did it, go to the last post



EDIT: I managed to solve the first part of my question, just need help with the second part (see below)

Hello everybody
I hope this is the right section
I need some help with cpufreq: I installed it on my laptop (P IV, 2,6Ghz) to turn the heat and noise down.
Thing is, the values keep changing all the time.
I edited scaling_min_freq and set it to 333000 (333Mhz)
scaling_max_freq is 2666600  (2,6Ghz)
and then i set the governor to "ondemand"

These settings lasted about 15 seconds, then it automatically goes to "performance" and scaling_min_freq=scaling_max_freq=2666600, sometimes switching to min=max=2,0Ghz  :confused:
Why does it keep changing all the time?

This is my cpufreq-info

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Per favore, comunicare errori e malfunzionamenti a [email]linux@brodo.de[/email].
analisi della CPU 0:
  modulo p4-clockmod
  CPU per le quali e` necessario cambiare la frequenza contemporaneamente: 0
  limiti hardware: 333 MHz - 2.67 GHz
  frequenze disponibili: 333 MHz, 667 MHz, 1000 MHz, 1.33 GHz, 1.67 GHz, 2.00 GHz, 2.33 GHz, 2.67 GHz
  gestori disponibili: ondemand, powersave, conservative, userspace, performance
  gestore corrente: [COLOR="Red"]la frequenza deve mantenersi tra 2.67 GHz e 2.67 GHz[/COLOR].
                   Il gestore [COLOR="Red"]"performance"[/COLOR] puo` decidere quale velocita` usare
                  in questo intervallo.
  la frequenza attuale della CPU e` 2.67 GHz.

It's in italian but as you can see minimum frequence=max frequence=2,67Ghz

I want it to remain to "ondemand" and 333Mhz to 2,6Ghz!
And once I can with your help get it to remain set to these values, I'd like to know how I can make sure that it doesn't change AT BOOTUP
Thank you

---

### Post by someonestolemyname on 2008-04-22
Isn't 333 a bit too low? I'm just guessing, as my 2.0gHz Core2 Duo only goes down to 800mHz.

Maybe try a different limit; it might be changing it back to a safe default when you try.

---

### Post by oloapota on 2008-04-22
Didn't think about that!
I guess I just wanted it to consume as little as possible when idle
I'll try and set it to 999Mhz and see what happens, then I'll report back here
Thanks someonestole[your]name!

---

### Post by oloapota on 2008-04-22
No, didnt'work:(
As usual, the settings I made lasted about 20 seconds, then it went back to "performance" and minfreq=maxfreq=2,6Ghz , sometimes switching to minfreq=maxfreq=2,0Ghz (most puzzling :confused:)
I read on the internet about other people using cpufreq on a P4, so I guess it should work....
any ideas? :)

---

### Post by oloapota on 2008-04-22
I managed to resolve the [COLOR="Red"]**first part**[/COLOR] of my question!
I had to edit /etc/cpufreq.conf and delete all the # (comment) markings before the lines about the ondemand governor, the one I'm interested in.

But I still need help about [COLOR="Red"]**the second part of my question**[/COLOR], that is, how to get cpuconf to save the settings I made so that when I reboot my laptop, they're all there.
In particular, when I turn on the pc, it still is on "ondemand" governor (good), but the minimum frequency is changed to 2,6Ghz, the same as the maximum frequency, so it just stays there!
I want to set the minimum frequency to 999Mhz, and I want it to save this setting so that it is still there when I boot xubuntu
Can anybody help please?

---

### Post by oloapota on 2008-04-22
Looks like it's finally doing what I want it to do!

1)I edited rc.local and added these lines

cpufreq-set -g ondemand
cpufreq-set -d 999000


2) I also commented the lines in cpufreqd.conf that made it switch to "performance" when connected to AC!

I don't know whether this is the "right" way to do it, but it works now.
This program is great, even though a bit hard to set
Hope this helps others who might have the same problem in the future
ubuntu rocks:guitar:
:lolflag:

---

