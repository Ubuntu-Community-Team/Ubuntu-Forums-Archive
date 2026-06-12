---
title: "Ubuntu 16.04 LTS vs Firefox"
date: 2020-08-18
forum: General Help
---

### Post by 77_GCSX on 2020-08-18
Yes, You read that right...VS, as in verses ( a fight).

We've been using Ubuntu for a few years with only a couple minor issues but this one is really stumping me. Firefox seems to REALLY want to eat our available RAM. This started with the normal version of Firefox. My wife mainly uses it to shop online (and use Rakuten and other to save $$) and will sometimes leave Firefox open. When she does this and someone else needs to use the PC it gets REALLY laggy with a lot of disk activity.

I have a widget installed on my log on that shows the system status (including available RAM %) and it would be very high (RAM = 8 gb). We decided to try out FireFox ESR and this seemed to help the issue but now it's back again. One day, just recently, I switched users (with her still signed on) and the RAM % being used was up to 93%!!! All she had open was 2 tabs with a store website on each. She wasn't even doing anything.

If it helps, my PC specs are: Dell 3010, 8gb ram, 1 tb HD, not much else. It's not modded, just a relatively plain jane 3010.

BTW: Chrome works great! No issues hogging the ram or anything.

Thanks for any help!

---

### Post by mrdc76 on 2020-08-18
Have you tried disabling all Firefox extensions? One of them might have gone rogue.

---

### Post by TheFu on 2020-08-18
> **mrdc76 said:**
> Have you tried disabling all Firefox extensions? One of them might have gone rogue.

+1.

Every time I've had a firefox issue, it was always removed by running in "safe-mode" - which is disappointing, since it is easy to blame FF and not the addon/plugin providers who make it a little more usable.

According to the FF manpage, use 
```
       -safe-mode
              Start  firefox  in safe-mode. This disables all third-party
              extensions, and may be necessary if you are having problems
              with an extension you installed.
```
FF is using about 500MB of RAM now as I type this with 18 tabs and about 6 addons.

---

### Post by Autodave on 2020-08-18
I would also try adding *uBlock* as an ad blocker.  Disable any other ad blocker that you may have running.

---

### Post by 77_GCSX on 2020-08-18
Unfortunately there are a couple of extensions that my wife uses for online shopping. EBates and Rakuten that I can think of off the top of my head.

I'll check these out and see which one may be the culprit.  Thank You!

---

### Post by TheFu on 2020-08-18
> **77_GCSX said:**
> Unfortunately there are a couple of extensions that my wife uses for online shopping. EBates and Rakuten that I can think of off the top of my head.

I'll check these out and see which one may be the culprit.  Thank You!

She needs her own account - and I'd run the browser for that in a separate "container" to prevent too much leakage with normal web browsing.  Those extensions are all high-risk, anti-privacy.  Fight back by having a separate browser config just for using those.

---

### Post by 77_GCSX on 2020-08-18
> **TheFu said:**
> She needs her own account - and I'd run the browser for that in a separate "container" to prevent too much leakage with normal web browsing.  Those extensions are all high-risk, anti-privacy.  Fight back by having a separate browser config just for using those.

By "separate container", do you mean something like a Virtual Machine (EDIT...I Googled this and found "Docker")

After looking this Docker info over I think i MAY end up making a VM running Ubuntu (Yes, Ubuntu inside Ubuntu) and having just Firefox and or Chrome installed with the apps my wife uses and see if this helps.

If you have any other info or tips/suggestions I'm open.

Thank You.

---

### Post by mastablasta on 2020-08-19
you can install it as snap (it is *containerized*).

otherwise we use same account to do stuff on PC, but we use profile manager for firefox so that each of us can keep their own profile and theme. not so much important as the kids got their own machines now, but sometimes they still use the main PCs's or each others PC.
more here: [https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles)

it's also easy to backup/move profiles. you could also use Firefox sync for that.

---

### Post by TheFu on 2020-08-19
> **77_GCSX said:**
> By "separate container", do you mean something like a Virtual Machine (EDIT...I Googled this and found "Docker")

After looking this Docker info over I think i MAY end up making a VM running Ubuntu (Yes, Ubuntu inside Ubuntu) and having just Firefox and or Chrome installed with the apps my wife uses and see if this helps.

If you have any other info or tips/suggestions I'm open.

Thank You.

Option 1:
use a different userid - one for normal stuff, different one for wifey doing normal stuff, and a different one for when tracking/coupons are done.  You can use a "private firejail" to run most web browsers, so they appear to be a fresh install each time. Nothing can be written to disk in that mode.  I'd never trust a browser's claimed "incognito-mode" or any other attempt to sandbox tabs. They have such a long history of failures to keep things private, I'm not willing to trust them. Browsers are overly complex for reasons that aren't really that important to users - besides speed.

