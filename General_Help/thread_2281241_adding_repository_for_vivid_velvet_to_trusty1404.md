---
title: "adding repository for vivid velvet to trusty1404"
date: 2015-06-05
forum: General Help
---

### Post by Nosphky on 2015-06-05
I'm using UbuntuStudio 1404 Trusty and one of my main applications is getting rather outdated.  I see on launchpad that the current stable release, vivid velvet has the latest version of this application.  I've already tried it out on a debian machine using jessie but taking the application from sid and it handles my files well.

What is the form of words for adding the vivid velvet repository to the repo list in Trusty software and updates dialogue ?

---

### Post by deadflowr on 2015-06-05
Nothing good ever comes from trying to run a mixed-repository system.
What's the package, anyway?

---

### Post by Nosphky on 2015-06-05
Well thank-you deadflowr for that downbeat message.  I've used PPA's for a few applications without trouble so far.  I know there are risks but I wouldn't agree that 'nothing good' ever comes from these attempts..

The package in question is Inkscape, the vector drawing tool which I have used quite a lot for preparation of illustrations.   1404 Trusty only has 0.48.4  I tried mixed-repository on a portable using debian jessie and taking Inkscape 0.91.4 from sid and this worked fine. 

So I thought I'd have a go with trusty / vivid if I can.

---

### Post by QDR06VV9 on 2015-06-05
Don't kill the messenger I see very sound advice coming from deadflowr so you have been warned.
You May or Maynot have Ill effects depending if all dependencies are in fact in place, and as things get their updates or upgrades well there is the possibiltiy
It will kill your OS or faulty apps on and on.
Regards

---

### Post by howefield on 2015-06-05
Why don't you use the inkscape ppa for Trusty and forget the nonsense about mixed repositories :) ?

---

### Post by Nosphky on 2015-06-05
Thank you, howefield.  Your reply made me look again for a PPA link.  

I'm not the greatest explorer of websites and I've failed to refind stuff a 100 times on Ubuntu, launchpad and debian websites even when I know it exists.   And I couldn't see any PPA link on launchpad for ubuntu inkscape but using the inkscape's own website, I found a PPA Ubuntu reference which took me to another launchpad page - and there it is.

I have no objection to using a PPA especially if it involves latest version backported to Trusty.  I'll investigate further over the weekend and see if that gets me the 0.91 version.

And excuse me, please, if I don't go along completely with your expression 'nonsense about mixed repositories'.  I appreciate the risks and I've already broken distros on my old laptop.  That's where I experiment and haven't had a lot of breakages - some.  ;)

---

### Post by howefield on 2015-06-05
> **Nosphky said:**
> And excuse me, please, if I don't go along completely with your expression 'nonsense about mixed repositories'.  I appreciate the risks and I've already broken distros on my old laptop.  That's where I experiment and haven't had a lot of breakages - some.  ;)

As is your right to do so, your system, your choices :)

But also the right of others to point out how it may end, if nothing else to ensure casual readers are made aware that it is not good practice.

Btw, you'll get 0.91.0+47~ubuntu14.04.1 by using the inkscape ppa.

---

### Post by grahammechanical on 2015-06-05
I have used a trusty PPA to install an application on a vivid install of Ubuntu. But there is a big difference between a PPA and a main Ubuntu repository. What repository is Inkscape in? Universe? So, your system will have as software sources a trusty universe repository and a vivid universe repository. I think and update/upgrade would start upgrading all the installed packages from that repository along with the dependencies of those installed packages.

I suggest that the PPA is the better way to do this.

Regards.

---

### Post by Nosphky on 2015-06-06
OK, thanks everyone.  Job done, I've now got the PPA updated version of Inkscape for Trusty v.0.91.0+47~ubuntu14.04.1 and it seems to be working fine.

