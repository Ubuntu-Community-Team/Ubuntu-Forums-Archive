---
title: "Using feisty packages on gutsy"
date: 2007-11-07
forum: General Help
---

### Post by djrobthaman on 2007-11-07
Quick question,

Does anyone know of any issues with installing packages compiled for Feisty on Gutsy instead???

---

### Post by por100pre1 on 2007-11-07
> **djrobthaman said:**
> Quick question,

Does anyone know of any issues with installing packages compiled for Feisty on Gutsy instead???

I know of many issues, ranging from unusable packages to totally broken systems. However some packages work just fine. Which package do you want to install? :-k

---

### Post by pjkoczan on 2007-11-07
It should "work", as in you can probably force the packages to install and run properly provided you have the right architecture. Linux in general is very good about backwards-compatibility (unless you're trying to run pre-Redhat 6.1 binaries on the newest RHEL 5...but why would you do that anyway?)

There are a few concerns, and probably reasons you really *don't* want to do this...
- The update manager will probably whine at you and think that you should use the gutsy package.
- You will likely have to use some sort of --force option when installing, this is usually a red flag/caveat emptor/Danger, Will Robinson.

It sounds like it's a third-party package (not part of the repos) and that you didn't compile it yourself. The maintainers probably have gutsy builds, or you might be able to build it yourself if you're so inclined, or you just might have to update a repository entry. My point is, this should be a last resort, if it's a resort at all. There are probably better ways to do this.

---

### Post by djrobthaman on 2007-11-08
Before upgrading to gutsy I was using compiz fusion from Trevino's repositories (tried a couple other repos but found his to be the best.  I know it shouldn't really matter where you get it from... compiz is compiz, but that's how it panned out for me).  I loved that whenever I heard about a new feature that just got added, I had it within days.  Now, I'm using the version included with gutsy, which is great.  One the main reasons I hadn't checked back on his (Trevino's) site for a gutsy version of compiz was that drag and drop worked with the scale plugin, which hadn't worked in trevino's version for ages.  But now I read on the compiz blog that they've got it to work again in the latest build.  So, I figure I'd try his version... but he has no gutsy repositories yet.  I even tried typing in gutsy instead of feisty in the address to see if it was there anyway (actually worked when feisty came out), but none.

So, I was thinking of using his fiesty repos.

What do you guys think?  Yes? No?

---

