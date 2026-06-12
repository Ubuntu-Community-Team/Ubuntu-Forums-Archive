---
title: "Need I be CONCERNED that I use Ubuntu?"
date: 2006-10-14
forum: General Help
---

### Post by emarkay on 2006-10-14
I have been using Ubuntu for a few weeks, and so far things are going slow, but they are progressing in my switch from Window$ (I have not even gotten to looking at the applications yet - I am still getting my basic desktop and Interent set up!)  Recently, I started a thread after a printer install:
[http://www.ubuntuforums.org/showthread.php?p=1616379&posted=1#post1616379](http://www.ubuntuforums.org/showthread.php?p=1616379&posted=1#post1616379)
and found some disconcerting replies:

"It's most likley not needed but it is most likely a dependency."
"Ubuntu's philosophy kind of reminds me of Apple's. We know what is best for you, so just shut up and use whatever the Ubuntu devs think is the best."

I said there. that I thought all Linux versions played nice with the user and didn't automagically do things that weren't essential, that you could trust the developers to play nice and not install unwanted things (yea, why DOES a printer install need a mail server?)
Do I have to start going back into my paranoid mode where I delete all traces of everything after use, scrub the registry weekly, have 3 anti-malware programs, don't use most multimedia extensions live on the Internet, have a hardware and a software firewall, etc. while using Ubuntu?

What are the facts?  

I figured that if I posted this in this section I would get a larger variety of more experienced users to comment, with some sincere and constructive replies.  
Remember many of us Linux 'noobs' have been burnt "long time big time" by Micro$oft!

Thanks!

---

### Post by meng on 2006-10-14
I must admit to some confusion as to why you felt you needed to install all those packages in order to get your HP printer to work (e.g. mine, similar model, worked "out of the box"). build-essential? that allows you to compile from source, which you don't require if you are installing from binary repositories. python2.4-dev? I don't know why that would be needed!

So that's part of the problem right there, in the first place you're trying to install a bunch of stuff that isn't really necessary for using your printer, and it's circular logic to turn around and complain that the system is forcing you to install unnecessary bloat.

That said, dependencies and recommended packages are not always determined perfectly, but it's not the Ubuntu devs alone who decide these things (as I understand it). There has to be a compromise between forcing all users to decide exactly what is required, and a usable package management system for those of us who are more simple-minded. Ubuntu is geared more towards low-end users, but there are other distros that cater to the higher end of the spectrum. (If you're really keen and have the time, go for Linx From Scratch!)

I don't feel this is comparable to the Apple philosophy, as there is still significant scope for customization, but there's no denying the default Ubuntu desktop installation is somewhat bloated!

---

### Post by nalmeth on 2006-10-14
> Do I have to start going back into my paranoid mode where I delete all traces of everything after use, scrub the registry weekly, have 3 anti-malware programs, don't use most multimedia extensions live on the Internet, have a hardware and a software firewall, etc. while using Ubuntu?
Just what does this have to do with installing python or setting up your printer, or the extra dependencies involved?

---

### Post by K.Mandla on 2006-10-14
> **emarkay said:**
> I started a thread after a printer install. ...
Hi. I looked at your thread there, and it seems you've told Linux to install the python development packages and so forth. In that sense, when you gave it the install command, it was just doing as you told it.

> **emarkay said:**
> Do I have to start going back into my paranoid mode where I delete all traces of everything after use, scrub the registry weekly, have 3 anti-malware programs, don't use most multimedia extensions live on the Internet, have a hardware and a software firewall, etc. while using Ubuntu?
Nope. In general you don't have to "scrub" as much as you did in Windows. It's still possible to have unneeded packages left as residue of other stuff, and it's still possible to contract bad things, but not nearly as easy as in Windows.

In general, remember if you ask Ubuntu to install a package, it's going to install that package, plus whatever it needs to work. If you try to subtract one of its dependencies, it'll end up confused and unable to finish.

Does that help?

---

### Post by emarkay on 2006-10-14
Ptyhon, Postfix? Ahem, the printer installation INSTALLED them!

