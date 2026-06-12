---
title: "Xiphos &amp; Ubuntu Repo's"
date: 2014-08-21
forum: General Help
---

### Post by andrew5859-e on 2014-08-21
Has anyone bothered to update the Ubuntu repo's for the newest version of xiphos......as I see it, it's still stuck on 3.1.5, when the newest version is 3.2.1

Sword is also updated, using version 1.7.0 or higher......could someone please update the repo's to reflect this, so those of us who actually want to use this newer version can actually do so?  Thank you in advance  


Andrew

---

### Post by deadflowr on 2014-08-21
You be better off asking the maintainers, possibly here
[https://launchpad.net/ubuntu/+source/xiphos](https://launchpad.net/ubuntu/+source/xiphos)

Developers rarely, if ever, read the forums, and we have nothing to do with what goes in or comes out of the repos.

---

### Post by Impavidus on 2014-08-21
The contents of the repositories are mostly frozen after the release of an Ubuntu version, except for bug fixes and security issues (which are, in fact, also bugs). This makes the software less buggy and more reliable, as everything can be tested together and, if necessary, tuned for Ubuntu. There are some exceptions, like Firefox. New releases of software will come at the next release of Ubuntu in October. If you really need the latest release of something instead of a version of half a year old (sometimes older), try to find a PPA or install manually, but that is usually not recommended.

---

### Post by ian-weisser on 2014-08-21
> **andrew5859-e said:**
> Has anyone bothered to update the Ubuntu repo's for the newest version of xiphos......as I see it, it's still stuck on 3.1.5, when the newest version is 3.2.1

Updating is a user-community repsonsibility, not a Canonical or developer job.
In other words, *you* and other xiphos users didn't bother to update it. Do feel free to get involved with packaging updated software.

 Xiphos is migrated from Debian every six months.
Debian updates since 3.1.5 have been blocked by a bug. See [https://tracker.debian.org/pkg/xiphos](https://tracker.debian.org/pkg/xiphos) for complete details.
Since Debian cannot update versions due to the bug, Ubuntu obviously get the updated version either.

---

### Post by andrew5859-e on 2014-08-28
It's a pretty sad thing, when everyone wants to pass the buck....I myself, am not a programmer/developer.  Who exactly maintains the repo's if the developers aren't involved in that.....the sites given/suggested above, don't really give any straight answers either...

---

### Post by ian-weisser on 2014-08-28
> **andrew5859-e said:**
> It's a pretty sad thing, when everyone wants to pass the buck....I myself, am not a programmer/developer.  Who exactly maintains the repo's if the developers aren't involved in that.....the sites given/suggested above, don't really give any straight answers either...

See [https://tracker.debian.org/pkg/xiphos](https://tracker.debian.org/pkg/xiphos) for straight answers.
All the answers are there.
Really. Look carefully. 

The current maintainer is listed there: "CrossWire Packages".
With a link to their e-mail address.
And a full list of all the problems preventing upgrade in Debian.

So maybe you want to ask instead "Why haven't they tried to update the package lately?"
Well, you must ask the *volunteers* at CrossWire Packages that question. Nicely.
You use their output, but you're not their customer. They don't owe you anything.
Perhaps they need your help.

Maintaining and Developing are different, and require different (though related) skills. You don't need to be a programmer to maintain.

---

### Post by andrew5859-e on 2014-08-29
Ok.....I finally got the latest & newest version of xiphos on my laptop, soon to go on all my other machines.....for anyone else who is interested in upgrading, and/or those who are maintaining the repo's.....here's the site with the latest:


[http://sourceforge.net/projects/gnomesword/?source=typ_redirect](http://sourceforge.net/projects/gnomesword/?source=typ_redirect)


\\:D/

---

### Post by ian-weisser on 2014-08-29
Glad you found a solution that works for you.

---

