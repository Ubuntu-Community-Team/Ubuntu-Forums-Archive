---
title: "No sound on Zsnes"
date: 2008-05-09
forum: General Help
---

### Post by jarica on 2008-05-09
I have had a problem with Zsnes on Hardy and after looking for answers could not find an answer.

I have checked elsewhere and this worked for me:

To work around this problem, start zsnes with the following command:

zsnes -ad sdl

You only need to do that once. After that it will remember that going forward and just typing "zsnes" will do the trick.

If you have garbled or low quality sound after running that command, inside zsnes set the sound quality to 48000.

I hope this helps others as it did me.

All credit to the person on this [post ]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/188567/comments/9")

---

