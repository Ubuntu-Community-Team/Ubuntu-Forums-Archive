---
title: "Warty with select packages from Hoary?"
date: 2004-11-30
forum: General Help
---

### Post by ponds on 2004-11-30
Hi, I'm wondering if it's possible to have Warty, and then to install a few packages from Hoary.  Mainly Firefox and X-org.

I know in Debian you can do something like APT::Default-release "woody"; in /etc/apt/apt.conf and then put both repo's in sources.list, and then when you wanted something from sarge you could do "apt-get -t sarge mozilla-firefox."  Does this work in Ubuntu, or are the builds between Hoary and Warty too different for it to?  I'm also worried about Xorg, with stuff in Warty that depends on XFree86.


Thanks.

---

### Post by wallijonn on 2004-11-30
If you have an ATI card I would wait awaile before venturing into XOrg. I tried it and it was a mess. 

As for FF1.0 I believe there is a write up for it, elsewhere. Besides the Hoardy there is a method for updating with Mozilla's .bin. 

I'm perfectly happy with FF0.93 and haven't even bothered updating my WXPP & W2KP FF1.0PR to FF1.0. I've decided to wait awhile until all the extensions are updated.

---

### Post by astoltz on 2004-11-30
When I tried upgrading FireFox from Hoary, apt pulled in a few dependancies which broke my Warty system.  I ended up backing all the firefox upgrade stuff out to repair.

I think FF1.0 is worth the trouble though, so I downloaded it direct from mozilla.org (I get the manual version, as opposed to thier installer version), unpacked it and pointed /usr/bin/mozilla-firefox at the newly installed FF1.0.  It's been working flawlessly ever since.

---

### Post by jdong on 2004-11-30
I was JUST experimenting with this last night, but not good news:

Yes, you can pin Warty as default, but Warty's repo isn't like Sarge: Warty's updates are in warty-security, a separate repo, so you won't get security updates (!!).

You can pin warty-security, but that means newly installed packages will come from Hoary.

Neither situation is pretty.

---

### Post by ponds on 2004-11-30
I have an ATI card, but it always worked fine in Xorg on other platforms Gentoo/Slackware/BSD is what I've used before.

For some reason, XFree86-DSFG screws up my font sizes in Gtk apps when I'm not running gnome (and often I don't run Gnome), and I've spent hours trying to find out what causes it, and since Xorg doesn't give me the same problem, I'd rather just take the path of least resistance.

Firefox isn't really that big of a deal, it was more of an example.

---

### Post by clasqm on 2004-11-30
FF from Hoary works fine over here, but the Evolution I got from there is seriously broken. I had to turn Secure Connection off to get it to fetch my POP3 mail, for instance.

Not complaining, I knew what I was getting into ...

---

### Post by poofyhairguy on 2004-12-01
[QUOTE=ponds]Hi, I'm wondering if it's possible to have Warty, and then to install a few packages from Hoary.  Mainly Firefox and X-org.

I know in Debian you can do something like APT::Default-release "woody"; in /etc/apt/apt.conf and then put both repo's in sources.list, and then when you wanted something from sarge you could do "apt-get -t sarge mozilla-firefox."  Does this work in Ubuntu, or are the builds between Hoary and Warty too different for it to?  I'm also worried about Xorg, with stuff in Warty that depends on XFree86.


Thanks.[/QUOTE]

Well, you could go all out and update to hoary. I use hoary, its as stable as official releases of Fedora or Mandrake could dream to be!

---

### Post by jdong on 2004-12-01
[QUOTE=poofyhairguy]Well, you could go all out and update to hoary. I use hoary, its as stable as official releases of Fedora or Mandrake could dream to be![/QUOTE]
I agree too, as far as with the stability...

However, keep in mind that Fedora/Mandrake get security updates, too -- something that Hoary sometimes lags behind on! No problem, except if you run a server!

---

