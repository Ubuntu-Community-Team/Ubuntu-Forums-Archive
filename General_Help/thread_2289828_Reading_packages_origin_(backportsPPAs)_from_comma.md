---
title: "Reading packages origin (backports/PPAs) from commandline"
date: 2015-08-07
forum: General Help
---

### Post by cogset on 2015-08-07
Synaptic can display (=filter) packages  originating from backports or PPAs, is there a way to do that (without some complicated script) via commandline?

As far as I can see, in Synaptic I can use the "Origin" tab to isolate packages coming from backports, and set a custom filter to identify packages coming from a given PPA: if Synaptic can do that, it is certainly using the underlying apt tools, problem is, I can't figure out a simple command to do that.

That would come handy when updating with apt-get, to pinpoint which packages are going to be updated as part of a normal security update and which instead as part of a PPA (I may want to apply regular updates but not install newer versions of packages that are part of the default distribution but are also  provided by a PPA with higher version numbers) .

I could certainly list the relevant packages with apt-cache policy, but is there any quicker/nicer way to do that?

I could also simulate an upgrade first with the normal release as a target and then with the backports, but again, is there a more elegant and quicker way to do this?

---

### Post by ian-weisser on 2015-08-07
'apt cache policy <packagename>' will tell you the source.

---

### Post by cogset on 2015-08-08
> **ian-weisser said:**
> 'apt cache policy <packagename>' will tell you the source.

Sure, I had no doubt about that (see my post above):
 > I could certainly list the relevant packages with apt-cache policy, but is there any quicker/nicer way to do that?


Maybe I didn't explain myself so well, the thing is that after (eventually) adding backports and /or PPAs to your sources, apt-get upgrade will list all packages that are going to be upgraded, but without clearly telling you which are coming from default sources and which instead from backports/PPAs.

Therefore, a less tedious way  then listing each upgradeable package with apt-cache policy would be what I'm after.

---

### Post by ian-weisser on 2015-08-08
I am unaware of any other apt command that does what you wish. Apt assumes that you, the admin, have added only trustworthy and fully-compatible sources. You seem to be trying to override that basic assumption, and Apt doesn't really roll that way. Dpkg, however, does allow you to choose your source...since it cares nothing about sources.

---

### Post by cogset on 2015-08-10
So it's confirmed, there is no (easy) way with apt to  quickly tell apart packages coming from other sources than the default repositories.

On regard to this > Apt assumes that you, the admin, have added only trustworthy and  fully-compatible sources. You seem to be trying to override that basic  assumption
it's not like I've been trying to mix and match who knows what sources, it's just that sometimes a program (or even a single package) that you may want is only available through (official) backports or a PPA, and you may only be interested in installing that package and not all the other packages included in those backports/PPAs.

Problem is, a normal *apt-get upgrade* even with the -V option won't tell you where those upgrades are coming from, so you are either stuck with manually checking each upgradeable package with apt-cache policy or install them all and be done with it.

I've read somewhere that some black magic with Aptitude could possibly do what I'm after, but I really don't understand how to use Aptitude...

---

