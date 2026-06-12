---
title: "iTunes iPod Sync In Amarok."
date: 2007-03-12
forum: General Help
---

### Post by esaym on 2007-03-12
Ok I have a problem but I don't know if it is a problem with itunes or amarok.  Basically I synced my ipod with an itunes library on my girlfriend's computer.  That went fine.

However when I plugged the ipod into my linux computer and transfered some classical music onto it using amarok it left the ipod unable to play some of the protected files that it got from the itunes library.  The prtected files were still on it but it would not play them.  It is like the ipod detected that it was not syncing to an itunes library so it deleted it's encryption keys or something.  Is this just the "nature of the beast" or did amarok screw something up?

---

### Post by briguy on 2007-03-12
Sometimes mixing between different iPod managers can cause headaches.  I find that iTunes is the worst for this - avoid it if you can!

Anyways, sometimes you can "fix" your iPod under Amarok.  When connected, try the "Stale and Orphaned" button.

I'm not sure about the protected file thing - you may be right but I've never heard of that before.  You might try pulling the protected files off through Amarok as well... could make it worse though!

You may also try gtkpod - there are two versions in the repos, install the gtkpod-aac package.  Gtkpod has a "check ipod's files" selection which may help.

Not really sure what the issue is, these are some possible solutions.  Good luck, and post back the results in case anyone else has the same problems!

---

