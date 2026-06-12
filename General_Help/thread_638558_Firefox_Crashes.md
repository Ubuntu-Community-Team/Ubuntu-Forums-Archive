---
title: "Firefox Crashes"
date: 2007-12-12
forum: General Help
---

### Post by Trunk_z on 2007-12-12
Hey there,

I've been having a few problems with my Firefox ever since I upgradte to Fiesty, when it came out.
Just been living with it up until now, but I cant solve it.

When I type a URL in the address box, sometimes firefox will crash (it seems to happen when i type quickly, but I'm not sure), other times it will crash when I type into the search box. And a couple of times it will crash when I type in a text box on a website (It did so typing in the title of the post).

Has anyone had something similar, or knows how I can resolve this problem?
Would be great if anyone could help,

Regards,
Chris

---

### Post by Dr.Suse on 2007-12-12
> **Trunk_z said:**
> Hey there,

I've been having a few problems with my Firefox ever since I upgradte to Fiesty, when it came out.
Just been living with it up until now, but I cant solve it.

When I type a URL in the address box, sometimes firefox will crash (it seems to happen when i type quickly, but I'm not sure), other times it will crash when I type into the search box. And a couple of times it will crash when I type in a text box on a website (It did so typing in the title of the post).

Has anyone had something similar, or knows how I can resolve this problem?
Would be great if anyone could help,

Regards,
Chris
this is happening to me all the time too. sometimes randomly and sometimes when i load certian pages.

---

### Post by simonj21 on 2007-12-20
it's also the problem as described here:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/158958](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/158958)
[http://www.thescripts.com/forum/thread618077.html](http://www.thescripts.com/forum/thread618077.html)

It basically happens whenever I type a space in a textbox when running my Ubuntu. Also, if I type something in that doesn't include a space, it will crash when I submit the form relating to that text box. I've tried reinstalling and it's still the same problem. It's firefox 2.0.0.11 and it's Ubuntu-Fiesty. I also haven't installed any add ons or extensions to firefox. There's also nothing in the crash folder (it's just empty). Basically firefox just closes when it encounters this problem... It's ubuntu 7.10 and it says Gutsy, but in firefox it says Fiesty. As you can tell I'm a n00b :)

---

### Post by tgalati4 on 2007-12-20
Does it crash consistently if you use Tools-->Clear Private Data?

This clears the cache.  Perhaps there is a bad cache file that is tripping up Firefox.

I'm running 2.0.0.6 on Linux Mint 4 XFCE (based on Gutsy).  Perhaps its a Gnome issue with Firefox.

You can run firefox with debug mode on:

In a terminal:

>firefox --debug

---

### Post by satx on 2007-12-20
Delete FireFox, then re-install:)

---

### Post by simonj21 on 2007-12-20
Hey,

I also posted again in [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/158958](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/158958) and got a response to turn off spell checker. I did this and it worked. Thanks for your replies though, I can't believe how good support is for Ubuntu!

Simon

---

### Post by Trunk_z on 2007-12-21
Thanks for all the replies.

I did try reinstalling it, deleting the cache and everything.But it didnt work. Well... deleting the temp files fixes it until there are more temp files

I'll try disabling the spellchecker when boot ubuntu and let you guys know how it went.

Chris

---

