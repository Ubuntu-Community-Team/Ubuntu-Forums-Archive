---
title: "Flash Installer Error"
date: 2008-01-14
forum: General Help
---

### Post by blanc11 on 2008-01-14
I got a strange flash installation problem. When I visit a site with embedded flash Firefox asks me if I want to install it. The installation appears to work normally but when I click finish the page reloads yet it says I need to install flash again and Firefox also asks me if I want to install again. Is this some kind of Bug?
Thanks!

Ubuntu 7.10
Firefox 2.0.0.11

---

### Post by steeleyuk on 2008-01-14
There is a problem with installing Flash, from what I remember is has to do with the CRC (checksum) being different to the one the repo has. You'll need to download a DEB file and install manually.
[URL="http://lug.mtu.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.31.0.2ubuntu1_i386.deb"]
Try this[/URL].

If that doesn't work the Launchpad report is [here]("https://answers.launchpad.net/ubuntu/+question/10061") with more suggestions.

---

### Post by blanc11 on 2008-01-14
Thanks for the reply, however, I am still having the same problem :(

---

### Post by wolfen69 on 2008-01-14
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file. you can remove it in synaptic.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by blanc11 on 2008-01-14
It works! Thanks guys for the help! ;)

---

### Post by clong83 on 2008-01-14
Blanc, do you have a 64-bit version of Ubuntu?  Adobe doesn't really support 64-bit Linux and that could be the problem.  There are some workarounds [here]("http://ubuntuforums.org/showthread.php?t=664588&highlight=flash+firefox") and [here]("http://ubuntuforums.org/showthread.php?t=202537").  Hope that helps.

---

### Post by clong83 on 2008-01-14
Ah, well nevermind then.  Glad you got it working.

---

### Post by buspital on 2008-01-14
fixed it for me too, thanks

---

