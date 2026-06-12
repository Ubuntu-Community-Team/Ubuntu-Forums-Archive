---
title: "Gnome15 Keyboard LCD Degredation"
date: 2013-05-23
forum: General Help
---

### Post by Rikeshar on 2013-05-23
Hello everyone. I tried asking this originally on the Gnome15 project website, but their forums are pretty much useless since they're constantly bombarded by spambots.

I have a Logitech G510 keyboard, and am using the Gnome15 software to enable to the LCD screen on it for use with linux. It worked fine until about a week ago when suddenly the quality of the LCD screen has gotten really terrible, to the point where i can barely make out letters when it showing, for instance, what song is playing. 

I don't know if this was maybe caused by a linux update, or what. I really have no idea where to start, so if anyone has any ideas, I'm more than open to hear! Thank you.

---

### Post by dino99 on 2013-05-23
their package for ubuntu (10.10) is oldish (0.8.3), so maybe install an other (from fedora for example)
[http://www.gnome15.org/index.php?option=com_content&view=article&id=9&Itemid=33](http://www.gnome15.org/index.php?option=com_content&view=article&id=9&Itemid=33)

---

### Post by russo on 2013-06-04
> **Rikeshar said:**
> Hello everyone. I tried asking this originally on the Gnome15 project website, but their forums are pretty much useless since they're constantly bombarded by spambots.

I have a Logitech G510 keyboard, and am using the Gnome15 software to enable to the LCD screen on it for use with linux. It worked fine until about a week ago when suddenly the quality of the LCD screen has gotten really terrible, to the point where i can barely make out letters when it showing, for instance, what song is playing. 

I don't know if this was maybe caused by a linux update, or what. I really have no idea where to start, so if anyone has any ideas, I'm more than open to hear! Thank you.

Hi Rikeshar

If you used the "Somnus" nickname on the Gnome15 forums I posted a reply to your post.
Here it goes again:

I know there are issues with Gnome15 and Cairo >= 1.12.10 that may cause some fonts to look "skewed".
I already tried to take a look at the problem and partially found the cause for it, but still didn't found a solution.
I'm working on it tough.

By the way, after having no news for several months from the developer, I created an "unofficial" website for gnome15 and have packaged it for the newly released versions of the supported distributions (Fedora 18, Debian 7, Ubuntu 13.04, openSUSE 12.3...).
I also published a new unofficial version of Gnome15 (0.9.3) who fixes some issues that users have talked about in the forums.

You can take a look at it here [www.russo79.com/gnome15](www.russo79.com/gnome15)

It still doesn't fix the problem with the skewed fonts, but some other issues with Gnome15 were solved with this new version.

---

