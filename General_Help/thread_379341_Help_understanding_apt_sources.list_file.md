---
title: "Help understanding apt sources.list file"
date: 2007-03-08
forum: General Help
---

### Post by CaptSaltyJack on 2007-03-08
For the most part I understand how it works.  I'm just having trouble understanding a few things about it..

we have different repositories:

- edgy
- edgy-updates
- edgy-security
- edgy-backports

OK, so "edgy" contains applications like XChat, Gaim, etc., right?  And it will upgrade those apps when new versions are available.  But then what is edgy-updates?  And edgy-security I assume are security related patches.  edgy-backports, not entirely sure what that is.. I think it's bleeding edge software and will upgrade your software as soon as even a minor revision is released.

Now the real question here is about these:

- main
- universe
- multiverse
- restricted

I thought edgy-backports IS basically the multiverse??  So if I have a line like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main multiverse
```

What is that doing exactly?  Does it work like this basically?:

main = fully stable, tested, supported
universe = mostly stable, tested, not supported
multiverse = could be unstable, not fully tested, not supported

I am CONFUSED.  I don't understand the difference between main/universe/multiverse/restricted and edgy/edgy-updates/edgy-security/edgy-backports.

---

### Post by CaptSaltyJack on 2007-03-08
OK I checked out a couple online resources, I think I have a slightly better understanding, but correct me anywhere I'm wrong.

edgy/edgy-updates/edgy-security/edgy-backports = all contain completely different software packages
main/universe/multiverse/restricted = contain different VERSIONS of the above software packages

So for example, Gaim from edgy/main is fully tested/supported, stable, etc.  Gaim from edgy/universe is more up to date, mostly stable, unsupported.  Gaim from edgy/multiverse is brand spanking new latest version, use at your own risk.

Right?

And I assume "restricted" just contains .. what?  DRM related stuff?  Codecs, etc. that are questionable?

I guess what I'm wondering is, what is the appropriate sections (main,universe,etc) to be using for the different distribution sources?  I want a sources.list file that keeps me mostly up to date so I'm not using OLD versions of software, but I also don't want to be running betas and release candidates either.  Maybe this?:

edgy main universe multiverse restricted
edgy-security main universe restricted
edgy-updates main universe restricted
edgy-backports main universe multiverse restricted

---

### Post by PriceChild on 2007-03-08
edgy is what is contained int he final release
edgy-updates & edgy-security are bugfixes and security updates (no new features)
edgy-backports are maintained by the backports team and contain a small amount of packages from feisty recompiled ready for edgy use.

main is officially, completely & utterly supported "free" content.
restricted is officially, completely and utterly supported, non-free content.
universe & multiverse are community maintained, free & non-free.

---

### Post by PriceChild on 2007-03-08
No. Each piece of software is only in one repository. (main, restricted etc. however new versions may be in security,updates,backports)

---

### Post by CaptSaltyJack on 2007-03-08
> **PriceChild said:**
> edgy is what is contained int he final release
edgy-updates & edgy-security are bugfixes and security updates (no new features)
edgy-backports are maintained by the backports team and contain a small amount of packages from feisty recompiled ready for edgy use.

main is officially, completely & utterly supported "free" content.
restricted is officially, completely and utterly supported, non-free content.
universe & multiverse are community maintained, free & non-free.

So THAT'S what "backports" means.. I was wondering, how is that stuff new if it's "backports"?  Backports from Feisty.. gotcha.

Um, so.. if restricted is non-free, does that mean adding it to your sources.list is basically like you're downloading warez?

And the difference between universe and multiverse is what, that multiverse is non-free? (again, is that somehow illegal?)

---

### Post by PriceChild on 2007-03-08
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

Is much better explained :)

---

### Post by CaptSaltyJack on 2007-03-08
Thanks, I will read that thoroughly

I guess "supported by the Ubuntu team" is of zero importance to me.  I don't plan on paying $200 or whatever it is for tech support.. I just come to the forums for help.

---

### Post by CaptSaltyJack on 2007-03-08
OK, below is my new sources.list file.  I removed multiverse, as it sounds like it could be potentially unsafe/unwise to use software from there.. ?  Multiverse is just like a "universe restricted" right?  I guess I don't fully grasp that one yet...

Is this sources.list good for someone who wants to keep their system up to date and stable/secure?

```

deb http://security.ubuntu.com/ubuntu/ edgy-security universe main restricted
deb-src http://security.ubuntu.com/ubuntu/ edgy-security universe main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates universe main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports universe main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe main restricted

deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable
deb http://ubuntu.beryl-project.org/ edgy main

```

One more thing.. let's say a program called GnuBlah is at version 1.0.  This is found in edgy/main.  If there's a bugfix, GnuBlah 1.08, it's found in edgy-updates/main, right?  Basically, if I removed edgy-updates and edgy-security from my sources.list completely, apt-get would NEVER ever find new updates for anything, correct?  And if, on top of that, I removed all references to 'universe,' it would only be browsing the repositories that are official as of Edgy's final release date, right?

---

