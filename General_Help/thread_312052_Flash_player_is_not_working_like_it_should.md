---
title: "Flash player is not working like it should"
date: 2006-12-03
forum: General Help
---

### Post by PrinceArithon on 2006-12-03
Ok, so I've tried 3 different browsers and no matter what I can't get places like google video and youtube to work.

I installed the Flash 9 a while ago and it was working fine.  The thing is this.

I will click on a video to watch, and it will play for a few seconds and then just stop.  Do I need to uninstall and reinstall my flash player??  Like there was a command something like sudo apt-get uninstall flash 9 or something like that??

Anyway if anyone has any idea what is going on let me know

---

### Post by xopher on 2006-12-03
How did you install it? Are you sure you do not have flash 7 still installed? Are you on 32-bit or 64-bit?

We need more information to be able to help you, better ;)

---

### Post by PrinceArithon on 2006-12-03
Yup I know for sure it's Flash 9 running.  I installed it like this

wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)
tar xvzf FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 


I am running on a 32 bit system

---

### Post by PrinceArithon on 2006-12-03
It's weird, I turned Amarok off completely instead of just pausing it, and it works now...

I wonder why that happened??  LOL

---

### Post by Old Jimma on 2006-12-04
I"ve had a similar problem... After enabling mp3 support for amarok, flash stopped working!

Phil Smith
Duluth, GA

---

### Post by scuzzo84 on 2006-12-13
im having the same issue

---

### Post by dunnerz on 2006-12-20
Same problem here!
(kubuntu edgy, firefox 2, flash player 9)

---

### Post by ozp on 2007-01-05
for the the fullscreen is not working neither on youtube or google

---

### Post by hikaricore on 2007-01-05
> **ozp said:**
> for the the fullscreen is not working neither on youtube or google

You actually want to watch compressed flash videos fullscreen  >.<  They look bad enough when they're in a small box.

---

### Post by cgm12mgc on 2007-09-20
this is exactley what is happening to me.. what exactley is amarok and how do i turn it off

---

### Post by siman on 2007-10-15
Same problem here, I got flash9 and also installed it with the wget method.

Sometimes flash-videos work flawlessly, but most of the time the stop after 5-10sec. If I then move the "position-marker" of the video manually it works again for a couple of seconds and stops again.

I haven't used amarok in ages, but it can play mp3s.

edit: found this thread, same problem not solution [http://ubuntuforums.org/showthread.php?t=517072](http://ubuntuforums.org/showthread.php?t=517072)

edit2: and now I noticed that I don't have this problem on my work computer. If someone tells me what to do, I could try reproduce the problem on the work-comp or look for diff in the configurations.

---

