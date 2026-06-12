---
title: "[SOLVED] Making Math Image thing"
date: 2008-02-12
forum: General Help
---

### Post by dethredic on 2008-02-12
I need to to make an image like this:

[IMG]http://www.ghostshipmorphy.com/downloads/unity.PNG[/IMG]

What program could I use to make it?
I used to do it in word.

---

### Post by apetresc on 2008-02-12
LaTeX! It's the best system for typesetting mathematics, and it's used by almost all mathematical journals nowadays.

Information on setting it up is all over the place. Try [here](https://help.ubuntu.com/community/LaTeX) for starters.

Go with TeX-Live, not tetex.

---

### Post by dethredic on 2008-02-12
well, I went to their site to dl it. 1gig. This will take a couple mins...

will update soon.

---

### Post by apetresc on 2008-02-12
> **dethredic said:**
> well, I went to their site to dl it. 1gig. This will take a couple mins...

will update soon.

Their site? What? It's in ubuntu's repository, and much smaller there (because it's broken up into multiple packages that you can pick and choose just the features you need)

You shouldn't need to get anything from "their" site, whoever "they" are.

---

### Post by aJayRoo on 2008-02-12
Whilst I agree that LaTeX is certainly the best tool for getting the job done well, it can be quite daunting. I just thought you might like to know that openoffice has a formula tool/application that can create these kind of equations. I believe it uses the same syntax as latex, however you won't need to deal with the other elements of latex required to produce a document... and since the syntax is the same you can always apply what you learn to latex later on. Hope that helps.

---

### Post by dethredic on 2008-02-12
> **aJayRoo said:**
> Whilst I agree that LaTeX is certainly the best tool for getting the job done well, it can be quite daunting. I just thought you might like to know that openoffice has a formula tool/application that can create these kind of equations. I believe it uses the same syntax as latex, however you won't need to deal with the other elements of latex required to produce a document... and since the syntax is the same you can always apply what you learn to latex later on. Hope that helps.

Where can I find this? I can get a formula bar, but that just acts like a calcluator

---

### Post by polmir on 2008-02-12
If You do not know Latex You try wysinwyg-frontend for LaTeX --- **lyx**
```
sudo apt-get install lyx
```

---

### Post by Whiffle on 2008-02-12
> **dethredic said:**
> Where can I find this? I can get a formula bar, but that just acts like a calcluator

Openoffice Writer -> Insert > Object > Formula

---

### Post by dethredic on 2008-02-12
Great the open office one is fine, but I am gonna try lyx cause i got some free time.

Is there any way to export the formula as an image (in openoffice), because taking a screen shot and croping it takes too long.

---

