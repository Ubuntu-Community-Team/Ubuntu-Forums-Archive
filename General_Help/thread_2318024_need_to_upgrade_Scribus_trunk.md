---
title: "need to upgrade Scribus trunk"
date: 2016-03-22
forum: General Help
---

### Post by Buntu Bunny on 2016-03-22
I need to upgrade Scribus 1.5 to 1.5.1. Synaptic only offers 1.5, which I already have. I've found a tar.xz file [here]("http://linux.softpedia.com/get/Text-Editing-Processing/Others/Scribus-2148.shtml"), but seem to recall that this is not the file of choice for Ubuntu. Are there other options? Or can someone tell me how to safely extract and install the tar.xz version?

---

### Post by Dennis N on 2016-03-22
The article states "it is available for download only as a source archive on UNIX/Linux systems" which can't be used as-is. It needs to be compiled, the process which uses the source code to create an executable program.

---

### Post by Dennis N on 2016-03-22
Does this help?

[http://linuxg.net/install-scribus-svn-on-ubuntu/](http://linuxg.net/install-scribus-svn-on-ubuntu/)

---

### Post by Buntu Bunny on 2016-03-22
If it works, it helps, LOL. So if I follow the installation instructions I don't need to compile it?

---

### Post by Dennis N on 2016-03-22
Yes, no compiling if you use the PPA.

The PPA page is here:
[https://launchpad.net/~scribus/+archive/ubuntu/ppa](https://launchpad.net/~scribus/+archive/ubuntu/ppa)

---

### Post by Buntu Bunny on 2016-03-22
Thank you! I'll give this a try when I get home tonight and report back, hopefully with success.

---

### Post by Buntu Bunny on 2016-03-22
```
scribus-trunk is already the newest version.

```

Which on my machine with 12.04, is still Scribus 1.5.0. I notice at Launchpad that 1.5.1 is for Ubuntu 14.04, and that 1.5.2 is available for Ubuntu 15.04, 12.10, and 16.04. So it would seem that I will need to move up to at least 14.04 in order to update Scribus trunk.

---

### Post by Dennis N on 2016-03-22
> **Buntu Bunny said:**
> ```
scribus-trunk is already the newest version.

```

Which on my machine with 12.04, is still Scribus 1.5.0. I notice at Launchpad that 1.5.1 is for Ubuntu 14.04, and that 1.5.2 is available for Ubuntu 15.04, 12.10, and 16.04. So it would seem that I will need to move up to at least 14.04 in order to update Scribus trunk.

Yes, that seems to be the case. They have no package there for 12.04. 15.04 is already out-of-support from Ubuntu, but the PPA has a 15.10 version, and 15.10 is still in-support from Ubuntu for a few more months (Oct 2015 + 9 mos.) and 14.04 up to 2019. 

I recently installed Xubuntu 16.04 beta1, and it seems stable - I haven't seen any problems in limited use. Lots of updates, though.

---

### Post by Buntu Bunny on 2016-03-22
> **Dennis N said:**
> Yes, that seems to be the case. They have no package there for 12.04. <snip> I recently installed Xubuntu 16.04 beta1, and it seems stable - I haven't seen any problems in limited use. Lots of updates, though.

Well, I've dragged my feet in upgrading Xubuntu, and it appears I'm running out of excuses not to. :o  Final release of16.04 is next month, isn't it? That's just around the corner, so perhaps I should do my "fresh install with a home partition how-to" homework in preparation for that.

---

### Post by dragonfly41 on 2016-03-22
For your information ... I worked out how to install scribus-trunk and scribus-ng on Ubuntu 14.04.

The Ubuntu Software Centre version of Scribus stops at 1.5.

I can dig out my installation notes if you want to run Scribus daily build on Ubuntu 14.04.

---

### Post by Buntu Bunny on 2016-03-23
> **dragonfly41 said:**
> I can dig out my installation notes if you want to run Scribus daily build on Ubuntu 14.04.

Thank you for the offer! Since we're so close to the release of 16.04, I think I will just wait on that rather than go with 14.04.

---

