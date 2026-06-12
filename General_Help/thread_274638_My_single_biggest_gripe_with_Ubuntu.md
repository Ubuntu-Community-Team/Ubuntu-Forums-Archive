---
title: "My single biggest gripe with Ubuntu"
date: 2006-10-10
forum: General Help
---

### Post by jimwillsher on 2006-10-10
Hi all,

Don't get me wrong, I think Ubuntu is a great product. A big thanks to Mark Shuttleworth and all the guys who provide this product.

But I have ONE single gripe, and that is this: Ubuntu is poorly maintained.

There is much hype about how easy it is to install and use, how "it just works", and how it's designed for ANYBODY to use. One of the main "selling points" is how easy it is to install software via APT.

Why, then, is the software so poorly maintained?


The current version of the spamassasin package is 3.1.6, released on 5th October. The current version in the universe repository is 3.1.0. Version 3.1.1 was released on 11th March, so we're running software that's 6 months old (and 6 releases old, one of which was an important security fix).

The current version of the clamav package is 0.88.4, released on 7th August. The current version in the universe repository is 0.88.2. Version 0.88.3 was released on 1st July, so we're running software that's 3 months old (and 3 releases old).

I don't doubt that more released are available in the "unstable" repositories. I also know that I can compile these modules from source. And I also know that there are alternative AV solutions available. But doesn't this destroy the whole mantra of Ubuntu? If I have to start using unstable software, or compiling stuff myself, just to stay current, then all of a sudden Ubuntu is not friendly, and not for beginners.

This is in a product that has long term support (6.06 LTS). Yet in just a matter of months since it was released, it has already fallen behind in the level of software.

I understand that a later version of clamav is available in the Edgy repositories. But Edgy isn't even available yet. Shouldn't the team spend more time concentrating on its current user base rather than its future user base?

Rant over. And comments welcome.



Jim

---

### Post by kerry_s on 2006-10-10
From my understanding is that once it's released the packages get locked except for security updates. Then there is also the backports for some packages to get updated. In doing it that way your not constantly updating things that might break a system. As i'm sure you realize linux is always moving forward and it would be a pain in the developer's butt's to try and fix a system that was stable at the time of release but becomes unstable because of constant updates. I really much prefer how they have seperated the newer stuff for the next release(edgy). I'm using edgy now and let me tell you there are constant updates almost every day, you can never be sure if the next update is going to break the system. If your one of those that want the latest, you should jump over to edgy, but then you must also except the risk and the bugs that come with using the latest. You can also just add edgy repo's and grab that updated package to use, but you still run the risk of it breaking. The chice is really up to you how much risk you want to take just to get the newst.

---

### Post by jimwillsher on 2006-10-10
I hear what you're saying - and many thanks for taking the time to post your thoughts.

I don't use Ubuntu for my desktop, it's for my webserver/mailserver. It's my first line of defence when it comes to cutting down on spam and emails.

I understand the risks in changing package versiosn such as MySql, Perl, Apache etc. But both spamassassin and clamav are "end of the tree" products, there are no packages which are dependent upon these two. So surely there's nothing to break?



Jim

---

### Post by tommcd on 2006-10-10
In debian, and ubuntu, once the OS is released, the packages are "frozen" until the next stable release. This helps to keep the OS stable. Throwing in new packages here and there could cause instablility. Debian is one of the most stable OSs around. NASA has used it for experiments on the space shuttle, because you just can't go into space easily to repeat the experiment if it crashes.
Important security fixes are updated though, in both ubuntu and debian.

---

### Post by PriceChild on 2006-10-10
At the end of the day... the software WILL work!

All security and bugfixes will be applied if you enable those repos.

If you want the latest version.... build it yourself to find out how much trouble you can get in ;)

---

### Post by kerry_s on 2006-10-10
"But both spamassassin and clamav are "end of the tree" products, there are no packages which are dependent upon these two. So surely there's nothing to break?"

Often the updates from version to version is often just slight, you may get a little better function from it, but it doesn't mean the one your using is any less functional. It should still do the job it was intended to do.

---

### Post by nocturn on 2006-10-10
> **tommcd said:**
> In debian, and ubuntu, once the OS is released, the packages are "frozen" until the next stable release. This helps to keep the OS stable. Throwing in new packages here and there could cause instablility. Debian is one of the most stable OSs around. NASA has used it for experiments on the space shuttle, because you just can't go into space easily to repeat the experiment if it crashes.
Important security fixes are updated though, in both ubuntu and debian.

Debian has the volatile repos for things like spamassassin and Clam.  IMO, we need such a system too very urgently!

---

### Post by jimwillsher on 2006-10-10
> **PriceChild said:**
> All security and bugfixes will be applied if you enable those repos.

