---
title: "How long will Feisty last as a solid operating system?"
date: 2007-06-20
forum: General Help
---

### Post by shanest on 2007-06-20
I am about to purchase a computer for college.  I am very strongly considering the Raven x60 tablet from EmperorLinux.  It is simply a Lenovo x60 tablet that comes configured with a Linux distro of your choice that is very highly customized (they use their own modified kernel as well) to work with the laptop/tablet.

My only issue is that since it is such a highly customized installation of Ubuntu 7.0.4 (the OS I would choose to run), it will probably be very difficult/pointless to upgrade when new releases come out.  Therefore, I would almost be "locked in" to the OS I choose upon ordering the computer.

Will Ubuntu 7.0.4 be able to last me for 3-4, or even some more, years?  Could I use it through my entire college career?

---

### Post by empthollow on 2007-06-20
feisty is supported for 1 year technically, however packages are available for a at least 1 year, probably and even longer time after that.  i would like to point out however if you download the alternate upgrade cd or do it over network with upgrade manager it makes the distro upgrade pretty painless and you don't lose any of your customizations. then next distro to be released by ubuntu will be LTS or Long Term Support which means it is well supported for 3 years, 6.06 dapper is the current LTS distro and technically a bit more stable although i have found feisty to be quite stable as well.  this distro will not be released for about a year as feisty was just released.  if you think you can handle one distro upgrade through college you will be set for at least 4 years.

---

### Post by justin whitaker on 2007-06-20
> **shanest said:**
> I am about to purchase a computer for college.  I am very strongly considering the Raven x60 tablet from EmperorLinux.  It is simply a Lenovo x60 tablet that comes configured with a Linux distro of your choice that is very highly customized (they use their own modified kernel as well) to work with the laptop/tablet.

My only issue is that since it is such a highly customized installation of Ubuntu 7.0.4 (the OS I would choose to run), it will probably be very difficult/pointless to upgrade when new releases come out.  Therefore, I would almost be "locked in" to the OS I choose upon ordering the computer.

Will Ubuntu 7.0.4 be able to last me for 3-4, or even some more, years?  Could I use it through my entire college career?

Yes and No. Any Linux distribution will go through many iterations in 3-4 years....officially, Feisty is NOT a long term support (LTS) version of Ubuntu. Once Gutsy Gibbon is out, then Feisty may see security updates, that is about it. 

That said, you could probably run it safely and happily for that period of time....but at some point, you are going to want to update the core applications and OS. 

Do they offer an update/upgrade service option?

---

### Post by mdurham on 2007-06-20
To answer that question correctly Feisty would have to be 'solid'. It seems pretty flaky (not solid) to me.
Cheers, Mike

---

### Post by shanest on 2007-06-20
> **empthollow said:**
> feisty is supported for 1 year technically, however packages are available for a at least 1 year, probably and even longer time after that.  i would like to point out however if you download the alternate upgrade cd or do it over network with upgrade manager it makes the distro upgrade pretty painless and you don't lose any of your customizations. then next distro to be released by ubuntu will be LTS or Long Term Support which means it is well supported for 3 years, 6.06 dapper is the current LTS distro and technically a bit more stable although i have found feisty to be quite stable as well.  this distro will not be released for about a year as feisty was just released.  if you think you can handle one distro upgrade through college you will be set for at least 4 years.

How exactly would an upgrade be painless?  If core files are changed, but an upgrade doesn't undo the changes, then how would it be an upgrade at all?  There's some sort of paradox there.

EmperorLinux is working on offering an upgrade plan, but it's unclear if/when that will become official.  Would a distro like Fedora be a safer bet?

---

### Post by raul_ on 2007-06-20
You don't lose your files, if that's what your asking.

---

### Post by southernman on 2007-06-21
> **empthollow said:**
> this distro will not be released for about a year as feisty was just released.  

You are WRONG! (sorry it's an inside joke with my fellow LUG members) 

Gusty is due to release in October this year.

[Link to Gusty Gibbons Release Notes]("http://www.ubuntu.com/testing/tribe1")

To the OP, I vote for Feisty being very stable. If it were me buying a new laptop, I'd buy one without an OS and do my own install, tweaking, and customizing.

Modified kernels locks you out of public updates. You would be at the mercy of your merchant for upgrades. Sounds like the upgrade plan would cost more in addition to the purchase price.

Best of luck with the route you choose best for you. May your college days be ummmm educational. ;)

---