Option 2:
Don't use a different userid for real privacy. How to block bad sites most of the time, but not always? I normally block about 130K "bad", spyware, tracking, and malware domains from the internet in my daily use, but those coupon tools need 10,000 tracking sites enabled.  I don't know how to have selective answers on the network where some users get full protection and others only get selected protections from tracking.  A linux "container" would be the lite-est, most integrated, solution for that, since the container can use different network and blocking settings than the host OS it runs inside.  A VM can also perform this, but VMs are 10x heavier and 20x larger on disk than a container.  Regardless, I wouldn't run a full Ubuntu if all that I wanted was a web browser + coupon addon. I'd run a minimal, browser-only solution - perhaps TinyCore Linux in a VM and just the preferred browser if a Linux Container was used. Containers don't really have a separate OS, but some appear to work that way.  A base LXD container is about 500MB. A base VM is 4GB.  I wouldn't use docker for a number of reasons. I'd use LXD. LXD provides a little more OS than docker does and many network things that don't work or are a huge hassle in docker can be handled in lxd.

BTW, no way would I be using Chrome anywhere.  Use Chromium or Brave or Firefox, never Chrome.  Why run the software created by the largest advertising, tracking, spyware and marketing company in the world if you hope to have any privacy?  Seems counter productive, doesn't it?  

I will admit to using Android, but I don't use any Google apps on that device, unless there isn't any other choice. Still, many of those apps require google infrastructure to work, so I am a hypocrite. Still, preventing _some_ data is better than doing nothing, right?  My network blocks hundreds of google-owned internet domains.  Some I have to allow for certain websites to work at all which I need from time to time. These are usually for hotel reservations and other travel planning. Most of the time, they aren't necessary, but my travel has drastically slower the last few years.

I think the Gnome guys have a tool called "Boxes" which may put everything run into a separate container. That wouldn't block different profiles from seeing each other, however. A "box" works within the same constraints for the same userid+program combination.  Separate userids should have 100% separate "boxes".  I'd hope. I'm not sure. I don't use Boxes. [https://wiki.gnome.org/Apps/Boxes](https://wiki.gnome.org/Apps/Boxes)

**What I'd really try to setup**
Just providing options.  I'd use lxd - perhaps with tinycore as the base OS (assuming that is possible) inside the container.  For my online banking, I've been running **firejail --private chromium**, so nothing ever gets saved between program runs. The browser thinks each run is the first time ever and sees a nearly empty HOME and next to nothing of the base OS.  When I want chromium with some constraints, but access to ~/Downloads/, then I use **firejail chromium**.  I use chromium only for very specific needs and run a fresh instance for each.  Firefox and Dillo are my normal surfing weapons.  Dillo for new sites I'm unsure about, firefox for "trusted" sites I know, but usually with limitations.  The problem running in firejail --private mode is that any addons are lost.  Firejail blocks all access to any existing configs, settings, so the browser "appears" to be running in a brand new userid HOME directory.  I'm not sure how to automate a quick install of the desired addons into that specific environment, because any scripts created wouldn't be in the environment either.  I've been doing some GUI automation the last few weeks when normal scripting fails. Perhaps a cnee script or xdotool script running outside the firejail environment would work?  IDK.

This is all probably too complex for most people. Fortunately, we all have choices and options.

---

### Post by 77_GCSX on 2020-08-19
A ton of great info in these last 2 posts. Thank you all. It will take me some time to read and understand and possibly test some of this so bare with me.

---

### Post by monkeybrain20122 on 2020-08-20
To locate the problem you can start FF is safe mode (without any extension) or test with a new profile and see if the problem persists.

---

### Post by kurt18947 on 2020-08-20
I have nowhere near TheFu's knowledge and sophistication so I created a 2nd installation with as few add-ons as I can manage, not even a printer driver. That O.S. is used ONLY for information that needs to stay private. At least one credit card company plants some sort of 'SuperCookie', browser finger print or something. I can't connect to their site with a machine that hasn't been there before. If I have a new install  I have to request a one-time use code to get the identifier. Then I can log in normally.

---

### Post by mastablasta on 2020-08-21
wow! and then they get hacked... :)

mine uses 2FA + notification to user (SMS+e-mail) + insurance up to certain amount. though i imagine insurance is likely more difficult to claim than they advertise. they are quite accommodating and were even willing to double the limit on card for one month 2 years ago when i needed it temporarily while resolving a claim for unused air ticket. anyway no system is ideal, but i think the one i currently use is relatively safe and user friendly. so far it was also without incident. 

i am still puzzled how in USA you do not need to provide the pin to use credit card. in fact hotels and businesses still use magnetic strip (rather than safer chip) and no user signature required. :O
on the other hand no touch and go for small amounts (is it called RFID?!) and in many places no portable POS.

---

