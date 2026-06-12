---
title: "Where is libreoffice in software manager?"
date: 2013-02-10
forum: General Help
---

### Post by lsutiger on 2013-02-10
I followed the instructions to add the PPA for 10.04 [from this link]("https://wiki.ubuntu.com/LibreOffice"). After going through each step, I go to the software center, but libreoffice can not be found. So I try via CLI and  get a message that it is not available. Did I miss a memo?

---

### Post by fj401971 on 2013-02-10
You made sure to run "sudo apt-get update" afterwards?

---

### Post by lsutiger on 2013-02-10
Yes

---

### Post by lsutiger on 2013-02-10
This is strange, I think. I looked up the repositories in the update manager. Attached is the screen shot. You can clearly see that libreoffice is there. I then did a search through the sources.list file. Not there???

---

### Post by lsutiger on 2013-02-10
bump

---

### Post by Yellow Pasque on 2013-02-10
Please do not bump more than once every 24 hours.

The problem is the instructions. They tell you to use the wrong PPA (the one you added doesn't have libreoffice packages for lucid). Remove the PPA you added and use this one: [https://launchpad.net/~libreoffice/+archive/libreoffice-3-5](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5) (ppa:libreoffice/libreoffice-3-5)

---

### Post by lsutiger on 2013-02-10
Sorry for being an A-hole! But it was in the official ubuntu wiki...How was I to know different? 
This should have been updated by those who regulate this system....just saying.
Oh I forgot to say thank you!

---

### Post by Yellow Pasque on 2013-02-11
> **lsutiger said:**
> Sorry for being an A-hole!
I just informed you of a (unwritten?) forum rule. I wasn't implying you were being obnoxious (now if you had bumped 20 times in one day...).

> But it was in the official ubuntu wiki...How was I to know different?
You weren't. That's why I told you.

> This should have been updated by those who regulate this system....just saying.
It's fixed...

> Oh I forgot to say thank you!
You're welcome. Please mark the thread [SOLVED] in the thread tools menu towards the top of the page.

---

