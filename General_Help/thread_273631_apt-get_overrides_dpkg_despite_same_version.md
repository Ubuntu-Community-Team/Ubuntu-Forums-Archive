---
title: "apt-get overrides dpkg despite same version"
date: 2006-10-08
forum: General Help
---

### Post by Boris2 on 2006-10-08
I hope I choosed the right forum for my question. :)

**History**: I missed a feature in one package, so I installed the source (apt-get source), patched my changes, made a .deb and installed it. It all went fine, the feature worked great.

**Problem**: But on the next apt-get upgrade apt wants to replace my version of this package with it's own one. Although the version is exactly the same.

**Question**: How can I tell apt-get, that there is the right version installed?

---

### Post by William the Conquerer on 2006-10-08
you could repacked the deb so it's a later version number =).  Sorry, I'm sure there's a way to do what your asking though, I'm just not that familiar with all of the features of apt-get...  BUT, I would suggest looking through options in synaptic...  I see a few options like "lock version" and "force version" that might just work for you...

---

### Post by Boris2 on 2006-10-09
> **William the Conquerer said:**
> you could repacked the deb so it's a later version number =).
I had that thought too, but that would potentially prevent security-updates.

> **William the Conquerer said:**
> BUT, I would suggest looking through options in synaptic...  I see a few options like "lock version" and "force version" that might just work for you...
I don't use synaptic, but I'll give it a try.

---

### Post by Boris2 on 2006-10-09
> **Boris2 said:**
> I don't use synaptic, but I'll give it a try.
I can force a version in synaptic, but then I'll have to stick with synaptic because apt-get does not seem to know this setting.

So I continue to look for a solution.

---

### Post by mixmaster on 2006-10-09
If you want to stay on the command line, the forbid-version option in aptitude prevents upgrading to a specific version but allows upgrades beyond that.

Of course, you would then need to use aptitude instead of apt-get but that is not a major hardship - most of the apt-get options carry over to aptitude and the aptitude database is better when it comes to removals (it will automatically remove dependents installed as a result of package install if they are not in use by anyone else).

---

### Post by Boris2 on 2006-10-09
> **mixmaster said:**
> If you want to stay on the command line, the forbid-version option in aptitude prevents upgrading to a specific version but allows upgrades beyond that.
That would be a aceptable solution. As long as nobody steps up with a better one, I'm going to use aptitude.

Thanks.

---

