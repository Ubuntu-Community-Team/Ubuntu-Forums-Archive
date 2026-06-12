---
title: "So how do I upgrade to Feisty exactly?"
date: 2007-04-18
forum: General Help
---

### Post by Fireblend on 2007-04-18
Will it pop up tomorrow like an update and replace edgy or something? @_@ I'm lost here.

---

### Post by justin whitaker on 2007-04-18
> **Fireblend said:**
> Will it pop up tomorrow like an update and replace edgy or something? @_@ I'm lost here.

No. Edgy will soldier on, unless you intervene. You can apt-get dist upgrade and apt will do the whole thing for you. You can also use aptitude. 

Personally, I prefer a clean install, but I'm already running Feisty Beta, and I am up to date. No point. :)

---

### Post by Fireblend on 2007-04-18
I see. What's the difference between that and a clean install? I don't think I should do that, no time to back up all my data. So can I apt-get the beta? or wait til tomorrow?

---

### Post by justin whitaker on 2007-04-18
> **Fireblend said:**
> I see. What's the difference between that and a clean install? I don't think I should do that, no time to back up all my data. So can I apt-get the beta? or wait til tomorrow?

I would make time to backup your data, one way or the other. Dist-upgrading has been known to break systems in the past....

As for your question, I believe you can upgrade to the Beta/RC now. Not sure, haven't tried it. It's really more of a style thing: I prefer to start over with a fresh install rather than dist-upgrading, but that's just me.

---

### Post by old_geekster on 2007-04-18
Upgrade now.  Here is how to do it:

sudo update-manager -c -d

Update Manager will open and inform you that Feist 7.04 is available for upgrade.  Simply start the upgrade.

I have used this method twice and worked great.

---

### Post by Fireblend on 2007-04-18
> **old_geekster said:**
> Upgrade now.  Here is how to do it:

sudo update-manager -c -d

Update Manager will open and inform you that Feist 7.04 is available for upgrade.  Simply start the upgrade.

I have used this method twice and worked great.

Thanks. As soon as I [figure out how to get online again]("http://ubuntuforums.org/showthread.php?t=412958") (>_<) I'll do that.

---

### Post by Fireblend on 2007-04-18
Wait a second. Is this telling me it's gonna remove beryl? Does it not work for Feisty or something?

---

### Post by Julolidine on 2007-04-19
> Wait a second. Is this telling me it's gonna remove beryl? Does it not work for Feisty or something?

You'll have to update your repositories for Beryl to work, and reinstall.  You'll probably have to get nvidia drivers and wireless up and going again too.  

Tis unfortunate, but until there are open source replacements these problems will affect every kernel upgrade.

---

### Post by jonom on 2007-04-19
> **Fireblend said:**
> Wait a second. Is this telling me it's gonna remove beryl? Does it not work for Feisty or something?
Not sure aobut beryl, but Feisty comes with compiz built-in. I've been running it for a few days now on the beta and it's been working and looking great!

---

