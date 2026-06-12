---
title: "is ubuntu behind in software updates?"
date: 2007-06-15
forum: General Help
---

### Post by atlfalcons866 on 2007-06-15
i just noticed that there is thunderbird 2.0.4. My version of thunderbird is 1.5.11. Shouldnt it have been upgraded to thunder bird 2 by the update manager? The gimp is also out of date too. The gimp version is 2.2.13. The latest gimp version is 2.2.15.  Shouldnt the updated versions be in the resportorys?

---

### Post by raja on 2007-06-15
Usually the version in the repos will be somewhat behind the current version. If you absolutely want the latest, you will have to install it yourself.

---

### Post by strabes on 2007-06-15
Which generally involves compiling. You won't have to compile Thunderbird though; you should just be able to download it from mozilla and run it.

---

### Post by raul_ on 2007-06-15
Yeah.

Official repositories can hold really pre-historic versions.
There are some unofficial repos, that you should use at your own risk, but that have much more up to date versions.

I like getdeb.net ;)

---

### Post by atlfalcons866 on 2007-06-16
do other linux distros do that?

---

### Post by raul_ on 2007-06-16
> **atlfalcons866 said:**
> do other linux distros do that?

Do what?

---

### Post by hardyn on 2007-06-16
the ubuntu repositories usually contain the stable build @ the time of release; its the only way to keep the repositories manageable.

we should see thunderbird 2 in the gutsy repos.

---

### Post by atlfalcons866 on 2007-06-17
do other distros like debian or fedora core have prehistoric versions like ubuntu or do they update immediately

---

### Post by information_entropy on 2007-06-17
Read the section entitled **“Debian package life cycle” ** in the wikipedia article about Debian.

[http://en.wikipedia.org/wiki/Debian]("http://en.wikipedia.org/wiki/Debian")

You will get some insight into what it takes to get an update into the repositories.
This is true for any major distribution.

---

### Post by FuturePilot on 2007-06-17
When a version of Ubuntu is released, the repos are frozen, meaning that whatever version of software that is in there will stay at that version. The only updates they get it bug fixes and security updates. Your software gets updated every 6 months with a new release of Ubuntu.

Other distros like Gentoo are based on a rolling release cycle where the most up to date software is added to Portage within a couple days of its release.

Like someone else said, there are 3rd party repos around (use at your own risk;) Although I've never had a problem with using 3rd party repos) or you could always compile it yourself.

---

### Post by handydan918 on 2007-06-17
> **atlfalcons866 said:**
> i just noticed that there is thunderbird 2.0.4. My version of thunderbird is 1.5.11. Shouldnt it have been upgraded to thunder bird 2 by the update manager? The gimp is also out of date too. The gimp version is 2.2.13. The latest gimp version is 2.2.15.  Shouldnt the updated versions be in the resportorys?

It is true that the repos don't stay perfectly up to date with the latest release, but Firefox 1.5?
What version of Ubuntu are you running, Warty? If nothing else, you could try adding the Feisty repos to you sources list and download Firefox from a current repo...

---

### Post by DeeWox on 2007-06-17
> **raul_ said:**
> Yeah.

Official repositories can hold really pre-historic versions.
There are some unofficial repos, that you should use at your own risk, but that have much more up to date versions.

I like getdeb.net ;)
When I download something from getdeb.net and open it with GDebi package installer, I get this error messages when I'm trying to install something: 

ERROR: Dependency is not satisfiable

How do I fix this problem?

---

### Post by Fungyo on 2007-06-17
You may not be able to fix it.
Or
Some software from getdeb have more than one part. There may be a particular order in which you need to install each part for it to install nicely.

---

### Post by DeeWox on 2007-06-17
> **Fungyo said:**
> You may not be able to fix it.
Or
Some software from getdeb have more than one part. There may be a particular order in which you need to install each part for it to install nicely.
Thank you. That got me thinking, so installed it in another order, and it works fine. 

Once again I learn that I'm the idiot, not the programs :D

---

