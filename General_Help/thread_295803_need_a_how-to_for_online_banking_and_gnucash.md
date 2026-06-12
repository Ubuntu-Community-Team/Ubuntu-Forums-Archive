---
title: "need a how-to for online banking and gnucash"
date: 2006-11-08
forum: General Help
---

### Post by onesojourner on 2006-11-08
I have googled for a couple hours and I can't find any good information on setting up online banking with gnucash. I read something about needing aqbanking and installed that through the repos ( I am using edgy by the way). I also ran accross a site that looked like extensions and said something about online banking but I have no idea how I would go about installing the extensions or if they are even needed. thanks for any info you guys can give me. right now I am looking into moneydance but I would prefer to use gnucash.

---

### Post by mark2741 on 2006-11-08
Me too! I've been trying to figure this out myself as well. A while back when 2.0 first came out, even before it was available in the repositories, I tried installing it and getting the DirectConnect/ofx thing to work but had zero luck. Today I ran across this link:

[http://specialreports.linux.com/article.pl?sid=06/11/06/0850235&from=rss](http://specialreports.linux.com/article.pl?sid=06/11/06/0850235&from=rss)

It's a review on GnuCash 2.0 and it peaked my interest to give it a try again. It mentions needing a libOFX which is very new. I am busy installing a bunch of other apps right now but will check the repos to see if it's in there and give GnuCash 2 another go. In the meantime I hope someone who has gotten 2.0 to work with DirectConnect will chime in!

> **onesojourner said:**
> I have googled for a couple hours and I can't find any good information on setting up online banking with gnucash. I read something about needing aqbanking and installed that through the repos ( I am using edgy by the way). I also ran accross a site that looked like extensions and said something about online banking but I have no idea how I would go about installing the extensions or if they are even needed. thanks for any info you guys can give me. right now I am looking into moneydance but I would prefer to use gnucash.

---

### Post by lazyart on 2006-11-08
Did you look at this? [http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2)

---

### Post by mark2741 on 2006-11-08
Yes, I found that right after posting my response. Problem now is I can't get aqbanking installed. It required gwenhyfen, which I finally got installed, but now after getting the required newer version of aqbanking (the one in the ubuntu repos is not new enough) I am running into dependency problems. I get this when trying to ./configure:

configure: *** The library "libglade2" is required for GTK2-frontend "g2banking". Specify --with-frontends="cbanking qbanking kbanking" to build aqbanking without that frontend.
configure: *** QT3 is required for QT-frontend "qbanking". Specify --with-frontends="cbanking g2banking" to build aqbanking without that frontend.
configure: *** KDE3 is required for KDE-frontend "kbanking". Specify --with-frontends="cbanking g2banking qbanking" to build aqbanking without that frontend.
configure: error: *** Requirements not fulfilled. Fix your requirements or change the configuration.
mark@mark-ubuntu:~/Desktop/aqbanking-2.2.3$ 

I have tried typing in the following to avoid the errors:

./configure --with-frontends="cbanking qbanking kbanking" --with-frontends="cbanking g2banking" --with-frontends="cbanking g2banking qbanking"

but it still errors - looks like it's only accepting the first --with argument. What am I doing wrong? I think it might just be the way I'm typing these three '--with' arguments in but I just don't know. Also, the last '--with' seems to me to state that it doesn't think I have libOFX installed (at least not a new enough version) but in fact I do per Synaptic. 

I'm amazed no one has come up with an easier way to get this thing configured and instaled for Ubuntu, considering gnucash with directConnect support is a very important app to the open source community IMO.

> **lazyart said:**
> Did you look at this? [http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2)

---

### Post by mark2741 on 2006-11-08
....a followup:

the reason I'm installing aqbanking and all of its dependencies in the first place is because I assume I have to have them, because in my GnuCash 2.0 Tools menu there is *not* an option for HBCI, as stated in the beginning of the tutorial you referenced. I assume that menu item isn't available until aqbanking is setup?

---

### Post by lazyart on 2006-11-08
I don't have an answer here because I never got it running myself.  I tried 1.8.2 but with no OFX I quit on it.  2.0.2 is just dependency hell, just as you said.

There is a howto for taking the debian pkg and adding OFX to it here: [http://ubuntuforums.org/showthread.php?t=213130&page=2](http://ubuntuforums.org/showthread.php?t=213130&page=2) but I presume you've already looked at it.

This is worse than trying to get Beryl to cooperate.  Moneydance is starting to look pretty good at $30.  I downloaded the trial and it found my itty-bitty bank.

---

### Post by onesojourner on 2006-11-09
I have been messing with moneydance for about a day now. is very nice. it also will run on my home ubuntu machine and my windows machine that I use at work. I think I will hold off on gnucash until a few more of the headaches are worked out. if any one gets this going with out a hitch using edgy let me/us know.

---

### Post by sirmrmatt on 2006-11-09
I am having all the same issues...that elusive fifth menu item on Tools just does not want to show up. ](*,) 

GNUCash looks great, but I wish I could use it like I need to use it (automagically). Any progress on this in Edgy?

- Matt

---

