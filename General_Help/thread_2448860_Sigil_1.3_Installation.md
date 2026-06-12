---
title: "Sigil 1.3 Installation"
date: 2020-08-15
forum: General Help
---

### Post by Kalyan-sg on 2020-08-15
Hello
I want to install this file **sigil_1.3.0+dfsg-1.debian.tar.xz**

Can someone please tell me step by step how to install this.

Thanks in advance for your help.

Best Regards
Kalyan

---

### Post by Holger_Gehrke on 2020-08-15
This looks like the source-code archive for the ebook-editor sigil in the version that's going to be part of Ubuntu 20.10 (Groovy Gorilla). The easiest way to install this is to wait a month or two, upgrade to groovy and then do a 'apt install sigil'. The next harder way would be to update to groovy now (expect a bit of breakage, it isn't quite done yet) and do the same. The hard way would be to go to [https://sigil-ebook.com/get/](https://sigil-ebook.com/get/) , follow the link to the documentation on how to compile this on Linux and follow that.

If all this doesn't appeal you can get older versions (1.1 on 20.04, 0.9 on 18.04) with apt.

Holger

---

### Post by Yellow Pasque on 2020-08-16
With a few small tweaks to the packaging, I put it in a PPA:
[https://launchpad.net/~dtl131/+archive/ubuntu/mediahacks2](https://launchpad.net/~dtl131/+archive/ubuntu/mediahacks2)

---

### Post by Kalyan-sg on 2020-08-16
Hello I got this response when I tried.

The repository 'http://ppa.launchpad.net/wxformbuilder/release/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by Yellow Pasque on 2020-08-17
What version of Ubuntu are you using?

---

### Post by Kalyan-sg on 2020-08-17
Hello,
The ppa worked perfectly in Ubuntu 20.04. 
'http://ppa.launchpad.net/wxformbuilder/release/ubuntu bionic Release'
I was initially trying in Peppermint 10. It didn't work. But that's off topic.
My apologies.
Many thanks for the help.
Kalyan-sg:D

---

