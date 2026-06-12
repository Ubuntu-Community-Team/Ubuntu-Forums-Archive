---
title: "Looking to run 32bit browser on 64bit OS"
date: 2007-10-16
forum: General Help
---

### Post by evsoul on 2007-10-16
First off, sorry if this is a redundant question.. I tried to search and found nothing. Nor did the "here are the similar threads we found" find anything.

OK, now that I have a clear conscience,

How stable is it to run a 32bit web browser on a 64bit system?
I currently have firefox that is 64bit.. I did this without thinking about flash and I setup way too much to want to just reinstall in 32bit. 

Does anyone have any suggestions for alternative web browsers I can install in 32bit on my 64bit Ubuntu? 

If its best to just reinstall in 32bit I will do that. But I'd prefer some alternatives for now as I just got settled with my configuration.

thanks guys!

---

### Post by Rui Pais on 2007-10-16
simple and easy:
[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64](http://ubuntuforums.org/showthread.php?t=202537)

May i suggest you go for swift weasel32. You can, that way, keep your firefox 64 and use swiftwesel (a variant of Firefox compiled for your arch) to use with flash and java.
:)

---

### Post by evsoul on 2007-10-16
Oh cool I will check SW out.
If it doesn't work for me I will try the 32bit FF.

thanks!

---

### Post by Rui Pais on 2007-10-16
> **evsoul said:**
> Oh cool I will check SW out.
If it doesn't work for me I will try the 32bit FF.

thanks!

You welcome :)

---

### Post by evsoul on 2007-10-16
Do you have a link to swiftweasel? Google is not bringing anything up that I can see.

---

### Post by Rui Pais on 2007-10-16
> **evsoul said:**
> Do you have a link to swiftweasel? Google is not bringing anything up that I can see.

running kilz script will download and install it if you choose that browser... on the other hand i have an idea that it pulls some old version of swiftweasel. 
So here is the link:
[http://swiftweasel.sourceforge.net](http://swiftweasel.sourceforge.net)

Downloads [here]("http://sourceforge.net/project/showfiles.php?group_id=195473").
Choose:
[swiftweasel32 for Intel]("http://downloads.sourceforge.net/swiftweasel/swiftweasel32-2.0.0.7_nocona-32bit_ubuntu-AMD64.deb?modtime=1190259872&big_mirror=0") or [swiftweasel32 for AMD]("http://downloads.sourceforge.net/swiftweasel/swiftweasel32-2.0.0.7_athlon64-32bit_ubuntu-AMD64.deb?modtime=1190259849&big_mirror=0").

then you can run kilz script to get flash+java, answering that you already have a 32bits when asked, to skip that step (the browser installation).

hth

---

### Post by evsoul on 2007-10-16
I get an error with the package installer..

"Error Dependency is not Satisfiable: ia32-lib-firefox"

Any idea what that would mean?:confused:

---

### Post by Rui Pais on 2007-10-16
> **evsoul said:**
> I get an error with the package installer..

"Error Dependency is not Satisfiable: ia32-lib-firefox"

Any idea what that would mean?:confused:

You need ia32-lib-firefox (and possibly others). 

Maybe better do the other way around. Run 1st kilz script, install swiftweasel with it (it will install everything need). 
When finish, check if you got the latest  version, 2.0.0.7. If not, install the deb you downloaded over it.

That should do the trick.

post on any doubt

---

### Post by evsoul on 2007-10-20
ok thanks a lot man. I will work with that tonight.

---

### Post by dcstar on 2007-10-20
> **Rui Pais said:**
> simple and easy:
[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64](http://ubuntuforums.org/showthread.php?t=202537)

May i suggest you go for swift weasel32. You can, that way, keep your firefox 64 and use swiftwesel (a variant of Firefox compiled for your arch) to use with flash and java.
:)

On Gutsy I have flash (and Java) working fine on the native 64 bit Firefox that comes with it, why would anyone need a 32 bit browser?

---

### Post by lonniehenry on 2007-10-20
dcstar -- if you have java working on 64 bit Gutsy, please instruct us on how you did it.  I have not been able to get it to work with 64 bit Firefox.  Thanks

---

### Post by dcstar on 2007-10-20
> **lonniehenry said:**
> dcstar -- if you have java working on 64 bit Gutsy, please instruct us on how you did it.  I have not been able to get it to work with 64 bit Firefox.  Thanks

Just install the Icedtea version of Java offered when you visit a site that needs the Java plugin - or install it using Synaptic - it seems to work fine for me.

You need the Universe repository enabled to get it (and I seem to recall that I had to uninstall the "standard" Java plugin).

---

