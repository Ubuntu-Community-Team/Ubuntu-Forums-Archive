---
title: "Inconsistent sound issue"
date: 2007-11-08
forum: General Help
---

### Post by Niniel on 2007-11-08
Hello,

this is my last attempt to try and  understand what's going on, my next move will be to nuke my installation and start from scratch; I am a bit afraid though that it'll happen again so I'd prefer to figure out what's going on first.

Anyway, when I boot to Ubuntu on my HP Pavilion z5000 notebook (originally installed 7.10 B5, now after various rounds of updates it claims to be just 7.10), the sound may or may not work. Sometimes I can tell it won't work because the statup sound is cut short, sometimes that plays in all its glory and then I still can't play CDs or MP3s or get sound in games, and sometimes it just works. It seems to be totally random.

What might be going on here? 
Other than a ghost in the machine. :)

---

### Post by Niniel on 2007-11-10
Looks like this is destined to remain a mystery.
Oh well, I guess there isn't a solution to every problem.

---

### Post by Niniel on 2007-11-11
I installed GNOME alsa mixer, and when that starts, it gives me some errors:

> Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/Silicon_Laboratory_Si3036,8_rev_7": `,' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_names/Silicon_Laboratory_Si3036,8_rev_7": `,' is an invalid character in key/directory names

Maybe that's what's causing my problem... but, I can't find that directory. Where could that be hiding?

---

### Post by jocko on 2007-11-11
> **Niniel said:**
> I installed GNOME alsa mixer, and when that starts, it gives me some errors:



Maybe that's what's causing my problem... but, I can't find that directory. Where could that be hiding?

My guess is that it is a gconf-setting and not a real directory.
Start gconf-editor (by typing gconf-editor in a terminal) and see if you can find it there.
I don't think that's the real problem though, as that error looks like it's specific for gnome-alsamixer.
Try using the actual alsa-mixer instead (type alsa-mixer in a terminal).

---

### Post by Niniel on 2007-11-11
Hm, no error messages when I start that.

---

