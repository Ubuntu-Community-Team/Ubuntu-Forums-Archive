---
title: "Deleting a package from a repository"
date: 2014-11-20
forum: General Help
---

### Post by Brandon_MacEachern on 2014-11-20
Running into a huge problem here.  The main ubuntu repository has a package called "compton", but it's numbered incorrectly.  It has a version number of 0.1beta2, but the official developers repository has the actual latest version numbered 0.0.9.  Guess which one apt-get keeps pulling.

So I went into synaptic and did a package force version and got the real latest installed.  But now every single time the computer wants to do an update, it keeps trying to actually downgrade compton because it thinks it's doing an upgrade.

How can I essentially delete compton out of the ubuntu repository (in my computers eyes that is), so this does not happen?

---

### Post by vasa1 on 2014-11-20
Have you installed a ppa for Compton? Is that what you mean by "the official developers repository"?

---

### Post by qamelian on 2014-11-20
Unless you've made a typo somewhere. 0.1beta2 is a more recent version number than 0.0.9.

---

### Post by deadflowr on 2014-11-20
Perhaps you should contact [richard grenville at launchpad]("https://launchpad.net/~richardgv/+archive/ubuntu/compton") and ask why the latest upload is 0.0.9 (around two weeks ago), yet the ppa page says that version 0.1beta2, which is somewhere around a year old is listed as newer.
Maybe he can explain what it means...

Edit: Oh, and for the record compton is in universe, not main.
nitpicking, but there is a major difference in the two.

---

### Post by Brandon_MacEachern on 2014-11-20
> **qamelian said:**
> Unless you've made a typo somewhere. 0.1beta2 is a more recent version number than 0.0.9.
It's really not, or I wouldn't have made this thread.

0.1beta2 is a year old, but 0.0.9 is only a few weeks old.  It's a problem with version numbering.

---

### Post by vasa1 on 2014-11-20
Nice to know: [https://github.com/chjj/compton/issues/251](https://github.com/chjj/compton/issues/251)
> I tried Ubuntu's own forum to ask this but they usually never give me the help I ask, so I'm gonna ask here in hopes I can actually solve this.

---

### Post by Brandon_MacEachern on 2014-11-20
Well the track record here is at least 10 questions unanswered, multiple bumps and no answers, and I've always had to ask elsewhere for help. I got more ubuntu help even on xfces board, even with unity. I never get help here. So you can't fault me for getting rather impatient here.  Especially like above. Oh I must be wrong on the version numbers, even though date stamps don't lie. But it's me. I'm just wrong. Lol. 

That's why I said that.  For those very reasons.

---

### Post by Impavidus on 2014-11-20
You could pin the package to a specific version. It's quite easy in synaptic. And use synaptic to force a specific version from your preferred source when an update is available.

---

### Post by buzzingrobot on 2014-11-20
0.1beta2 is the release in Jessie and Sid, whence came the Ubuntu package.

I've found that blocking updates in Synaptic does not necessarily block an update via apt, or vice versa.

---

### Post by vasa1 on 2014-11-21
> **Brandon_MacEachern said:**
> Well the track record here is at least 10 questions unanswered, multiple bumps and no answers, and I've always had to ask elsewhere for help. I got more ubuntu help even on xfces board, even with unity. I never get help here. So you can't fault me for getting rather impatient here.  Especially like above. Oh I must be wrong on the version numbers, even though date stamps don't lie. But it's me. I'm just wrong. Lol. 

That's why I said that.  For those very reasons.
Well, all the best. Although sometimes it pays to look inwards.

---

