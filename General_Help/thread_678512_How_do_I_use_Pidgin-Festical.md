---
title: "How do I use Pidgin-Festical?"
date: 2008-01-25
forum: General Help
---

### Post by sulusulu on 2008-01-25
How do I use the Pidgin-Festival plugin?  I have it installed it in Pidin and I installed Festival but I still get no voice.  I don't need an actual screen reader I just what Pidgin to read my IMs to me.  My sound card does work.  Any ideas?

---

### Post by Teddy_P on 2008-02-15
Any luck?
I am looking for the same thing.

Teddy

---

### Post by sulusulu on 2008-02-16
> **Teddy_P said:**
> Any luck?
I am looking for the same thing.

Teddy
Nope. :(

---

### Post by kevdog on 2008-02-17
Where is a link to this plugin?

---

### Post by sulusulu on 2008-02-17
> **kevdog said:**
> Where is a link to this plugin?
It's in the repos under "Pidgin-festival".  Also [here]("http://freshmeat.net/projects/pidgin-festival/").

---

### Post by chriswyatt on 2008-06-04
I've also got this problem, no one found a fix for it then?  P.S. I've tested out Festival, and it works by itself.

---

### Post by spacesearcher on 2008-06-24
Same problem here! >.<
I wonder if it has something to do with alsa or pulse audio.

---

### Post by 5m0k3 on 2008-06-28
Tools > Preferences > Sounds.  I had to change the method and it started working

---

### Post by spacesearcher on 2008-07-03
Can you explain exactly what settings you had?
I still cant use it i posted my problem about 4 weeks ago here:
[http://ubuntuforums.org/showthread.php?t=813740](http://ubuntuforums.org/showthread.php?t=813740)

I can only hear the beep on automatic and alsa but i cant hear festival on any of the sound settings in pidgin...

to get festival to work in terminal i had to use this code:
```
printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > .festivalrc
```
that i got from this thread [http://ubuntuforums.org/showthread.php?t=171182&page=2](http://ubuntuforums.org/showthread.php?t=171182&page=2)

---

