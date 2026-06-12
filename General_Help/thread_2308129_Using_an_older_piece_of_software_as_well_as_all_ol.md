---
title: "Using an older piece of software as well as all older necessary dependancies?"
date: 2015-12-31
forum: General Help
---

### Post by dexter8 on 2015-12-31
I decided to update to 15.10 from 14.04 thinking that an absolutely essential piece of software that I use, would be compatible, but it turns out the last release it supports is 14.10. I've had a go at installing the deb, but to no avail as the dependancies it needs are older than the ones installed. Is there some way to sandbox the an environment where this might work?

---

### Post by brian-mccumber on 2015-12-31
What software are you trying to run?

---

### Post by dexter8 on 2015-12-31
qcma, but there are other situations where a workaround for these types of situations would be useful - I LOVE Courage The Cowardly Dog.

---

### Post by brian-mccumber on 2015-12-31
So have you tried to manually install the dependencies from the links at the qcma github page? 

[https://codestation.github.io/qcma/](https://codestation.github.io/qcma/)

Also Courage is awesome, hehe.
Here is another avatar I made that you might like. I drew this one with Illustrator when I was running Windows. It's a little large but pics look better when you make them large then resize them.

[http://americanacolyte.site50.net/dexterLg.png](http://americanacolyte.site50.net/dexterLg.png)

---

### Post by monkeybrain20122 on 2015-12-31
You have to manually install the dependencies in your $HOME, then when build qcma set the environmental variables to point to the local dependencies instead of the system ones. Depending on how many such dependencies you have it can be relatively easy or intractable (dependencies depending on other dependencies which also have to be installed locally) I have compiled programs which a are too new so some dependencies have to be compiled locally.

---

### Post by dexter8 on 2015-12-31
> **brian-mccumber said:**
> So have you tried to manually install the dependencies from the links at the qcma github page? 

[https://codestation.github.io/qcma/](https://codestation.github.io/qcma/)

Also Courage is awesome, hehe.
Here is another avatar I made that you might like. I drew this one with Illustrator when I was running Windows. It's a little large but pics look better when you make them large then resize them.

[IMG]http://americanacolyte.site50.net/dexterLg.png[/IMG]
Really awesome. Yeah, the dependancies that it needs are already installed, albeit newer than it wants.

---

### Post by dexter8 on 2015-12-31
I was afraid that it may be a little beyond me. Is there a noob guide to achieving this?

Cheers!

---

### Post by monkeybrain20122 on 2015-12-31
> **dexter8 said:**
> I was afraid that it may be a little beyond me. Is there a noob guide to achieving this?

Cheers!

Hard to say, it depends on the build recipe for the software and the dependencies. You have to give more info.

---

### Post by brian-mccumber on 2015-12-31
I have traced the dependencies from the other dependencies for qcma and it would be quite a complicated procedure to get this installed manually because the qcma dependencies have dependencies so there is a long line of stuff you'd have to install to get this working right. 

I found this - [https://dogfood.paddev.net/~codestation404/+archive/ubuntu/qcma](https://dogfood.paddev.net/~codestation404/+archive/ubuntu/qcma)    it is untrusted but if you're into experimentation you could remove qcma, add this repository and then try to install qcma again. It looks like this ppa includes the vitamtp package which is probably the package that is causing you the problem since qt and ffmpeg can be installed through the software center. I think ffmpeg is included in the Ubuntu restricted extras.

---

### Post by brian-mccumber on 2015-12-31
You can always go to the qcma github page and follow those links and read everything carefully especially the parts about dependencies and then search those up to see how to install them and work your way up the tree. It would be a long process but it has been done successfully before.

---

### Post by monkeybrain20122 on 2015-12-31
Some dependencies in 15.10 may still work. I would think actually most would. Just install the dependencies from the system and try to build it. When you get errors you would know which doesn't work and have to be separately installed. The most tricky thing would be compiler. If the software is really old the new compiler in 15.10 may not work, but since you are only upgrading from 14.04 it is not likely.

---

### Post by Yellow Pasque on 2015-12-31
Use the source(, Luke)!

I just built it (vitamtp and qcma) successfully in my Ubuntu 15.10 VM, but the GUI segfaults. I tried to use the latest stable tarballs together and also tried cloning directly from git.

The build procedure is relatively clean since the devs have the debian packaging included: The recipe follows, though you will likely encounter missing dependencies when you debuild. No worries though. Just copy/paste the list of missing packages into a 'sudo apt-get install' command:
```
sudo apt-get install devscripts build-essential git wget
cd ~/
mkdir source
cd source/
git clone https://github.com/codestation/vitamtp.git
cd vitamtp/
debuild -B -us -uc 
cd ..
sudo dpkg -i libvitatmp*
git clone https://github.com/codestation/qcma.git
cd qcma/
debuild -B -us -uc
cd ../
sudo dpkg -i qcma*.deb
```

---

### Post by HermanAB on 2016-01-01
Install Virtualbox and an old version of Debian with your old software, then set it up to launch transparently on the host desktop.

---

