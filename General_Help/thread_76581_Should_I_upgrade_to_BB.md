---
title: "Should I upgrade to BB?"
date: 2005-10-15
forum: General Help
---

### Post by Sham on 2005-10-15
Hi all,

I use Kubuntu at work, so I really need my machine to be rock solid (no time to fix problems ;)  ). My Hoary box is running really well, no problems at all.

Should I do the upgrade, or hangfire for a bit?

Cheers

---

### Post by Sirin on 2005-10-15
Well, for the latest updates (software and security), I'd recommend that you upgrade. It contains the very latest stable version of KDE, with the choice to also add the very latest version of Gnome, too. It brings your system more protection against hackers and malware. Since KDE and it's large community of developers announce bug fixes in it's latest release, your system should work even better than Hoary ;) .

---

### Post by DJ_Max on 2005-10-15
Really no need to upgrade unless you're missing some features.

> It brings your system more protection against hackers and malware.
Never heard of malware on linux, even so, if it was possible using Ubuntu repo's would squash that, and besides, Hoary is still getting security updates untill Oct. 2006. Heck, warty is getting the until April 06'.

---

### Post by Sham on 2005-10-15
Thanks for the input guys. I might try and locate a testbox for me to use first. I seriously can't afford to break this box at the moment :???:

---

### Post by Firetech on 2005-10-15
Upgrading worked fine for me, I just had some issues with stuff I had compiled myself and some apt-get issues (had too run dist-upgrade a few times because dpkg encountered errors with same files in multiple archives some times... If you have "manually" compiled stuff, remember to recompile them with GCC 4. ("make clean" first, else you _will_ encounter strange errors...)

Just rememember that if you do use a testbox, it might not be the same. A fresh install is always cleaner than a massively upgraded one.

---

### Post by matthew on 2005-10-15
[quote=Sham]Thanks for the input guys. I might try and locate a testbox for me to use first. I seriously can't afford to break this box at the moment :???:[/quote]
I think that's a good plan. As they say, "If it's not broken, don't fix it." Now if I could only learn to take my own advice... :)

---

### Post by gat on 2005-10-15
After reading all the great reviews, I couldn't resist trying the Breezy upgrade.

I'm pretty much a noob, but "change hoary to breezy in sources.list, then sudo apt-get dist-upgrade" sounded easy enough...  

I had been using Hoary on my laptop -- the wireless wasn't great, and there was no hibernation, etc., but I had fought my way into getting madwifi working and getting my 3d acceleration working, so I was in decent shape, but the promise of the new applications in breezy, along with the better laptop support was too much to ignore, so I just tried it.

At least right now, I DEFINATELY wish I hadn't.  None of the new laptop functions appear to be working, very few of the new applications showed up in the kmenu, my touchpad actually works worse than it did before, and my wifi is unimproved (thankfully, it isn't any worse).  My graphics also seem a bit shakier.  

Synaptic now gives me this lovely message:
E: postfix: subprocess post-installation script returned error exit status 1
E: mailx: dependency problems - leaving unconfigured
E: mutt: dependency problems - leaving unconfigured
E: lsb-core: dependency problems - leaving unconfigured
E: lsb-graphics: dependency problems - leaving unconfigured
E: lsb-cxx: dependency problems - leaving unconfigured
E: lsb: dependency problems - leaving unconfigured

I read in a number of reviews that it is "worth the upgrade" -- I'm nooby enough that I figured what I had working would keep working, and maybe some of the new versions would work even better.  Now I think I may be in a bit over my head.

I'm guessing an install from CD or a dist-upgrade from one of the release candidates is probably ok, but if you've got a stable Hoary system, it's probably much safer to just stick with what's working.

Obviously people with real linux skills will probably skate right through this, but I'm one of those poor Windows victims who is trying to sneak over to Linux in his spare time, which means I can resolve about two error messages per weekend. 

(K)ubuntu is awesome.  It's the first Linux with a flat enough learning curve that I could begin to make the escape.  For those out there like me, who made it as far as Hoary without breaking anything precious, I say stay with Hoary, at least for a month or two, until there are enough testimonials and/or howto's out there online that the problems you run into will have been documented.

Good luck :)

---

### Post by gat on 2005-10-16
about the apt errors, I found a fix in the archives at:

[http://ubuntuforums.org/archive/index.php/t-21460.html](http://ubuntuforums.org/archive/index.php/t-21460.html)

deppingh says there:
[INDENT]
I had the same problem after upgrading to breezy. The solution for me was to simply stop postifx before running apt-get again:

sudo /etc/init.d/postfix stop
sudo apt-get install
[/INDENT]

Once I'd gotten far enough to see those errors and let the dust settle, deppingh's quick fix was a big help.  Seems the whole cascade was caused by postfix running during the upgrade.

---

### Post by massiCC on 2005-10-25
I had the same problem.....

the two commands listed fixed it (also if there wasn't postfix running ??)

Cheers

---

### Post by jeremy on 2005-10-25
I did a fresh install (having backed up my home dir) of Kubuntu 5.10 on my work machine. Am working away without any serious promlems, just a minor thing with mounted drives not showing in media:/ (but I can see them in /media so it's not too bad).

---

