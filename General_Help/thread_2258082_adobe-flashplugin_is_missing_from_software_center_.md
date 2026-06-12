---
title: "adobe-flashplugin is missing from software center in 14.04"
date: 2014-12-24
forum: General Help
---

### Post by aprekates2 on 2014-12-24
Having trouble viewing videos in firefox i saw in ubuntu software center that  addon adobe flash is installed .
Searching i came onto:
[http://ubuntuhandbook.org/index.php/2014/04/install-adobe-flash-in-ubuntu-14-04-lts/](http://ubuntuhandbook.org/index.php/2014/04/install-adobe-flash-in-ubuntu-14-04-lts/)
suggesting to install from command line adobe-flashplugin cause for 64bit systems (like mine) the
aforementioned package wont do.
My question is why 'adobe-flashplugin' is missing from U.C.S ? 
(i activated all repos in ucs).

Thanks
alexandros


lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
$ uname -a
Linux enousII 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by deadflowr on 2014-12-24
Firstly, you should update your system, linux image 3.13-40 is little old now, the latest is 3.13-43 from what i have.

Secondly, adobe-flashplugin is actually in the Partner repository, which you need to enable yourself.

Thirdly, you can get flash through the terminal by using the flashplugin-installer package, which itself is in the multiverse repository.
```
sudo apt-get install flashplugin-installer
```

Have no idea if this will be helpful, but I see flash in the software center just fine.

---

### Post by raptir on 2014-12-24
One thing to keep in mind is that Adobe dropped full support for the NPAPI plugin a while back and it now only receives security updates. As a result, some sites will see that you're using an old version of flash (11.x instead of the current 16.x) and will refuse to play video regardless. Google Chrome is unfortunately the only way to run an up-to-date flash on Linux at this point.

---

### Post by deadflowr on 2014-12-24
> Google Chrome is unfortunately the only way to run an up-to-date flash on Linux at this point.

Natively.
You can have an updated flash using packages like Pipelight
[http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)

fer what it's worth.

---

### Post by aprekates2 on 2014-12-24
thanks for feedback.
it turned out it was a software center's poor search issue !
I added a comment in :
[https://bugs.launchpad.net/software-center/+bug/1190016](https://bugs.launchpad.net/software-center/+bug/1190016)

---

### Post by deadflowr on 2014-12-24
Don't know, works fine for me

---

### Post by Bucky Ball on 2014-12-25
> **deadflowr said:**
> Don't know, works fine for me

And I. ;)

deadflowr: Does Pipelight allow one to use the latest Flash in Firefox? I just had a look at your link and I'm assuming this is the case ... :-k

---

### Post by deadflowr on 2014-12-25
> **Bucky Ball said:**
> And I. ;)

deadflowr: Does Pipelight allow one to use the latest Flash in Firefox? I just had a look at your link and I'm assuming this is the case ... :-k

Yes.
But as I stated it is non-native to linux as pipelight is a very customized build of wine.
So, basically, it downloads the latest version of flash for Windows.

I've had no problems running it, but who knows about anyone else.
The real pain I have found is that when enabled sometimes it slows down the startup for firefox, as the pipelight looks for a new version and runs a wine configuration setup.
So that can be a small hassle for time to time. You know, try to open the browser to do something quick and then the pipelight stuff starts running and you have to wait a moment.

---

