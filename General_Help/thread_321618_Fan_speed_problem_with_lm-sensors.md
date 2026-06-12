---
title: "Fan speed problem with lm-sensors"
date: 2006-12-19
forum: General Help
---

### Post by jonboy99 on 2006-12-19
Hi folks
Have just installed lm-sensors, and using gkrellm to monitor.  All working well apart from the fan speed dividers - all 3 fans are reading double the actual speed (as reported by the bios and my ears), and I can't figure out how to change them.

Have tweaked /etc/sensors.conf but it seems to make no difference - not sure if i'm changing the right bit 0  it's a huge file!

Have attached my sensors.conf - if you search for the string jb99 it'll take you to the bit i've changed.  The dividers were 4, 2, 2 initially and i changed them to 8, 4, 4, and the limits down to 1000 as my fans run at about 1500 rpm each (but are reading about 3k rpm in gkrellm).

Have tried rebooting and typing ```
sensors -s
``` after making the changes.

Motherboard is an asus a7n8x deluxe (nforce 2).

Cheers
Jon

[http://www.jonbrookes.dsl.pipex.com/filestore/sensors.conf]("http://www.jonbrookes.dsl.pipex.com/filestore/sensors.conf")

---

### Post by MeduZa on 2006-12-19
maybe you need to do something like this on your sensors.conf (fans area):

 ### Fan divisors
 set fanX_div 8 (try numbers here I have a a8n and uses Nforce2 driver too)

or

compute fanX @ / 1, @ / 2 ( I never try this before ^_^ )


fanX is the fan name ex: fan2

maybe this works :-k

---

### Post by jonboy99 on 2006-12-19
Cheers, about to try it then discovered that I can do all this from gkrellm with a nice GUI..:oops: 
Ta for help  :D

---

