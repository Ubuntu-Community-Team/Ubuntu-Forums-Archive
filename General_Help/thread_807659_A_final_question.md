---
title: "A final question"
date: 2008-05-26
forum: General Help
---

### Post by janpla on 2008-05-26
This is probably inappropriate for this forum, and almost certainly futile, but I'm nothing if not boneheaded.

I installed Ubuntu 7.10 a while ago, and while I was initially quite pleased, I am slowly growing less so, and I can foresee the day when I will simply wipe it and install something else. But before I leave I am curious about sometinhg: Why is it that the good people who develop Ubuntu have taken a perfectly good operating system like Linux and started mangling it like this?

I don't remember all my gripes at the moment, but let's just take the latest:

/etc/inittab

- which apparently has been replaced by something else. I mean, why? I can tolerate changes that make sense, and it just doesn't. The reason this one in particular is irritating is that I, as UNIX system manager, have several UNIX architectures to look after - AIX, Solaris, HP-UX, SuSE, Redhat, UNIX System Services on MVS, and everything that makes my life more complicated is just not on. 

A fundamental system file as /etc/inittab should not be replaced in this way - that is the Microsoft way doing things, to be completely oblivious to the world around and change things "just because". And it's a shame, because I really liked many of the ideas in Ubuntu; but if you guy change such a fundamental configuration, what else will change silently, suddenly rendering my UNIX experience useless?

Is there at least a way to make Ubuntu comply with the established practise of other UNIXes - something I can install or uninstall?

---

### Post by jimmy the saint on 2008-05-26
If you would like to install/uninstall somethihg I would recommend Ubuntu.  If it is not working for you, move on.  If you don't have the option then recommend it to whoever does.  
good luck

---

### Post by rubicon on 2008-05-26
You see, I'm agree with you on one hand &#8212; good old reliable inittab.
But on the other I say &#8212; it **is old**. SysV init system has been replaced by upstart, as well as all sysvinit ideology. Upstart lets you load daemons asynchronously, thus shorting boot time, and inittab just wasn't considered as an appropriate solution for configuring this new system. It is a progress, after all.

---

### Post by janpla on 2008-05-28
It's all very well, replacing things in the system and calling it progress, but there is such a thing as making it optional. I suppose I could go and rip it out and use the old inittab, but then I might as well just reinstall the entire thing, I suppose. 

One of the huge advantages of UNIX from my perspective is that once you know how it works behind the scenes on one version, you know it for all of them, more or less. I fail to see that the advantage of starting up a little faster is all that big - if all goes smoothly, yes, it works faster, but you create a vastly more complex situation when things run in parallel, and it will bite you when you have problems with the boot process.

It has always been sensible program design to optimise the parts of the code that run most often - initialisation is normally only run once, and it is more important to get it right than to do it quickly.

---

### Post by ShinHadoken on 2008-05-28
I agree with rubicon, upstart makes things a lot faster than using /etc/inittab, and in my opinion, a lot easier. But, if you're having that big of a problem, downgrade to Edgy or get rid Ubuntu altogether.

Hope this helps,

SH

---

### Post by pointone on 2008-05-28
Wow... at least do a bit of research before throwing a hissy fit. :P

You can easily create your own /etc/inittab and upstart will still read it. One of the key features of upstart is backwards compatibility with the old style.

[upstart]("http://upstart.ubuntu.com/") (please do look around to see what the fuss is about) is a GREAT step forward and other distributions (Fedora, Debian) are starting to use it as well. Please don't hold back our progress because you can't be arsed to Google search.

---

### Post by janpla on 2008-05-28
Hissy fits? I don't think so - I just went over my previous postings, and as far as I can see I state my concerns in a moderate and reasonable way; it certainly wasn't my intention to step on any toes.

One of the very good things about Linux is that it is possible to have this discussion at all; that even the initialisation process isn't a big unknown like in Windows, and that we have many options at every turn of the road. What I can't understand, though, is that people can't see that I am always right :-)

---

### Post by Zorael on 2008-05-28
> **janpla said:**
> What I can't understand, though, is that people can't see that I am always right :-)
Hear hear! One of my main gripes with humanity. When will they ever learn! :>

That said; "just because something works doesn't mean it can't be improved."

---

