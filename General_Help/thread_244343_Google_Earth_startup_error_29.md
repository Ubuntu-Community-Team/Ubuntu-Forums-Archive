---
title: "Google Earth startup error 29"
date: 2006-08-26
forum: General Help
---

### Post by matthew on 2006-08-26
I installed Google Earth (version 4.0.1693 (beta)) some time back using the .bin downloaded from their website. All was working well for several weeks until a couple of days ago. 

Suddently when I run Google Earth a dialog box pops up that says> Google Earth detected an error while trying to authenticate
Please check the following:
- your network connection (can you get to [www.google.com?]("http://www.google.com?"))
- your firewall settings (are you blocking /home/matt/google-earth-bin?)

Error code: 29
For more information, visit:
[http://earth.google.com/support/bin/answer.py?answer=20717](http://earth.google.com/support/bin/answer.py?answer=20717) I can confirm the network connection works properly. I can connect to google's web pages.

The only firewall I am running is iptables and it was set up using Firestarter. No changes have been made in months, so I can't see how that would be affecting things.

I visited the web site listed and have also tried:
-using the Firefox "user agent switcher" extension I was able to use the Windows utilities linked on the site to confirm my ability to connect to the googleearth servers.

-I have reinstalled my ATI 3D video drivers and can confirm they are functioning properly.

-I have cleared my Google Earth cache.

-I have uninstalled and reinstalled Google Earth 3 times.

-I have tried to browse the Google Earth help center web pages looking for some sort of other ideas, but I'm running dry.

I have also tried searching Google and I have found other linux users having similar problems, but no solutions yet.
-in the [Google Earth forums (linux area)]("http://bbs.keyhole.com/ubb/showthreaded.php/Cat/0/Number/457243/page/4") (but no solution is mentioned)
-in other parts of the [Google Earth forums]("http://bbs.keyhole.com/ubb/showflat.php?Number=38130") (I'm not using windows)
-in the [Fedora Forums]("http://fedoraforum.org/forum/showpost.php?p=550132&postcount=18") (but I'm not behind a proxy)
-I found out here that it is [blocked in Bahrain]("http://mahmood.tv/?p=2670")...I wonder if it's now blocked here??

FYI, I am using Google Earth from my Centrino wireless laptop, connecting via WPA to my LinksysWRT54g router, then from that into an SMC7904BRA ADSL modem/router combo. I have been using this setup with no changes for at least 3, maybe 4 months with no problems and no settings have been changed. I connected to Google Earth this way with no problems as recently as last week.

BTW, running the startup command in the terminal produces no output in the terminal.

I can connect from Google Earth to see if there are any updates available from the Help menu.

I'm fresh out of ideas...does anyone else have one?? ](*,)

EDIT: I would like to add that I just disabled my wireless connection and plugged directly into the SMC router with a cat5 cable. Everything worked perfectly...except for Google Earth, which is still giving the same error.

---

### Post by matthew on 2006-08-27
I wanted to give an update. After changing absolutely nothing since my last post everything is working now, so I guess the problem was either with my ISP and their connection to the Google Earth servers or at the Google Earth servers themselves.

---

### Post by lethu on 2007-05-07
Hello, I seem to have the same issue with Google Earth (version 4.0.2735), an "Error code: 29".
I am using iptables set up by Firestarter too but I also tried running the app after stopping the firewall always in vain. The only other common point that may be causing this problem is the ISP which I guess is the same in both of our cases, so I think I will simply wait a day or two and try again, wanted to post this in case there are other people in the same situation, so they know that this might be ISP related.
PS: So you like coffee with milk... Hmm weak soul : p.

---

### Post by matthew on 2007-05-08
> **lethu said:**
> Hello, I seem to have the same issue with Google Earth (version 4.0.2735), an "Error code: 29".
I am using iptables set up by Firestarter too but I also tried running the app after stopping the firewall always in vain. The only other common point that may be causing this problem is the ISP which I guess is the same in both of our cases, so I think I will simply wait a day or two and try again, wanted to post this in case there are other people in the same situation, so they know that this might be ISP related.
PS: So you like coffe with milk... Hmm weak soul : p.I've checked with people all over the country and no one I know is able to use Google Earth from Morocco at the moment, not with Linux nor with Windows. I think IAM (the ISP I use, and I guess you are using) is blocking it.

Which part of Casa do you live in? I used to live in maarif a few years ago, before moving to Fes.

---

### Post by Technoviking on 2007-05-08
Google Earth is a package in Universe or Multiverse now. How you tried that and see if it works. Also try deleting your ~/.googleearth directory.

---

### Post by matthew on 2007-05-08
> **Mike said:**
> Google Earth is a package in Universe or Multiverse now. How you tried that and see if it works. Also try deleting your ~/.googleearth directory.Yeah, I have. I've installed both ways, from the Medibuntu/PLF repos (I don't think it's in the official repos, not even multiverse...) and from the bin package on the Google Earth website. I've cleared the cache, I've deleted my ~./googleearth directory, I've tried installing on different computers with fresh installations. 

That's when I started asking my friends for their experiences, because we were having lots of fun with the program--there are great archaeological sites in Morocco that show up great in GE, along with the standard, "Let's try to find our house" bits. Not one of my friends in the country is able to use Google Earth, and the program stopped working for all of us at the same time. 

When I travel outside the country, to Spain or Turkey, for example, Google Earth works fine on my laptop.

I'm 100% sure in my case the ISP is blocking it, probably at the polite request of the people in power. :) Enough said there. ;)

---

### Post by lethu on 2007-05-08
> **matthew said:**
> I'm 100% sure in my case the ISP is blocking it, probably at the polite request of the people in power. :) Enough said there. ;)
Too bad, I think am sticking too to your explanation, but I still like to doubt a bit about this in hope that we will get GE working again some near day, I have done some googling about this problem and found French and Moroccan articles talking about this same issue happening back in August, 2006 (which coincides with your first post's date) and blog comments continuously proposing various theses and solutions till this day, there seem to be some people using proxies "successfully" but I can't confirm their sayings since I didn't try this myself yet (I might try Tor when I have some free time, I always wanted to try it and it seems this is the perfect occasion : ).
Anyway I really hope this isn't occasioned by some kind of intentional blockage since it's both useless and inappropriate : /.

> **matthew said:**
> Which part of Casa do you live in? I used to live in maarif a few years ago, before moving to Fes.

I am not too far from maarif (just next to Bd. Ghandi), I go there by foot when am not pressed : ).

PS: Here are links to the articles and comments (in French) mentioned above, [http://www.pcinpact.com/actu/news/30911-Des-problemes-dacces-a-Google-Earth-au-Maroc.htm]("http://www.pcinpact.com/actu/news/30911-Des-problemes-dacces-a-Google-Earth-au-Maroc.htm")
[http://tempslibres.blogjahiz.net/index.php?2006/08/23/45-maroc-google-earth]("http://tempslibres.blogjahiz.net/index.php?2006/08/23/45-maroc-google-earth")

---

### Post by matthew on 2007-05-09
> **lethu said:**
> Anyway I really hope this isn't occasioned by some kind of intentional blockage since it's both useless and inappropriate : /.I agree. I have Tor set up and can use it with Firefox, so it shouldn't be too much trouble to set up for GE...I'll look into it when I have time. Tor does slow things down quite a bit, so I'm not sure how well it will work with GE. It will be fun to find out.

> **lethu said:**
> PS: Here are links to the articles and comments (in French) mentioned above, [http://www.pcinpact.com/actu/news/30911-Des-problemes-dacces-a-Google-Earth-au-Maroc.htm](http://www.pcinpact.com/actu/news/30911-Des-problemes-dacces-a-Google-Earth-au-Maroc.htm)
[http://tempslibres.blogjahiz.net/index.php?2006/08/23/45-maroc-google-earth](http://tempslibres.blogjahiz.net/index.php?2006/08/23/45-maroc-google-earth)Thank you for those. I'll take a look.

By the way, they also block [OpenDNS]("http://www.opendns.com")...

---

### Post by lethu on 2007-05-09
*Sigh* how sad...

---

### Post by @vijay@ on 2008-03-09
use sudo googleearth

---

### Post by scradock on 2008-04-26
tried that - makes no difference. And I'm in California!  The censors have long arms indeed.......

---

### Post by ZachSka87 on 2008-04-27
bump

I am also having this problem.

---

### Post by acope on 2008-04-27
This fixes the problem on my 64-bit system: 

sudo apt-get install lib32nss-mdns

---

### Post by JayBee808 on 2008-04-27
> **acope said:**
> This fixes the problem on my 64-bit system: 

sudo apt-get install lib32nss-mdns

This worked for me on 64bit Hardy, Google Earth 4.3
Thank you so much, I've been fighting with this for days.

---

### Post by pete35887 on 2008-04-28
> **acope said:**
> This fixes the problem on my 64-bit system: 

sudo apt-get install lib32nss-mdns

I would have to say this is solved.  Thanks bunch!

---

### Post by chinaski on 2008-05-05
> **acope said:**
> This fixes the problem on my 64-bit system: 

sudo apt-get install lib32nss-mdns
thank you for the tip ;)

---

### Post by Nescafi on 2008-05-06
> **acope said:**
> This fixes the problem on my 64-bit system: 

sudo apt-get install lib32nss-mdns

Thank you very much ! However I still have to execute googleearth as root for now.
But it works ! Thank you !

---

### Post by zakmyrr on 2008-05-10
aww shucks, i used my first post to post redundant info and revive a dead post...all in one shot.   sorry

---

### Post by luke16 on 2008-05-19
sudo googleearth worked for me. Why does google earth need root access?

---

