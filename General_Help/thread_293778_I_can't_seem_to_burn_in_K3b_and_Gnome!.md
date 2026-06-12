---
title: "I can't seem to burn in K3b and Gnome!"
date: 2006-11-05
forum: General Help
---

### Post by dreamer_cast on 2006-11-05
Hey guys, I really want to be able to use K3b, but it just will not work for me.  I'm running root so I know it's not a permissions thing, the drive I'm trying to use is a external USB burner, LG 16X DL type.  I'm running Edgy.  When trying to burn an audio cd for example, I always get "input/ouput error, not necessarily serious", and then it ejects the disc and yet another coaster.  Can someone please help me out with this, every other program I try either gives me errors or takes forever to convert audio files to burn to disc, which is another topic all together!  Thanks,

Dreamer

---

### Post by dreamer_cast on 2006-11-06
Anyone?

Dreamer

---

### Post by dreamer_cast on 2006-11-07
Can no-one shed some light on this?  I'm using Brasero right now, it's the only one that actually is working for me right now, pretty brutal if you ask me, but I guess it's better than nothing..

Dreamer

---

### Post by galego on 2006-11-07
have you ensured that you have all of the codecs? if you have automatix go to multimedia and select every codec you find.

---

### Post by tronica on 2006-11-07
in order to burn mp3's, you need libk3b2-mp3.

> sudo apt-get install libk3b2-mp3

---

### Post by dannyboy79 on 2006-11-07
> **dreamer_cast said:**
> Can no-one shed some light on this?  I'm using Brasero right now, it's the only one that actually is working for me right now, pretty brutal if you ask me, but I guess it's better than nothing..

Dreamer

i have a hell of time burning as well, i have tried different media and that has solved it sometimes. so you say brasero works hey? i should give that try cause all gnomebaker, nerolinux, k3b, and plain ol isogrowfs or whatever command line using dvd+rw tools just don't work, I always get the i/o error?????

i am using dapper though. i have a i/o magic DVD16DL, i think that's the model number.

---

### Post by dreamer_cast on 2006-11-07
Thanks, I'll see if it installs that library with K3b....Brasero works for me with audio, haven't tried using it with image burning yet...also, I'm using Edgy, so automatix won't work, I uninstalled it already...

Dreamer

---

### Post by dreamer_cast on 2006-11-07
I checked to see if that library is installed and it is installed, so it's not that...any other ideas people?  Thanks in advance,

Dreamer

---

### Post by mzilhao on 2007-01-31
sorry for the late reply. i have a similar problem with my LG burner (on a SATA drive). 
i just use brasero for burning becuase, apart from nautilus, it's the only app that works for me. 
there are similar threads [here]("http://ubuntuforums.org/showthread.php?t=217472") and [here]("http://ubuntuforums.org/showthread.php?t=233125")

---

### Post by laidback on 2007-02-01
I use K3b from Gnome. But I have Kubuntu-desktop installed as well (via synaptic). I chose gnome as my default desktop. I've burnt many Cds, music, data and ISOs. Only the odd DVD but that's out of choice rather than because it doesn't work. I loaded Kubuntu specifically because I wanted K3b.

My main DVD burner is attached to the IDE cable as normal. I also have a USB DVD burner, this works too. The only thing that's failed so far has been an attempt at a clone copy using both DVD drives, one as donner the other as burner. It appeared to work, K3b reported success, but the CD was useless and wouldn't play. I retried with another CD, same result, so gave up. Otherwise I'm completely satisfied. Perhaps installing the Kubuntu desktop is the secret.

---

