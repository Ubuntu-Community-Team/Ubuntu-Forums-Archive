---
title: "add-apt-repository does not edit sources.list"
date: 2012-11-25
forum: General Help
---

### Post by GuitarzanHV on 2012-11-25
When trying to add the Webupd8 Rhythmbox PPA to my system through
sudo add-apt-repository ppa:webupd8/rhythmbox
the command seems to work fine. Then i apt-get update and upgrade, and it shows no upgrade to be found. When i run
sudo add-apt-repository -r ppa:webupd8/rhythmbox
right afterward, it tells me it does not exist in any sources.list files.
Does anybody know what is going on?

P.S. - I have a **ton** of PPAs on my system. Is this part of the problem?

---

### Post by ibjsb4 on 2012-11-25
Looks like you have a typo.

webupd8team/rhythmbox

[https://launchpad.net/~webupd8team/+archive/rhythmbox](https://launchpad.net/~webupd8team/+archive/rhythmbox)
[]("http://ppa.launchpad.net/webupd8team/rhythmbox/ubuntu")

---

