---
title: "mplayer jumps forward and backward while playing videos"
date: 2007-11-17
forum: General Help
---

### Post by scorpio2002 on 2007-11-17
Hi there! I've been noticing mplayer has a strange behavior: while it's playing a file(no matters the format) it randomly jumps for and back through the video and there's nothing I can do about it. I even tried disabling compiz but that doesn't seem to solve the situation.

is anybody experiencing similar issues with mplayer? Is there a solution?

thx,
Donato (alias Scorpio2002)

---

### Post by edu barros on 2008-02-25
same problem here.
anyone?

---

### Post by pointone on 2008-02-25
Your mouse's scroll wheel will seek forward/backward. I experienced this problem and it turned out to be my palms resting on my laptop's touchpad "scroll bar".

---

### Post by edu barros on 2008-02-25
> **pointone said:**
> Your mouse's scroll wheel will seek forward/backward. I experienced this problem and it turned out to be my palms resting on my laptop's touchpad "scroll bar".
tried that before, no luck.
i even unplugged my usb mouse and disabled my touchpad, but it still randomly jumps forward/backward. :(

---

### Post by pointone on 2008-02-26
Is it just MPlayer? Try Totem or another player and see if it still occurs.

---

### Post by edu barros on 2008-02-26
> **pointone said:**
> Is it just MPlayer? Try Totem or another player and see if it still occurs.
totem and vlc play fine. smplayer jumps fw/bw.
seems like it's mplayer related only.

---

### Post by rvm4000 on 2008-02-26
You could try with a newer version of mplayer, like this one:

[mplayer_1.0rc2svn26030_i386.deb](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn26030_i386.deb)

---

### Post by edu barros on 2008-02-26
> **rvm4000 said:**
> You could try with a newer version of mplayer, like this one:

[mplayer_1.0rc2svn26030_i386.deb](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn26030_i386.deb)
apparently that solved the problem, but i just made a quick test. i'll give it another try later and post the results here. but thanks in advance! :)

---

### Post by Crafty Kisses on 2008-02-26
> **pointone said:**
> Your mouse's scroll wheel will seek forward/backward. I experienced this problem and it turned out to be my palms resting on my laptop's touchpad "scroll bar".

Yep, the first few months I used Ubuntu I was a bit confused too. :lolflag:

---

### Post by edu barros on 2008-02-28
> **edu barros said:**
> apparently that solved the problem, but i just made a quick test. i'll give it another try later and post the results here. but thanks in advance! :)

problem solved!
after a series of tests, it did not jump at all.

the only problem was the famous "could not open file..." error. that's when i realized why i had such an old version of mplayer. but fortunately i found an easy solution. just open **/usr/share/applications/mplayer.desktop** and change“Exec=gmplayer %U” to “Exec=gmplayer %F”.

thanks!!!

ps: sorry for my bad english, i'm brazillian. :)

---

