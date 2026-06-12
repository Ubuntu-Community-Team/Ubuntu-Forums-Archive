---
title: "bogofilter or spamassassin?"
date: 2007-04-17
forum: General Help
---

### Post by ubiwankanubi on 2007-04-17
i'm trying sylpheed-claws and want to use a spam filter. I've heard that spamassassin uses up lots of resources, so i tried the bogofilter plugin. i've been selecting the junk mail and clicking the spam button, hoping that the bogofilter will learn what spam is, but until now it hasn't filtered anything.

so, my question is, has anyone used bogofilter w sylpheed claws? and how did you get it to work? Or, should I use spamassassin and will the resource usage really slowdown my computer?

---

### Post by mexlinux on 2007-04-18
I have never used sylpheed-claws (I use kmail) but I have used spamassassin and bogofilter,
both in server and desktop.
Bogofilter is, in my opinion, a better alternative, but since it's full bayesian system: it has to learn first!
Best option is to collect a lot of some spam, and some good mail, and let it learn from both.
See this:
[http://bogofilter.sourceforge.net/bogofilter-faq.html#training](http://bogofilter.sourceforge.net/bogofilter-faq.html#training)

I can tell that two years ago, I had only spamassassin on the server, I was receiving around 100spam per day, and it was filtering around 40 of them.

Now that I have bogofilter, I receive around 150spam per day, around 140 are filtered by bogofilter in the server and for the 10 remaing i can tell that 9 are filtered by bogofilter in the desktop.

---