[http://sourceforge.net/projects/hplip/](http://sourceforge.net/projects/hplip/) (I am not in Ubuntu now, so I can't confirm this, but I recall this was where I got the updated driver for my HP all-in-one psc1350 as posted elsewhere on this forum.)

The fear that I have, and describe, is my fear that I may have to resort to being paranoid because of the decades of issues I have had with Window$, and may need to 'ramp it up' with Ubuntu, if installers are placing all this unneeded stuff in Linux packages.

I also do want to figure out how to remove some of the bloat (games, bluetooth, bittorrent and other things) from Ubuntu with out breaking it - there are some stern warnings there about removing these things.

MRK

---

### Post by meng on 2006-10-14
What was wrong with the repositories' HPLIP package? Looks like you tried to install from source (refer to my previous post).

---

### Post by skymt on 2006-10-14
> **emarkay said:**
> I also do want to figure out how to remove some of the bloat (games, bluetooth, bittorrent and other things) from Ubuntu with out breaking it - there are some stern warnings there about removing these things.

You can remove any of that with out breaking anything. By "stern warnings", do you mean the removal of ubuntu-desktop? If so, just ignore it. ubuntu-desktop is a "metapackage". It basically defines the packages installed by default. Removing it does no harm at all.

EDIT: Oh, and by the way: don't remove Python. Some important bits of the system use it, and will break without it.

EDIT 2: And Postfix was pulled in by lsb-core, which was, in turn, pulled in by lsb. The lsb package installs a bunch of things some standards committee thinks should be installed on every Linux system. I'd advise not installing it.

---

### Post by K.Mandla on 2006-10-14
> **emarkay said:**
> Ptyhon, Postfix? Ahem, the printer installation INSTALLED them!
That's okay. If you've decided you wanted to try a solution that worked for someone else, you're going to need all the external packages that the utility needs. 

I would agree that they're bloat. And I would agree that it's a waste of bandwidth. But I don't know how you would get around it. If the utility is written in such a way that it relies on those packages, there's not a whole lot to be done about it. You could contact the developers and suggest a diet plan. ... :D

> **emarkay said:**
> The fear that I have, and describe, is my fear that I may have to resort to being paranoid because of the decades of issues I have had with Window$, and may need to 'ramp it up' with Ubuntu, if installers are placing all this unneeded stuff in Linux packages.
I really don't think you should become paranoid about it. And again, if the utility is written to rely on those packages, they're not "unneeded." Quite to the contrary, they're necessary. 

I suppose in one sense, you could jump in there and adjust the original code to avoid those packages. That would depend on your comfort level with their coding, etc.

> **emarkay said:**
> I also do want to figure out how to remove some of the bloat (games, bluetooth, bittorrent and other things) from Ubuntu with out breaking it - there are some stern warnings there about removing these things.
The best place to start is the Add/Remove Programs, then the Synaptic Package Manager. I think some of the stern warnings are probably against removing core, base-level packages that are interdependent throughout the system. But you can give it a try. It's a learning process. :)

---

### Post by emarkay on 2006-10-15
> **meng said:**
> What was wrong with the repositories' HPLIP package? Looks like you tried to install from source (refer to my previous post).

The repository is version 0.9.7 whereas this is version 1.6.9.  I also needed HPIJS for the multifunction to run.

---

### Post by aysiu on 2006-10-15
I think Ubuntu affords you a lot of control, but not total control. As others have pointed out, you may be misinterpreting (or overestimating) the amount of control you don't have.

Still, it is what's known as a "user-friendly" distro. I think there are ones certainly more automated than Ubuntu, but Ubuntu's design goal is not "Do it yourself."

If you want a distro like that, I would suggest you go for Debian, Slackware... or even Linux from Scratch.

---

### Post by skymt on 2006-10-15
> **emarkay said:**
> The repository is version 0.9.7 whereas this is version 1.6.9.  I also needed HPIJS for the multifunction to run.

The HPLIP version in Edgy is 1.6.9, so you may want to just upgrade now. Or wait a couple weeks for the actual release. Edgy also has HPIJS 2.6.9.

---