### Post by shanest on 2007-06-21
I've considered doing my own install.  However, I am rather unexperienced in Linux and am not sure that that is the best route for me.  Also, I am about 99% sure that I am ordering a tablet PC, which requires some fairly advanced tweaking.  

What kind of upgrades does a custom kernel lock me out of?  (They do offer their kernel for free publicly, so they can't charge for upgrades to that.)

---

### Post by southernman on 2007-06-21
> **shanest said:**
> I've considered doing my own install.  However, I am rather unexperienced in Linux and am not sure that that is the best route for me.  Also, I am about 99% sure that I am ordering a tablet PC, which requires some fairly advanced tweaking.  

What kind of upgrades does a custom kernel lock me out of?  (They do offer their kernel for free publicly, so they can't charge for upgrades to that.)Ok, I understand now. 

I may have been totally wrong about "locking" you out of updates from Ubuntu. It may be that you could indeed install the updates, but it would bork your OS being it having a modified kernel.

Sorry if my original comment (or this one) is incorrect. Really think this one is more on target though.

*leaves for the back waiting area of the peanut gallery now*

---

### Post by foxmulder881 on 2007-06-21
Despite users saying that Feisty is fairly solid, I have a different view...

I have already reinstalled Feisty once since it was released. I had major problems that nobody could seem to fix or know how to. I even filed a bug report at Launchpad and got no replies. I was reluctant to reinstall Feisty at all and actually was going to reinstall Dapper. But something inside me told me to give Feisty another chance to prove itself. For how long, I don't know...

For a 'rock solid' install, I'd still happily suggest Dapper.

---

### Post by freund on 2007-06-25
I found that for my Lenovo X60 tablet that Feisty was the better than Edgy. Almost everything seemed to work out of the box.  There are a few tweaks to get some buttons working and conveniences that can be added. I just did a search at this form "X60 tablet" and most of the solutions are posted and are relevantly easy to follow.  

From my experience I had flawless upgrades, over the network, at the push of a button, from Edgy to Feisty on several of my systems that range from AMD 64 to Piii.  Now there could be hitches in some of the software and kernel modules because they are constantly being modified.  But what I do is refrain from upgrading until 2-3 months after a new distro comes out so that most of the bugs get fixed.

At the beginning of my Linux venture, Red Hat 6.0,  the learning curve was steep, but with time and  the improvement of the software it became less painful.

I also found that Ubuntu is lighting fast compared to XP on the X60.

check out
[http://groundstate.ca/tabletsoft](http://groundstate.ca/tabletsoft)

I use
xournal (pdf anotate)
and
a small virtual keyboard for KDE, Kavier at:
Get it at : [http://sebastien.huss.free.fr/?q=klavier](http://sebastien.huss.free.fr/?q=klavier)

al

---

### Post by bcw on 2007-06-26
> **shanest said:**
> I am about to purchase a computer for college.  I am very strongly considering the Raven x60 tablet from EmperorLinux.  It is simply a Lenovo x60 tablet that comes configured with a Linux distro of your choice that is very highly customized (they use their own modified kernel as well) to work with the laptop/tablet.

My only issue is that since it is such a highly customized installation of Ubuntu 7.0.4 (the OS I would choose to run), it will probably be very difficult/pointless to upgrade when new releases come out.  Therefore, I would almost be "locked in" to the OS I choose upon ordering the computer.

Will Ubuntu 7.0.4 be able to last me for 3-4, or even some more, years?  Could I use it through my entire college career?

I would be asking EmperorLinux what their OS support policy is.  Do they guarantee access to the newer version they develop for the distro when the distro itself upgrades?  They are subject to the same upgrade/support issue you are, and therefore will be developing a newer version based on the new distro version.  Do they provide that for you when it is released?

Cheers,
Bret

---

### Post by freund on 2007-06-29
Other useful configuration sites for X60 tablet that could help are:
[http://www.thinkwiki.org/wiki/Category:X60_Tablet](http://www.thinkwiki.org/wiki/Category:X60_Tablet)
[http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/)

Typically they are constantly updated withe new kernel/OS releases.

al

---

### Post by darksidedude on 2007-09-12
What I would do in your position would be to just wipe out there "Modified" version and just use the "consumer" edition, but thats just me =)

---

### Post by atlfalcons866 on 2007-09-12
each ubuntu release is supported for 18 months

---

### Post by the yawner on 2007-09-13
Uhm... What exactly are the modifications?

---

