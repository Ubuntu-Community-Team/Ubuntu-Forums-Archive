---
title: "Festival and Pidgen did I set it up right? i hear no sound."
date: 2008-05-31
forum: General Help
---

### Post by spacesearcher on 2008-05-31
Ok so I installed festival and the festvox-rablpc16k I then had problems because I got this error "Linux: can't open /dev/dsp festival"
I fixed this by using the command:
```
printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > .festivalrc
```
I got that from here [http://ubuntuforums.org/showthread.php?t=171182&page=2](http://ubuntuforums.org/showthread.php?t=171182&page=2)
changed it to use alsa

so now I can make the computer talk when I use
festival
festival>  (SayText " blah blah blah")   

now I install the pidgin-festival plugin via synaptic
I open pidgin (was all the way closed before)
go to plugins menu
check the festival plug in box

no sound comes out when I get a message.
I have tried closing it all the way and opening it back up and it still doesn't work.

Does any one have a solution?

---

### Post by bluej100 on 2008-07-03
I think this thread might have the fix: [http://ph.ubuntuforums.com/showthread.php?t=678512](http://ph.ubuntuforums.com/showthread.php?t=678512) .

---

### Post by jiapei100 on 2008-09-24
Exactly the same problem here. Do we need to try pidgin-festival-2.3 instead of pidgin-festival-2.2?

Regards
JIA

---

