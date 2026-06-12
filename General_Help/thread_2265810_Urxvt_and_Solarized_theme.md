---
title: "Urxvt and Solarized theme"
date: 2015-02-18
forum: General Help
---

### Post by adam37 on 2015-02-18
Apologies if I've posted this query in the wrong thread. 

I made the switch to linux (Ubuntu 12.04) about a year ago---it seemed very natural to me once I began to use latex for word processing. I really like it, but I've only recently started experimenting with further customization, different desktop environments, and the like. This is my first post on the forum, since I've often been able to find answers to my questions here by just googling around in the right way. But lately I've been having trouble accomplishing something, and many hours spent following up different suggestions that are out there hasn't yielded much of a result. 

I use Urxvt as my default terminal, and more and more find myself working directly from the terminal---this is especially true since I've recently started using i3 as my primary DE. I would like to learn how to "solarize" my Urxvt (I get the impression that solarized is a bit "old news" for some linux veterans, and I'm not particularly wedded to it, but I would just like to do this for the sake of learning how). I've added what I take to be the right files to my .Xdefaults, but the problem I'm having is that when I start a terminal there are no colors: the result of an ls -a command, for instance, does not employ different colors to discriminate between different file/folder types. (Otherwise things look good---terminal backgrounds are in solarized dark blue, etc.). I think this probably has something to do with my not fully understanding how to make the required changes to my .bashrc  and .dircolors folders, but I also think I've probably made some mistakes here already after trying out various "fixes" I've read on the net. 

Is there anyone out there who might be able to walk me through getting solarized up and running on Urxvt? I'd be happy to post any configuration files that might be helpful. I think one of the coolest things about linux is the existence of forums like this, and so thanks in advance to anyone who might have the time to give me a bit of help.

---

### Post by tgalati4 on 2015-02-18
One does not normally encounter "Natural" and "LaTex" in the same sentence.  

Because *urxt* is based on an old code base, it may not work as expected in a newer display environment.  It's possible that transparency is conflicting with your color selections:  [http://en.wikipedia.org/wiki/Pseudo-transparency](http://en.wikipedia.org/wiki/Pseudo-transparency)

What desktop environment are you using?  I would explore all of the terminal emulators available.  There are a few:

```
apt-cache search terminal emulator
```

Getting solarized colors to work correctly seems to be a challenge in terminals in general:  [https://bbs.archlinux.org/viewtopic.php?id=164108](https://bbs.archlinux.org/viewtopic.php?id=164108)

Welcome to the forums.

Great, now I want to set up solarized colors on my terminals!  [http://www.webupd8.org/2011/04/solarized-must-have-color-paletter-for.html](http://www.webupd8.org/2011/04/solarized-must-have-color-paletter-for.html)

---

### Post by adam37 on 2015-02-18
Thanks very much for your reply. After searching around a bit, it looks like xfce might be a better terminal option. The reason I initially chose urxt is because it doesn't have a "top menu" bar (with "file", "options" and the like), which I find takes up a lot of space when several terminals are running in a single window (I use i3wm for the most part as my DE). 

I'll check out xfce and see if configuring it is any easier. Thanks again.

---

