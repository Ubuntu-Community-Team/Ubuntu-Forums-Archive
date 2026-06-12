---
title: "Installing 10.04"
date: 2015-01-12
forum: General Help
---

### Post by kinnu on 2015-01-12
Greetings,
 
Last week Dec 2014,  I downloaded  [http://old-releases.ubuntu.com/releases/10.04.4/ubuntu-10.04.4-desktop-i386.iso]("http://old-releases.ubuntu.com/releases/10.04.3/ubuntu-10.04.4-desktop-i386.iso")

 but

 
$ sha1sum ubuntu-10.04.4-desktop-i386.iso
sha1sum: ubuntu-10.04.4-desktop-i386.iso: Input/output error

 $ md5sum ubuntu-10.04.4-desktop-i386.iso
md5sum: ubuntu-10.04.4-desktop-i386.iso: Input/output error

 
ls -l reports ubuntu-10.04.4-desktop-i386.iso to be 728150016 bytes.

 
It also failed to burn to media. I downloaded again with same  results. Two different PCs with different OSs report the same. So either something is wrong during download or something is wrong with the file. Other downloads working happily. Could someone else to try running md5sum on this file. That would help narrow down the problem. 

 
Any suggestions on how to contact the maintainer of this repository, and to another reliable repository for a healthy (different) copy of this iso greatly appreciated.

Thanks



PS. 
The webpage [http://old-releases.ubuntu.com/releases/10.04.4/]("http://old-releases.ubuntu.com/releases/10.04.3/ubuntu-10.04.4-desktop-i386.iso") is titled Ubuntu 10.04.4 LTS (Lucid Lynx) and this file is listed as

 ubuntu-10.04.4-desktop-i386.iso            14-Feb-2012 11:51  694M  Ubuntu 10.04.4 (Lucid Lynx)

---

### Post by corneldardenjr-y on 2015-01-12
Why do you want 10.04?

---

### Post by QIII on 2015-01-12
Hello!

Please read [this]("http://ubuntuforums.org/showthread.php?t=2229730") for the Forums Staff recommendations regarding the use of EOL releases of Ubuntu.

We would prefer that the volunteers here spend their valuable time helping people with problems with currently supported releases.

Please consider using one of the currently supported releases:  12.04, 14.04 and 14.10.

Thanks.

---

### Post by robsoles on 2015-01-12
Shifting focus from kinnu wanting a copy of my preferred release of Ubuntu, perhaps the issue can be seen as 'a file on a server referenced as $.ubuntu.com appears to have problems; please can someone download it and test it so that kinnu can determine if it is them or the copy on the server is not OK.'

---

### Post by Bucky Ball on 2015-01-12
Unsure what the point would be in downloading, installing and testing an unsupported release. As 10.04 LTS is EOL for the desktop it hasn't had updates in awhile and may be broken, for various reasons, on different machines. It could also be a possible security risk if the machine is online. kinnu has also tested on two different machines with the same result. 

@kinnu: Welcome. Please refer to QIII's comments, link and recommendations in post #3. Good luck. ;)

---

### Post by zombifier25 on 2015-01-12
I'm downloading the image and will report back in an hour or so with the md5sum result.

Still, why do you want 10.04 anyway? It (the desktop version at least) is dead, with outdated software, bugs and security holes. Do you prefer the GUI? There's Ubuntu MATE, which has the MATE desktop which is forked from GNOME 2.

EDIT: Results are in. The md5sum test works perfectly fine on my part. I would presume the image I downloaded would work fine as well.

---

### Post by robsoles on 2015-01-12
I've downloaded the file just now, using the link you provide kinnu, it booted a VM without blinking and when I chose 'Try Ubuntu' it delivered me to a usable desktop fairly quickly.

The file on their server is OK. Something must be doing something nasty to it on the way to you. "Defensive' software can be configured badly enough to modify files during download without alerting anybody; usually by a user selecting not to be nagged with piffling small details :)


Just for the 'Upgrade or risk extermination crew' around here:

One of my labels at work is 'IT Admin' and I manage a grand total of 9 computers (inclusive server + phones, modem, usual sundry) for them.

Myself and the Chief Electronics Engineer both stayed back on Ubuntu 10.04 while the owner of the business insisted on being upgraded to Ubuntu 12.04, when it came out, and I figured the other administrative fellow may as well be a guinea pig for us as well when he finally gave up XP.

(1) C.EE and I are still recieving updates, or at least I just gave in and accepted a bunch that have accumulated in the last couple of months earlier today. C.EE just had me do the 'I just updated, did it break anything?' post check he makes me do after accepting udpates on his system last Wednesday.

(2) Owner of the business needed assistance with his PC for more than 10% of my day for the first month after insisting on taking the 'upgrade'. I have repaired 'google-maps' and 'skype' and other fiddlies quite a few times since. I still haven't gotten a suggestion from him that he has managed to comprehend the way 'spaces' works on his PC now, he had been using 10.04 for two years previously with barely a peep out of him and he could use spaces too!

(3) Administrative fellow hadn't used 10.04, came straight from XP into Ubuntu 12.04 and he liked it at first. The day since he started using it that he doesn't mention what a pig libre-office is is rare. I have to fix 'skype' and various other fiddlies on his PC nearly as regularly as the Owner's PC. Lately it is looking like his (rather misguided) love for 'google-chrome' is locking his system up anything from completely and utterly locked through to just badly unresponsive - maybe when I finally find the log with relevant entries in it that will turn out to be something else altogether but I just don't trust Chrome.

(4) I barely hear a peep out of myself or our C.EE.


I've been trying the new releases for general usability (particularly in terms of who I know (who relies on me) would be using it) and just simply chosen not to advance myself, nor recommend advancing to my work (or other 'dependents'), due to how Unity works and how Gnome does not (*in fairness, did not - while since I checked) work anywhere near as good in all LTS releases since 10.04

I begged my boss not to make me upgrade his machine from 10.04 without giving me the opportunity to show it to him in a VM (inclusive of testing a few of his favorite apps) but he didn't get where he is sitting around listening to dills like me I guess.


So, Here's a question for you if you are on the cutting edge of Ubuntu releases: Do you rely on your ability to be productive on your PC for your sole source of income?

---

### Post by Bucky Ball on 2015-01-12
> **robsoles said:**
> Upgrade or risk extermination ...


Don't think we're saying that, and people are free to use whatever release they want. The point is, if you are using an unsupported release you probably won't find much support in realtime on these forums (and probably others) if/when things go wrong with it as 99.9% of people here are using supported releases and haven't used 10.04 desktop in quite some time. I don't remember a lot about it and people tend to forget as they move on (especially if they move on to Unity or other desktop environments). A lot has changed.

There are plenty of old posts and pages to trawl through, so if a user is happy with outdated apps and possible security vulnerability if their machine is online, then go for it, I say.

But we digress. Carry on and good luck. ;)

PS: 10.04 LTS server version is still supported until April this year. ALL LTS releases are now supported for five years, desktop or server version.

---

### Post by Elfy on 2015-01-12
Downloading 10.04 specifically is a whole lot different to having had it in 2010 and not having kept up with releases.

@kinnu - get a supported version and start with that.

Thread Closed.

---