Which repos would you recommend enabling? My current /etc/apt/sources.list is:

```
#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Many thanks,


Jim

---

### Post by aussieskin on 2006-10-10
My 2 cents worth.

I totally agree with what everyone has said here. I have only just upgraded to Dapper and was using an 'outdated' version of Firefox and thunderbird and various other things on Breezy... Although, the stability of Ubuntu compared to windows is well worth having to use a couple of 'outdated' programs. And I havent even found any real differences in the 'newer' versions yet!

I'm with PriceChild
"At the end of the day... the software WILL work!

All security and bugfixes will be applied if you enable those repos.

If you want the latest version.... build it yourself to find out how much trouble you can get in "

I have also never had any trouble at all with security/virus or any kind of malicious ware, on Dapper or Breezy. I run 2 websites and get quite a lot of spam... but Thunderbird does the trick with weeding those out.

I love Ubuntu.... And I find Dapper to be even more user friendly and easy to install and maintain.. Damn, I would go so far as to say even my old man (who is pretty computer challenged) could install and run it.

Okay my rant is over now...

---

### Post by nocturn on 2006-10-10
For a server, running a stable, LTS version is a good idea.
Yet, if it is a mailserver, up-to-date versions of AV software and Spamassassin are very important, not just the security fixes in them because the fight against spam/malware is an armsrace.

Debian realized this at one point and moved said software to a volatile repo, which is updated even after a stable release has been made.

---

### Post by jimwillsher on 2006-10-10
So...can you advise me how I should update my apt/sources.list file? (or how I can manually, on a per-package basis, check other repos?). It's only clamav and spamassassin I'm after.


Jim

---

### Post by nocturn on 2006-10-10
> **jimwillsher said:**
> So...can you advise me how I should update my apt/sources.list file? (or how I can manually, on a per-package basis, check other repos?). It's only clamav and spamassassin I'm after.


Jim

There are no  newer versions of them out there AFAIK.  MAYBE backports has something, but I don't think so.

---

### Post by jimwillsher on 2006-10-10
Wow, that surprises me. Ubuntu's not quite as "on the ball" as I imagined it was. No updates to spamassassin in over 6 months? Given the current spam wars, that's very surprising.


Jim

---

### Post by kerry_s on 2006-10-10
"Which repos would you recommend enabling? My current /etc/apt/sources.list is:"

Well if you want those updated packages you should uncomment(#) your backports.

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 


Here is my edgy sources.list just in case you want to grab a package here and there.->
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse  

deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse 

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse 

deb http://packages.freecontrib.org/plf/ edgy-plf free non-free 

deb http://kubuntu.org/packages/not-kde-355/ edgy main 

```

plf key->
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -

kubuntu key->
wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
sudo apt-key add kubuntu-packages-jriddell-key.gpg

---

### Post by nocturn on 2006-10-10
> **jimwillsher said:**
> Wow, that surprises me. Ubuntu's not quite as "on the ball" as I imagined it was. No updates to spamassassin in over 6 months? Given the current spam wars, that's very surprising.


Jim

That is because we do not have a seperate policy like Debian volatile.  We treat SA and Clam just like any other Universe program (IMO, both should be in MAIN at the very least).

This is not good for a server configuration obviously

---

### Post by nocturn on 2006-10-10
> **kerry_s said:**
> "Which repos would you recommend enabling? My current /etc/apt/sources.list is:"

Well if you want those updated packages you should uncomment(#) your backports.

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 


Here is my edgy sources.list just in case you want to grab a package here and there.->
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse  

deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse 

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse 

deb http://packages.freecontrib.org/plf/ edgy-plf free non-free 

deb http://kubuntu.org/packages/not-kde-355/ edgy main 

```

plf key->
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -

kubuntu key->
wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
sudo apt-key add kubuntu-packages-jriddell-key.gpg

Keep in mind that the PLF repos are not official and may contain "untrusted" packages.

AFAIK, backports stops for a release once the next is out, so for a server, that is not a good thing.

---

### Post by jimwillsher on 2006-10-10
Okay great. Enabling backportys has at least upgraded spamassassin (and squirrelmail) which is a great start. Not to the latest versions, but I can live with that.

Many thanks all.



Jim

---

### Post by srt4play on 2006-10-10
> **kerry_s said:**
> Here is my edgy sources.list just in case you want to grab a package here and there

If you're going to just grab a .deb here and there, go to packages.ubuntu.com and search for the updated package.  Enabling an entire distribution repo for 1 or 2 packages seems like overkill to me.

---

### Post by jimwillsher on 2006-10-10
You've just completed the puzzle for me. packages.ubuntu.com. Thank you! Just what I was after! :D 

Many thanks,



Jim

---