I'm very happy to use PPA's (but I'm also willing to experiment) but I guess my basic problem is not finding it very easy to locate stuff on Launchpad.   Before starting this thread, I had made a search but without success.  I had examined these 2 pages :

[https://launchpad.net/inkscape](https://launchpad.net/inkscape)
[https://launchpad.net/inkscape-project](https://launchpad.net/inkscape-project) 

without seeing any indication of a PPA.   But when howefield's reply affirmed the existence of a PPA I started again from inkscape.org and this lead me to :  

[https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable](https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable)  

where I did find the PPA

It's a pity that the page with the PPA wasn't referenced from one of the other 2 pages - or maybe it was and I couldn't see it.

Anyway - job done and thanks again for the help.

---

### Post by howefield on 2015-06-06
Glad you got it sorted :)

To be fair, it is very easy to get to the relevant page from the first of your links posted above.

---

### Post by Nosphky on 2015-06-06
> **howefield said:**
> 

To be fair, it is very easy to get to the relevant page from the first of your links posted above.

In the light of your comment, I've reexamined the links from   launchpad.net/inkscape  trying to find an easy path to  

launchpad.net/~inkscape.dev/+archive/ubuntu/stable 

 Going down one level on all the launchpad links on that page which are not source code related and which don't go to inkscape.org or sourceforge, I didn't find any reference to PPA's.  Going down to a second level via the link to the 0.91.x branch, I did manage to get to the /~inkscape-dev/ part of the link but from there there I could not identify an easy way of getting to /+archive/ and again no direct mention of PPAs.

Digging down more than two levels without finding a PPA mention doesn't  correspond for me with "very easy" and so I'm sure there's something here that I haven't understood or I've missed completely.

I'm quite certain the site has been designed logically and I would appreciate it if you could share some info which would probably enable me 
to locate a PPA faster for other packages in the future.  Thanks.

---

### Post by QDR06VV9 on 2015-06-06
> **Nosphky said:**
> In the light of your comment, I've reexamined the links from   launchpad.net/inkscape  trying to find an easy path to  

launchpad.net/~inkscape.dev/+archive/ubuntu/stable 

 Going down one level on all the launchpad links on that page which are not source code related and which don't go to inkscape.org or sourceforge, I didn't find any reference to PPA's.  Going down to a second level via the link to the 0.91.x branch, I did manage to get to the /~inkscape-dev/ part of the link but from there there I could not identify an easy way of getting to /+archive/ and again no direct mention of PPAs.

Digging down more than two levels without finding a PPA mention doesn't  correspond for me with "very easy" and so I'm sure there's something here that I haven't understood or I've missed completely.

I'm quite certain the site has been designed logically and I would appreciate it if you could share some info which would probably enable me 
to locate a PPA faster for other packages in the future.  Thanks.

To decide which version of the PPA you will see a line _Technical details about this PPA_ in Green
Click on that line.
It will then have a drop down box with the various versions of Ubuntu IE 15.04 14.10 14.04
Etc.
If you want the easy way to add that PPA fire up your terminal and paste the code below.
```
sudo add-apt-repository ppa:inkscape.dev/stable
```

That was for the Stable Release or version 0.91.0+37
There is also the trunk or Development PPA This Below is their Discription

> The Inkscape Trunk PPA is intended to provide trunk builds for users who like the bleeding edge. We do not provide official support (you may be able to get support in our irc channel though) for these builds. As always bug reports and feedback are both appreciated. Note, we always try to keep trunk as stable as possible as our developers and testers use it for production work.
And That Version is 1:0.48+devel
To Select that PPA Again in terminal
```
sudo add-apt-repository ppa:inkscape.dev/trunk 
```

And then Update and Upgrade
```
sudo apt-get update && sudo apt-get upgrade
```

**I would not add both PPAs one or the other**.
Or remove one and try another.
Regards

---

### Post by monkeybrain20122 on 2015-06-06
> **Nosphky said:**
> OK, thanks everyone.  Job done, I've now got the PPA updated version of Inkscape for Trusty v.0.91.0+47~ubuntu14.04.1 and it seems to be working fine.

I'm very happy to use PPA's (but I'm also willing to experiment) but I guess my basic problem is not finding it very easy to locate stuff on Launchpad.   Before starting this thread, I had made a search but without success.  I had examined these 2 pages :

[https://launchpad.net/inkscape](https://launchpad.net/inkscape)
[https://launchpad.net/inkscape-project](https://launchpad.net/inkscape-project) 

without seeing any indication of a PPA.   But when howefield's reply affirmed the existence of a PPA I started again from inkscape.org and this lead me to :  

[https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable](https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable)  

where I did find the PPA

It's a pity that the page with the PPA wasn't referenced from one of the other 2 pages - or maybe it was and I couldn't see it.

Anyway - job done and thanks again for the help.

I usually find them by googling "package name, launchpad packages" . For example, searching "inkscape, launchpad packages" shows [https://launchpad.net/ubuntu/+source/inkscape](https://launchpad.net/ubuntu/+source/inkscape) click "other versions of 'inkscape' in untrusted archives" will show you three ppas with inkscape and clicking the bottom "other untrusted versions of inkscape" again will show you all ppas with inkscape.

I agree that the supposed risks of ppa is overblown. if I don't use any ppas I may as well use Debian.

---

