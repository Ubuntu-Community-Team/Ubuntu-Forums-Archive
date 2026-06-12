---
title: "[SOLVED] Firefox Add-ons Not Working/Downloading"
date: 2008-02-24
forum: General Help
---

### Post by ENB on 2008-02-24
Okay, so for some reason I can't install addons for firefox.

I go to the addons website to install Adblock Plus, but when I click the the green install button it doesn't do anything. But after a long time it will pop up the little message box with the 3 seconds countdown thing, Then I'll click Install Now, but in the addons window it shows Adblock Plus with an error "This Addon is incompatiable with the version of firefox".

I'm on Gutsy clean install (seconds ago), fully updated with Firefox 2.0.0.12. This was going on yesterday, and I figured it was Mozilla's servers acting up or something, but it is still this way.

The interesting thing is when I try to WGET the file for Adblock I get this message: 
"WARNING: Certificate verification error for addons.mozilla.org: unable to get local issuer certificate"

It then tells me I can try "wget [https://addons.mozilla.org/en-US/firefox/downloads/file/19510/adblock_plus-0.7.5.3-fx+tb+sm+fl.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/19510/adblock_plus-0.7.5.3-fx+tb+sm+fl.xpi) --no-check-certificate"

And this lets me open the xpi with firefox and install successfully.

(Everything works just fine on Vista....)

Any ideas?

---

### Post by ENB on 2008-02-24
I just tried the same thing on another computer with Fedora 8 installed/fully updated (FF 2.0.0.12).

And it's exactly the same way... So it's not Ubuntu. It's the firefox update?

Anyone else having the same issue?

---

### Post by ENB on 2008-02-24
*cough*

Also, I just tried installing addons in FF 3.0b4pre, but it's the same problem... I know it's not their download server, because it works fine in Windows. So is it a problem with 2.0.0.12?

---

### Post by sports fan Matt on 2008-02-24
I have had a similar issue with some addons: Forecastfox, the Iaqua theme and Adblock plus wouldnt work.  I redid all my addons (uninstalled as well, and they work but I sometimes get a "this version is no compatible with 2.0.0.12" So id think its a firefox update issue.

---

### Post by ENB on 2008-02-25
Hmmm. Yes, but I even install 3.0b4pre (Minefeild), and it still doesn't work. And all the addons I try to install take _forever_ to "pop up" and in the addon window, the status bar next to it is stuck at nothing. (No progress in installing it)

*sigh* This has never happened before...

And I think I was using 2.0.0.12 a few days ago without a problem. =(

---

### Post by sports fan Matt on 2008-02-25
Sounds like Firefox's latest update hosed alot of things, all I can think of...

---

### Post by y-lee on 2008-02-25
see for ways around this problem [How to fix broken Firefox extensions]("http://www.freesoftwaremagazine.com/blogs/how_to_fix_broken_firefox_extensions")

And btw I use [Swiftweasel]("http://swiftweasel.tuxfamily.org/") and it while being an optimized build of firefox 2.0.0.12 lets me add extensions I KNOW are incompatible with firefox 2.0.0.12, even tho i have **extensions.checkCompatibility** in **about:config** set it to **true**. Some extensions it refuses and I basically force it to use them. This can make firefox unstable, or I might add more unstable than already is :lolflag:

> Swiftweasel is an optimized build of the Mozilla Firefox web browser for Linux. With builds for both AMD and Intel processors. Swiftweasel is 100% compatible with all Firefox themes, plugins, and extensions.

---

### Post by ENB on 2008-02-25
Thanks for all the help!

This is how I did finally solve this:
I went into about:config and changed **network.dns.disableIPv6** to **true**

That still doesn't answer how all this went about, because I booted even into 7.10 livecd, which has FF 2.0.0.8 and the problem was still there.

Anyways, I'm happy now.:)

---

### Post by ENB on 2008-02-26
I'm just wondering though... Why did this work?

Like I've said it's never been this way...

The only thing I can think of is I have a new router, I think its the Linksys N-Wireless..

---

### Post by y-lee on 2008-02-26
> **ENB said:**
> I'm just wondering though... Why did this work?

Like I've said it's never been this way...

The only thing I can think of is I have a new router, I think its the Linksys N-Wireless..


I have no idea but i always set **network.dns.disableIPv6** to **true**. My ISP doesn't even support IPv6, it is hid deep in their web site but I was curious one day and dug around and found it :)

---

### Post by ENB on 2008-02-26
Well that's good enough for me :P

Thanks for all the help! :)

---

