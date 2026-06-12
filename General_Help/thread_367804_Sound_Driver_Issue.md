---
title: "Sound Driver Issue?"
date: 2007-02-22
forum: General Help
---

### Post by Zadok001 on 2007-02-22
So here's the situation.  Some of my programs work brilliantly.  Others, well, don't.  My hardware is plenty sufficient to support what I'm doing, with framerates upwards of 150 in most of the apps I'm trying to make work.  But when I run them, both sound and image "stutter" every 1-2 seconds, basically, jerky.  Between stutters, they work perfectly.

Now here's the twist.  Some of the programs that don't work allow me to disable sound - And when I do *THAT*, they work brilliantly, the stuttering vanishes.  My sound is an on-board element, from an Intel D925XCV.

I have two guesses:

1. This is a driver issue, and I just need new drivers.  There are quote-unquote 'Linux' drivers on Intel's site, so I'm prepared to go that route, but I can't be sure this is actually the problem.

2. This has something to do with the way Linux handles sound.  This makes more sense to me, since sound in a lot of applications are fine - Movies play beautifully, etc.  I've heard that Linux has a couple different sound mixers, but being relatively new to Linux, everything I find on the subject rapidly turns to Greek - Something about Alsa?  Is it possible that some apps (say, Planet Penguin Racer, which works fine) use one mixer, and other apps (say, Neverball) use a different one, and this could be causing my problem?

#2 seems more likely, but I don't really know how to walk that path...  Any help would be appreciated.

---

### Post by Daveth on 2007-02-22
well, your codec chip is a Realtek ALC880, for starters.
Might be useful for others if you try the "general help" section tests in

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

and see what answers pop out. I note other folk have had problems with this on-board chip, so you can search for it in the Forum, now it has a name. Hope this gets more knowlegible folk on your side to sort this.

---

### Post by Zadok001 on 2007-02-22
Ah, thank God, another term to search for.  Thank you!  I've got a good sized stack of info, I'll post a fix if I can pull it off.

---

