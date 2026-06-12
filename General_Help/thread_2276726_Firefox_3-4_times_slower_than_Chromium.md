---
title: "Firefox 3-4 times slower than Chromium"
date: 2015-05-04
forum: General Help
---

### Post by Sableye on 2015-05-04
Hello Ubuntu's

I have a 2-3 month old install of Ubuntu 14.04 on an SSD drive, on a medion E1317T with 8gb ram. I have Firefox installed, I believe it came as default.

It has always taken a while to open web pages, 5-10 secounds to fully load up [http://www.sluniverse.com/php/](http://www.sluniverse.com/php/) I have both Ghostery and AdBlock+ installed.

Today I installed Chromium Browser. It loads the same page in a secound or two at most. Even the Ubuntu browser manages quite quickly in comparison. I tried the same set up running of a USB3 thumb drive and found the same thing.

Is there something up with my PC for Firefox to be so slow, and how do I find and fix it if there is? Or is Firefox generally slow, or Chromium just fast?

Thanks

---

### Post by aljosa2 on 2015-05-04
hi,
our experiences with broswers are similar.
one day, just for fun, i installed chrome. i'm not using chromium any more, and the reason is simple: firefox 3-4 times slower than chromium, chromium 2-3 times slower than chrome.

---

### Post by v3.xx on 2015-05-04
Nothing should be slow with that setup.  I do not have the problem myself, but then I do not run standard FF.  I got tired of the little glitches that can come with a version release and moved on to FF-ESR.

[https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)

May work for you.

On the other hand, there are things to try.

[https://www.google.com/search?client=ubuntu&channel=fs&q=firefox+is+slow+linux+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=firefox+is+slow+linux+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by RobGoss on 2015-05-04
[COLOR=#000000]Try using preload it will help applications get loaded much quicker. Each time you open a program it will load it into preload to speed things up. 

Run this command
```
 sudo apt-get install preload 
```[/COLOR]

---

### Post by ajgreeny on 2015-05-04
I think there must be something wrong with your install of FF or your FF profile as those pages load in about 1.5 seconds on my machine, Intel i5-3570K, 8GB ram, so not very different from yours, and chromium is just about identical in speed terms.

Just a thought, but might this be more to do with your network and some DNS problem when using FF?

---

### Post by Sableye on 2015-05-04
After exhausting google, trying preload, and trying a new iso on a USB drive and having the same thing, all I have left to try is....

> **ajgreeny said:**
> Just a thought, but might this be more to do with your network and some DNS problem when using FF?

Seen a guide on ivp6 and prefetch settings. Will have a go tomorrow and report if it has any effect.

Cheers!

---

### Post by Mike_Walsh on 2015-05-04
Hi, Sableye.

I agree with AJ. With your set-up, it shouldn't be running slow in the normal course of things. However.....

This **is** only a suggestion, but I found it DID work for me...

Ditch AdBlock Plus. The thing loads a blocking script for every single item on the list; if you're viewing a page that has LOTS of items ON that list, it is astounding just how much it slows it down by. See here:-

[http://betanews.com/2014/05/15/is-adblock-plus-killing-the-web-massive-memory-usage-is-dragging-firefox-down/](http://betanews.com/2014/05/15/is-adblock-plus-killing-the-web-massive-memory-usage-is-dragging-firefox-down/)

I find that Ghosty takes care of by far the biggest chunk of trackers, and all the other assorted crap on web pages.....and for the rest of it, I use BluHell Firewall; it incorporates a very minimalist 'ad-blocker' by default, which seems to catch what slips through Ghosty's net.  Does the job for me.

I use Chromium much of the time, but for certain webpages, you just can't beat FireFox.


Regards,

Mike. ;)

---

### Post by sgage on 2015-05-04
I have not noticed any real disparity between FF and Chrome in speed of loading pages.

---

### Post by tgalati4 on 2015-05-04
Ad Block Edge (ABE) seems to have less overhead that Ad Block Plus.  If your firefox profile gets too bloated, you might need to delete it and create a new profile.

Open a terminal:

```
man firefox
```

---

### Post by Sableye on 2015-05-05
Fiddled with the Firefox config and ivp6, removed AdBlock+, kept Ghostery. Chromium is still faster by almost double speed. Baffling.

---

### Post by Mike_Walsh on 2015-05-06
> **aljosa2 said:**
> hi,
our experiences with broswers are similar.
one day, just for fun, i installed chrome. i'm not using chromium any more, and the reason is simple: firefox 3-4 times slower than chromium, chromium 2-3 times slower than chrome.

Hm. Quite unusual. I won't use Chrome; keeps asking me to sign in...and again...and again...and again.... Refuses to recognise my account. 

I've been using Chromium for some months now, and have NO problems with it at all....same account, but it's quite happy with an initial sign-in.  And I, too, find there's barely any speed differential between Chromium and FF. SOMETHING is not quite right there. Have you tried clearing the cache....or creating a new profile?


Regards,

Mike.

---

### Post by Sableyes on 2015-05-06
Went beyond creating new profiles and re downloaded Ubuntu onto a USB3 Sandisk Cruiser Fit, tried again and found the same. Chromium much quicker than Firefox.

---

