---
title: "Terminal Emulation Problem"
date: 2006-11-20
forum: General Help
---

### Post by FyberOptic on 2006-11-20
Hiya folks, maybe somebody can help me out with a problem I've had for quite a while now.  Basically, I'm having some sort of terminal emulation issue with anything trying to display extended ansi-like graphics, such as with Links and Kismet.  The screen just ends up looking kind of screwy, making those applications nearly useless from a standard text console.

Something to note is that if I load those same applications while inside of Screen, they appear perfectly fine.  They're also fine if I use them when inside an xterm.  So that's what makes me think it's got to be some kind of terminal emulation problem, even though my TERM=linux as it should.

I can't remember exactly when I started to have this problem, but it started after a major release upgrade I did once (via apt), possibly to Breezy.  I thought something in my system could have just gotten mucked up during the upgrade, and didn't pay it much mind since I couldn't find any solutions online, until I finally decided to just reinstall fresh with Edgy.  Well, that's why I'm here, because this fresh install of Edgy is doing just the same.

I might should point out that I generally boot straight to the text console, and use the framebuffer mode 791, though I booted to standard 80x25 to test if that could be the problem, and I found it made no difference.  And if it matters, I'm running on a Thinkpad 600e.  I'd certainly appreciate any help or pointers anyone could offer!

---

