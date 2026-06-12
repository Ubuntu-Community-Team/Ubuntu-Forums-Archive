---
title: "Adept keeps telling me there is one update available"
date: 2007-01-27
forum: General Help
---

### Post by Duffy on 2007-01-27
On Kubuntu, Adept keeps telling me there is one update available. Then when I tell it to fetch the updates, it tells me nothing is available to update. Anyone have an idea why it thinks there is an update when there isn't any? Is there a way to reset it?

---

### Post by taurus on 2007-01-27
Try to run it from a terminal and see what happens.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Duffy on 2007-01-27
Just did that and it tells me the same thing, nothing to update or upgrade. I even did a complete removal of Adept and Adept Notifier, restarted, reinstalled, rebooted and back to the same problem. I am perplexed.

---

### Post by taurus on 2007-01-27
Did adept tell you the name of the package?  Otherwise, I wouldn't worry too much about it.

---

### Post by AusIV4 on 2007-01-27
I'm running Kubuntu Dapper on one of my boxes, and it has one package that will never upgrade correctly: linux-image-2.6.15-27-386 - and every time I want to run adept updater I have to mark it not to update or the update fails.

---

### Post by Duffy on 2007-01-27
That's not my issue. It's not that it is failing to update a package, it's that Adept Notifier keeps telling me there is one updated package available, then I click on the icon to start Adept and Adept starts, I tell it to fetch the updates, and it does its thing and tells me there are not updates available.

---

### Post by ulriks on 2007-02-10
I am having the same issues - and have had them for a long time.

My solution was not to have the adept-notifier running, but to do 
```
apt-get update
apt-get upgrade
```
from the command line.

I have completely removed the adept-notifier including all dirs I could find belonging to adept, but the issue is still there on reinstall.

Attached is a screenshot of the issue

---

### Post by headphase on 2007-10-08
I am having a similar problem on Feisty, only it asks me to update compiz-core.

---

### Post by tjk on 2007-10-08
> **headphase said:**
> I am having a similar problem on Feisty, only it asks me to update compiz-core.

Exactly same thing here.  Could it be a problem with compiz-core?

---

### Post by ulriks on 2007-10-09
I think it is an issue with Adept as I do not have compiz installed

---

