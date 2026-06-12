---
title: "[How To] Keep your repos clean"
date: 2008-01-21
forum: General Help
---

### Post by Anduu on 2008-01-21
This may seem obvious to lots of us but with all the dependency problems I have seen new users having over the years I felt the need to share my experience.

Following these simple rules/steps will 99% warranty you will make no trips to Dependency Hell.

**Rules:**

**1:** ***NEVER*** add repos from another distribution...this is a one way trip to hell.
**2:** Back up your sources.lst before making any changes.
**3:** Only use trusted repos...If you are unsure ask on the forums...there isn't a single member of this forum who would willingly let you hose your system.

[B]How to add repos safely:
[/B]
Ok you have decided to take the plunge...there is an app not available through the Ubuntu official repos but you absolutely  *have* to have it...Follow these steps excactly to avoid problems later on.

**1:** Before you even open/modify your sources.list do a sudo apt-get update and a sudo apt-get upgrade to make sure you are up to date.

**2:** Modify your sources.list accordingly and save.

**3:** Don't even think about installing that app just yet.Immediately do an apt-get update/upgrade again.

            If suddenly apt-get wants to update [COLOR="Red"]***_any_***[/COLOR] system files,run like hell and never look back.Immediately remove the repo from the list and pretend it never existed! Ignore steps 4 and 5

This means they include updated versions of certain files the app needs to run and 99/100 times they in turn will have dependencies you ***will not*** be able to satisfy through conventional means.If they include any particularly important system files like libc6 for example your system will go down faster than a two dollar hooker.

**4:** Everything good? Now go ahead and install your app "sudo apt-get install <appname>"

Take careful note of any extra packages it installs and *_where they are coming from_*.If they are coming from the official repos everything is ok.If they are coming from the new repo you added be wary.It is quite possible they are updated versions of packages that are available through the official repos that you haven't installed yet and you could run into problems down the road.

**5:** Just for good measure apt-get update/upgrade one more time If everything comes up clean you should be good to go.

Well that's about all I can think of atm...If anyone else has additional input I'd love to hear it.

If this tutorial saves even one person from a reinstall I'll be a happy camper :)

---

### Post by K.Mandla on 2008-01-22
Moved to General Help.

---

### Post by bodhi.zazen on 2008-01-22
First, do not mix repos unless you know what you are doing.

Second, if you must, learn to pin :

PINNING:
		[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)
		[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

