---
title: "Ubuntu 13.04 -- Broke my Software Center :("
date: 2013-08-01
forum: General Help
---

### Post by Gnawnsense on 2013-08-01
Hello everyone!

Alright, so, I ran into an odd problem today. Hadn't added any new PPA sources or installed any new packages in the last few days and randomly my Software Center began to close immediately upon launch, without an error.

After a session with Google and checking out a few AskUbuntu and forum threads and none of the solutions working, I came across a few people who were having the exact problem. The general consensus across these AskUbuntu inquiries were that a quick uninstall=>reinstall would fix the issue painlessly, so that's exactly what I sent out to do.

So the first thing I did, like the suggestions said, was throw out a ***sudo apt-get remove software-center***. One thing I noticed that most people hadn't brought up, but a few had (and reported no issues), was that removing ***software-center*** also wanted to remove ***ubuntu-desktop***. But, people had reported they had no issue with the uninstall and reinstall process, so I continued.

After the uninstall finished, I went ahead and did the ***sudo apt-get install software-center*** and this is what happened:

[IMG]http://screencloud.net//img/screenshots/5d95f244932045ddb09daa7a67c7fb75.png[/IMG] 

So, I tried a ***sudo apt-get -f install software-center*** and got the same problem. 

So what did I do? Tried to see if I could install the ***ubuntu-desktop*** package that was removed to see if maybe that would help things along and got this:

[IMG]http://screencloud.net//img/screenshots/0e6bed5c8d2e54b5af548da1b9aceed0.png[/IMG]

After this failed, I tried installing all the missing packages manually from the first screenshot, but when I tried to install any of them it indicates I already have them, like this:

[IMG]http://screencloud.net//img/screenshots/d2838acf0753e6d2837c53c246c4197a.png[/IMG]

So needless to say I tried ***sudo dpkg --configure -a*** and ***sudo apt-get -f install*** to no avail. I can't think of any other solutions at this point, either.

Any assistance would be appreciated.

---

### Post by GwL3eNC on 2013-08-01
Hi, i am not shure but is 
sudo apt-get -f install software-center 

right to solve depens. Also i think sudo apt-get install -f isnt right or?Please try yust 

sudo apt-get -f install**

---

### Post by Gnawnsense on 2013-08-01
> **GwL3eNC said:**
> Hi, i am not shure but is 
sudo apt-get -f install software-center 

right to solve depens. Also i think sudo apt-get install -f isnt right or?Please try yust 

sudo apt-get -f install

Thanks for the reply!

That's what I originally meant. Here's what I get when I try ***sudo apt-get -f install***:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by GwL3eNC on 2013-08-01
And whats on 

sudo apt-get install --reinstall software-center

---

### Post by Gnawnsense on 2013-08-01
> **GwL3eNC said:**
> And whats on 

sudo apt-get install --reinstall software-center

Just got this:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 software-center : Depends: python-gi (>= 3.4.0-1ubuntu0.1) but it is not going to be installed
                   Depends: python-gi-cairo but it is not going to be installed
                   Depends: python-aptdaemon (>= 0.40) but it is not going to be installed
                   Depends: python-aptdaemon.gtk3widgets but it is not going to be installed
                   Depends: oneconf (>= 0.2.6) but it is not going to be installed
                   Depends: python-oneconf (>= 0.3) but it is not going to be installed or
                            oneconf (< 0.3) but it is not going to be installed
                   Recommends: sessioninstaller but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

All of those packages listed above are already installed, as well.

---

### Post by GwL3eNC on 2013-08-01
Sorry, i'm self a bit newbie. but you got yust 

sudo apt-get install software-center

in your first post. I miss the option --reinstall

---

### Post by Gnawnsense on 2013-08-01
> **GwL3eNC said:**
> Sorry, i'm self a bit newbie. but you got yust 

sudo apt-get install software-center

in your first post. I miss the option --reinstall

No worries! Any help trying to get this figured out is appreciated :)

---

### Post by GwL3eNC on 2013-08-01
I found that

[h=3]Fixing dependencies[/h] **dpkg --configure --pending**  If dpkg quits with an error while [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]ing try running this to configure the packages that were already unpacked. Then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade -f[/FONT], and then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]  again. Repeat as needed. This usually resolves most dependency problems  (also, if it mentions a specific package for some reason, you might  want to try installing or removing that package)

 [B]apt-get install -f 
 apt-get upgrade -f 
 apt-get dist-upgrade -f[/B]  

Attempt to fix dependencies while doing one of the above. Note that [FONT=FIXED]apt-get install -f[/FONT] does not require a <package> argument.
[http://www.cyberciti.biz/ref/apt-dpkg-ref.html](http://www.cyberciti.biz/ref/apt-dpkg-ref.html)

---

### Post by Gnawnsense on 2013-08-01
I think at this point I'm going to go ahead and just put a clean install of 13.04 on my machine since it's basically just a clean install now. I'm just out the hour or two getting everything reconfigured and installed again.

---

### Post by Gnawnsense on 2013-08-01
> **GwL3eNC said:**
> I found that

**Fixing dependencies**

 **dpkg --configure --pending**  If dpkg quits with an error while [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]ing try running this to configure the packages that were already unpacked. Then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade -f[/FONT], and then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]  again. Repeat as needed. This usually resolves most dependency problems  (also, if it mentions a specific package for some reason, you might  want to try installing or removing that package)

 [B]apt-get install -f 
 apt-get upgrade -f 
 apt-get dist-upgrade -f[/B]  

Attempt to fix dependencies while doing one of the above. Note that [FONT=FIXED]apt-get install -f[/FONT] does not require a <package> argument.
[http://www.cyberciti.biz/ref/apt-dpkg-ref.html](http://www.cyberciti.biz/ref/apt-dpkg-ref.html)

Ahh, thanks for finding this. It didn't work out for my issue this time, but I think it might of if I wouldn't of kept dinking around with things.

---

### Post by Paww on 2013-08-01
Can you do[COLOR=#000000] *dpkg --configure -a* ?[/COLOR]

---

