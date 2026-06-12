---
title: "I would like to move home"
date: 2007-05-26
forum: General Help
---

### Post by the lemming on 2007-05-26
How do you have the Linux operating system on the master drive (which dual boots with XP) and have the home drive on the slave drive?

I'm hoping to have a similar set up to my XP system where I keep all my data on the slave drive.  This way if I decide to install anything and then bugger it up, which happens all the time, I can re-install the XP operating system without losing my files.  I'm hoping to do the same with Linux.  

Ultimately I'm hoping to be able to swat distros, as the mood takes me, and install which ever takes my fancy without losing my data.

Is it possible?

Cheers

---

### Post by smoker on 2007-05-26
this is a link full of info that should help you move your home partition
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

i know you can share your swap partition with other distros, but not sure if i would do this with a home partition, though i think it may be possible.

---

### Post by scooper on 2007-05-27
Something to think about, perhaps...

I found that it's best to not share the entire home directory between different different system installations.  The home directory has a mix of your data and information cached by applications that may or may not be useful, or even usable, to a different version or instance of that application.  Basically, you'll get a lot more junk shared than you may want.  It shouldn't lead to a lot of instability, like Windows, but could have unexpected consequences to certain applications.

What I'm trying is to create a directory where selected shared things are kept, e.g. for me /users/steve, and make symlinks back to a separate home directory for each system installation.  So if I like my fluxbox settings to be used on every installed distribution I'd have a /users/steve/_fluxbox directory that get symlinked to /home/steve/.fluxbox.

It's more work, but you start learning what stuff is useful and what isn't, and you may avoid an occasional problem.  Just a thought.

---

