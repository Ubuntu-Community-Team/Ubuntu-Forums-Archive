---
title: "Why are repository versions of software always out of date?"
date: 2008-06-02
forum: General Help
---

### Post by Kiri on 2008-06-02
If you go to the homepage of almost any software that you find in the repositories you will find more up to date versions available. Not only betas or whatnot, but full releases. Doesn't it kind of defeat the purpose of the repositories if they are not up to date?

---

### Post by loell on 2008-06-02
stable repositories must always freeze at some point, so as to avoid breakage .

---

### Post by sdennie on 2008-06-02
Primarily for stability.  There is no reason to install the latest and greatest unless you really need it.  Having something that is known to work and simply applying updates to it is much better for maintaining a system than grabbing every new version of a piece of software.

---

### Post by Tomatz on 2008-06-02
> **vor said:**
> Primarily for stability.  There is no reason to install the latest and greatest unless you really need it.  Having something that is known to work and simply applying updates to it is much better for maintaining a system than grabbing every new version of a piece of software.


Exactly!

I still use gutsy and i wont install hardy for another few months because i prefer stability ;)

---

### Post by sdennie on 2008-06-02
> **Tomatz said:**
> Exactly!

I still use gutsy and i wont install hardy for another few months because i prefer stability ;)

Haha.  I swore I'd never upgrade from Gutsy because it worked just fine.  I then upgraded to Hardy in the beta stages.  User impatience is probably one of the primary motivators for not dropping in new versions of packages.

---

### Post by kpkeerthi on 2008-06-02
> **Kiri said:**
> If you go to the homepage of almost any software that you find in the repositories you will find more up to date versions available. Not only betas or whatnot, but full releases. Doesn't it kind of defeat the purpose of the repositories if they are not up to date?
Because ubuntu is not a rolling release distribution.

Ubuntu does not continuosly updates the packages in its repository. The software versions are frozen when a new Ubuntu version is announced. Once released, the packages remain the same until the next Ubuntu version is released. So you have to wait for 6 months to get updated packages. However some packages are made available via the backports repository.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by tact on 2008-06-02
New versions of software that is already in the repos need to be checked and packaged properly before being updated/added to the repos and pushed out as part of updates (none of us like getting broken updates huh)...  its a thankless and heartless neverending job prepping those packages.. what..  some 12000 or more now - how many hundreds a month need updating?

You don't think the job is done by trained monkeys who work for pats on the head do you?  If so perhaps we petition canonical to get more monkeys so, dammit, we dont have to wait.

Or we could volunteer to assist?  You first...  

Cheers

---

### Post by bingoUV on 2008-06-02
so "apt-get update" is useless?

Feisty came with approximately 2.6.17 kernel. Updating after some days gave me I think 2.6.18. What was that?

Of course new versions of software are made available for the same release without the backports repository.

One reason I can think of for Kiri is, that since packaging software for Ubuntu is "work", it takes time like all other work. Some changes need to be made to give it Ubuntu feel. Test it so that it works well with the whole distribution. Theme if it does not respect the gnome/gtk theme. Then security updates should take priority, so software with general feature addition might take even longer.

---

### Post by ingvildr on 2008-06-02
This is probably one of the main reasons I tend to use fedora a little more. I mean fedora does freeze its repositories just like Ubuntu but they aren't so tight on the updates front, so they will actually let bug fix releases in as updates and some minor enhancement releases. 

So for example I think fedora 9 was released with the 2.6.25 kernel but they are now on 2.6.25.3, transmission is now 1.11 when it was 1.06, banshee is 0.99.1 with 0.99.2 and 0.99.3 in proposed. I can understand Ubuntu wanting to keep things stable and not introduce new bugs but let us have a little fun :D

---

### Post by sdennie on 2008-06-02
> **ingvildr said:**
> This is probably one of the main reasons I tend to use fedora a little more. I mean fedora does freeze its repositories just like Ubuntu but they aren't so tight on the updates front, so they will actually let bug fix releases in as updates and some minor enhancement releases. 

So for example I think fedora 9 was released with the 2.6.25 kernel but they are now on 2.6.25.3, transmission is now 1.11 when it was 1.06, banshee is 0.99.1 with 0.99.2 and 0.99.3 in proposed. I can understand Ubuntu wanting to keep things stable and not introduce new bugs but let us have a little fun :D

You are right and wrong.  The Ubuntu kernel claims to be 2.6.24 but is actually something like 2.6.24.4 with a billion patches that make it a very up to date kernel.  As annoying as it may sometimes seem, package stability really is a good thing.

Edit:
It's also not very hard to find a super up to date package for something or grab it from svn/git/cvs and build it and use checkinstall to build and install it without horrible effects.  One of the reasons I use Ubuntu is because everything works and then I'm free to destroy my system however I see fit.  I'm quite happy that they keep things working.  ;)

---

### Post by mcduck on 2008-06-02
> **bingoUV said:**
> so "apt-get update" is useless?

No, it's not useless. It will get you all the security updates, and if you have enabled the backports-repository, you sometimes even get more up-to-date versions (as long as they are relatively simple packages to backport & check for compatibility errors, and don't have too many dependencies).

After package freeze during the development of a certain Ubuntu version the package versions are frozen, but of course all security updates and fixes for seriouus bugs are still applied. This won't give you the latest and greates versions, but instead you get a nice compromise between new software and stability.

---

### Post by Kiri on 2008-06-02
Thank you for all the responses. The logic behind it makes sense.
I was just wondering because it often seems to be the case that I need to go looking for deb packages or try to compile myself (which I am not yet very familiar with) to be able to use newer versions of most software. 
But I can see the reasoning behind opting for proven stability

---

### Post by Seisen on 2008-06-02
If you really want to see some packages that are more outdated than Ubuntu check out Debain Etch some of those packages are way behind.

---

