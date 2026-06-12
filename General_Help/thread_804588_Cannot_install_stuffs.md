---
title: "Cannot install stuffs?"
date: 2008-05-23
forum: General Help
---

### Post by gewone on 2008-05-23
Hiya!

I ran Linux in the late 90's. Slackware was my choice of dist at that time. I was no expert, but I guess I had intermediate skills for a ~14yr kid. So, now I've heard lots of talk about UBUNTU, "the new thing" that rocks in every aspect. I was so curious that I had to download it and try it. So, since **I have not Internet connection** at home; I downloaded the ISO installer at work, and brought it home on my USB stick for burn/install.

So, everything went well with the install. The operative system itself looks smooth! Then I wanted to get off. First of all I found out I could not play MP3 files due to lack of codecs, neither could I playback Xvid, also 'cuz of missing codecs / directshow filter.

Well, next day at work I'll do some downloading. I remember from my time with Slackware/X-windows that I loved the XMMS player. So I found the .tar.gz for it. Brought it on my USB stick.

Finally, home, aaah..
I remembered the way to install an application with "defaults", so I went straight ahead:

*sudo ./configure*

So, it halted almost immediately, with the error "compiler cannot create executables", something like that.. Wtf, I thought to myself. Then I tried a bounce of other .tgz packages. The same error on each of them. I can't do a ./configure! Gah! ;-/

So, I Googled it today. Then I find that I probably miss the *'build-essential'* package, which is really needed for all kinds of builds. Erhm, didn't need that one with good old Slack 7, or at least it was included from default installation. So, I found a .deb thingie on this one, 'cuz I read that on Ubuntu/Debian you use the 'dpkg' cmd to quickly install Debian exclusive packages. Neat feature, hehe. Anyways, got home and tried it. It complains about no gtk, no glibc6, and lots of other libraries. Isn't any of these ones included in the 700MB installation CD?

Oh my god. How do I do this the simplest way without having an Internet connection? I just want to be able to bring .tgz packages, perhaps also those .deb packages, home, installing..

Is this going to become a problem?
Thanks for the help guys!

---

### Post by tacutu on 2008-05-23
aptoncd?

---

### Post by nick_h on 2008-05-23
This link might help - [Install Applications in Ubuntu without Internet](http://planetoss.com/detail.php?id=13).

---

