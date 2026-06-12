---
title: "software center was unable to come up with any suggestions that may aid in you in you"
date: 2015-03-13
forum: General Help
---

### Post by Alduins_Khajiit on 2015-03-13
NO MATTER what I try to search in Ubuntu software center on Ubuntu 14.04, I ALWAYS get an error message, "**software center was unable to come up with any suggestions that may aid in you in your search**"!!! but if I type a bunch of random letters to obviously for a "no results" page it says, "*suggestions: make sure your spelling is correct*"!!!

I googled the first error message but NOTHING came up!!! searching again in quotes results in a "no results for" error message!!!

how do I fix???

---

### Post by oldrocker99 on 2015-03-13
Try using Synaptic, which is sort of "Software Center Pro."
```
sudo apt-get install synaptic
```
It has a quick search window, which matches file names, and a fuller Search function, which searches file descriptions. It also allows you to select multiple files and installs them all at once, unlike the Software Center, which installs one at a time.

The only time I personally use the SC is to reinstall software I have purchased at one time or another. For everything else, I use Synaptic or the apt-get command. You can also search for files using the ```
apt-cache search nvidia (for example)
```command. This also searches file descriptions.

Good luck and post any problems you might have.

---

