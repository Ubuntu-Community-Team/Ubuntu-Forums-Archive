---
title: "archive mounter?"
date: 2019-01-21
forum: General Help
---

### Post by cdnhermit on 2019-01-21
Hello, I downloaded fritzing-0.9.3b.linux.AMD64.tar.bz2. How do I install it? It is sitting at /tmp/mozilla_daniel0. Apparently I can open it with archive manager or archive mounter. I have opened it with archive manager and it seems I can only extract files. But I want to install it. Any good help is appreciated as I am new to Linux

---

### Post by ajgreeny on 2019-01-21
What does that archive contain?
Did it come from [https://launchpad.net/ubuntu/+source/fritzing](https://launchpad.net/ubuntu/+source/fritzing) ?

Tell us a bit more, and also look for a file called **install** in the archive which may tell you all you need.

---

### Post by TheFu on 2019-01-21
Being new to Linux, you probably don't know about PPAs.  These are how we extend the approved, Canonical, repos to include others from trusted sources. Using PPAs means the normal apt update/upgrade methods work to maintain the software.

[https://launchpad.net/~ehbello/+archive/ubuntu/fritzing](https://launchpad.net/~ehbello/+archive/ubuntu/fritzing) Follow the instructions to add the PPA to your system, then use **sudo apt update && sudo apt install fritzing** to install.  This should address any necessary dependencies too, BTW.

Downloading files directly should be the last choice for running any software on Linux. If you must, then you need to manually handle all the dependencies and manually get upgrades every few weeks.

Try to use APT whenever you can.  In this case, it appears you can.

Good luck.

---

### Post by oldos2er on 2019-01-21
Fritzing is in the repositories,  at least for 18.10.

---

### Post by cdnhermit on 2019-01-21
No I downloaded from the Fritzing site. I will follow your link, Thank you.

---

### Post by cdnhermit on 2019-01-21
Yes it is but it produces a major error.  "Cannot read file /home/daniel/bins/core.fzb:" I have another loading window saying: loading bin "core".

---

### Post by cdnhermit on 2019-01-21
Thank you TheFlu, I am afraid that luck will not be sufficient. Following [https://launchpad.net/ubuntu/+source/fritzing](https://launchpad.net/ubuntu/+source/fritzing) OR [https://launchpad.net/~ehbello/+archive/ubuntu/fritzing](https://launchpad.net/~ehbello/+archive/ubuntu/fritzing), the more I click on a link, the more there are files presented and the less I know which to choose from. To download the file from the Fritzing site is not complicated but then it seems I need a PPA. No idea what it is and if that is required, should it not already be included in the file?

In the link: [https://launchpad.net/ubuntu/+source/fritzing](https://launchpad.net/ubuntu/+source/fritzing) there is a file:

The Cosmic Cuttlefish (current stable release) 0.9.3b+dfsg-4.1ubuntu2 AND The Bionic Beaver (supported) 0.9.3b+dfsg-4.1ubuntu1 that could choose from. This raises questions:     
1) I have Ubuntu 18.10.1 the beaver one. Which should I get if it matters?
2) Should I click on one of those 2 links OR on their corresponding Fritzing Trunk Series link?

Suppose I click on the current stable release I will be presented with 3 files but further down there are 3 other binary files I could download. Which is the proper one? If I should download from the Fritzing Trunk Series then I am offered 3 choices in the published section and one choice in lthe source package; no matter which of the last 2 choices, I am again presented with lots of files, this is totally insane.

Suppose I click on its corresponding Trunk Series link I am presented with the same insane choices plus there are a bunch of Build dependencies that I have no idea how to deal with those.

[https://launchpad.net/~ehbello/+archive/ubuntu/fritzing](https://launchpad.net/~ehbello/+archive/ubuntu/fritzing) is offering older files with version 0.9.2b while the last version of june 2016 is 0.9.3b. Anyway there are 6 files to download which is a mystery on how to install them. Then this PPA that I am not certain. 

What would you download It is really confusing for me?

---

