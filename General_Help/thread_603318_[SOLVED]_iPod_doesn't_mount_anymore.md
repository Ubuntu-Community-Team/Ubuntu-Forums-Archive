---
title: "[SOLVED] iPod doesn't mount anymore"
date: 2007-11-05
forum: General Help
---

### Post by galvao on 2007-11-05
Greetings.

I plugged my iPod in (iPod Video, 30GB) on Gutsy and it just doesn't automount. Worked fine with Feisty but now I just can't make this work. 

When i run gtkpod and try to "Load iPod(s)" I receive the message "Could not find directory structure at '/media/IPOD' (...) Do you want to create the directory structure now?". If I say "Yes" I then receive the following:

Error initialising iPod: Problem creating iPod directory or file: '/media/IPOD/iPod_Control'.

I've tried what is described in [this post]("http://ubuntuforums.org/showthread.php?p=3573951"), but didn't worked. Problem is my iPod says "Do not disconnect" and now I don't know what to do. I'm also afraid it's screen will become marked, since it remains turned on on this message...

Please someone help me!

TIA,

---

### Post by galvao on 2007-11-05
Ok, this is one of those "Look how weird it was" fixes: After waiting with no reply I decided that between having a giant prohibited sign marking my iPod's screen and taking my chances I'd be better with the later.


So I boldly disconnected the damn thing to find out it was frozen (I didn't remembered that the prohibited sign usually blinks). So I reseted my iPod and connected it again and *poof!* everything worked like a charm.

Sorry about my lame attempts to be funny, but i was really stressed about this and jokes aside it was exactly what I did.

---

### Post by tombean on 2007-11-05
Hi there,

I got a Video and a Shuffle. It somehow recognized the Shuffle one automatically but I had the same problem like you with my IPod Video 30GB. 

So I tried a different program; Amarok, which surprisingly was able to mount it without a problem.
After that you're free to remove Amarok and install any other program of your choice.
I use Banshee.

I also used Automatix to install some extra codecs, due to .m4a playback issue.

It's kinda weird, but I hope this will help you.

Regards

---

