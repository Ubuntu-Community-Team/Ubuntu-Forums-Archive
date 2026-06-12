---
title: "Firfox crashing a lot - anyone else notice this?"
date: 2020-04-11
forum: General Help
---

### Post by iamtheeggman2 on 2020-04-11
Hi,

Some 2 years ago or so firefox started crashing a lot and then it somehow fixed, however over the last one to two months its crashing again, even on the most famous websites, youtube, ebay, etc. Anyone else get this recently? Its crashing the browser tab though and not the entire application.

---

### Post by leok2 on 2020-04-11
No problem with Firefox for me.What distro and version are you using?What version of Firefox? Ethernet or WiFi connection?

---

### Post by crip720 on 2020-04-11
First thing to try is running firefox with all extensions disabled.  Found sometimes an extension will do odd things.  You don't mention the time frame, but some sites are resource hungry if kept open/loaded for a long time(hours/days).  If first two don't help, might need to completely purge firefox and profiles(use google to find how), and reinstall, can use firefox sync if you don't want to add everything back manually.

---

### Post by iamtheeggman2 on 2020-04-11
lubuntu 18.04 32bit, firefox 74.0.1 - also I noticed sometimes when I click the home button it is non responsive for 5-6 seconds and then it goes there? wifi but there is no issue when I run windows.

---

### Post by crip720 on 2020-04-11
Noticed that you are using 32bit.  Quite a few 32b systems would be low in the amount of ram they have available.  Multiple open tabs for resource hungry sites could be a problem.  4GBs or less  does not go as far now as it used to

---

### Post by Autodave on 2020-04-11
Lack of sufficient memory will cause that.  As already suggested, remove/disable all extensions.  Then, add *uBlock* and see what happens.

---

### Post by iamtheeggman2 on 2020-04-12
> **crip720 said:**
> Noticed that you are using 32bit.  Quite a few 32b systems would be low in the amount of ram they have available.  Multiple open tabs for resource hungry sites could be a problem.  4GBs or less  does not go as far now as it used to


I spend a lot of time  on youtube, it uses up hundreds of MBs in Firefox app and web content whatever that process is.But sometimes I don't even use it for too long and i crashes.

---

### Post by iamtheeggman2 on 2020-04-12
When you say extensions you mean addons right? I don't have any.

---

### Post by sgage on 2020-04-12
It does sound like it could be a RAM issue. I have 12 GB RAM, and have no problems at all with FF.

---

### Post by iamtheeggman2 on 2020-04-12
> **sgage said:**
> It does sound like it could be a RAM issue. I have 12 GB RAM, and have no problems at all with FF.


I have 10 GB of ram

---

### Post by Autodave on 2020-04-12
Install *uBlock* on Firefox and see if that helps.  If not, you can disable it.

---

### Post by daniewicz on 2020-04-12
I would take the advice given in post #3 and try logging into FF with a new profile.

---

### Post by mörgæs on 2020-04-12
> **iamtheeggman2 said:**
> I have 10 GB of ram

Then you should do a fresh install of a 64 bit 19.10 or 20.04. A 32 bit OS does not handle this amount of memory well.

---

### Post by iamtheeggman2 on 2020-04-13
> **mörgæs said:**
> Then you should do a fresh install of a 64 bit 19.10 or 20.04. A 32 bit OS does not handle this amount of memory well.

ok will 64bit 19:10 upgrade easily to 20:04? last time I tried the upgrade feature it didn't work wasting several hours of time.

---

### Post by mörgæs on 2020-04-13
People should in general not upgrade any Buntu release. Always a fresh install.

Up*dates* on a daily basis, on the other hand.

If you install 19.10 the next fresh install should be in July when support runs out.

---

### Post by iamtheeggman2 on 2020-04-13
> **mörgæs said:**
> People should in general not upgrade any Buntu release. Always a fresh install.

Up*dates* on a daily basis, on the other hand.

If you install 19.10 the next fresh install should be in July when support runs out.

I know but i don want to prat about reinstalling a system every time.

---

### Post by Impavidus on 2020-04-13
64 bit 19.10 should upgrade just fine to 20.04, provided it's reasonably clean. 32 bit won't, as there's no 32 bit Ubuntu of any flavour after 18.04. But release upgrades are a bit of a hit-or-miss feature. For some people they always work, for some people they never work, and it isn't always clear why. My current system was installed as 16.10 and upgraded in stages to 19.10. It's getting a little sluggish, so I think I'll do a fresh install of 20.04 in a few weeks.

Instead of installing 19.10 now and upgrading to 20.04 in July, it may be better to install 20.04 directly. It should get released next week.

---

### Post by daveginboav on 2020-04-13
Do you use a FF synced account?  I was having crashes with a 32bit Linux Mint 19.3  FF when it synced my account from a 64 bit UbuntU 18.04 LTS.  I restarted FF without syncing, (firefox -no-remote from terminal prompt), then deleted account synching and now no more crashes.

---

### Post by iamtheeggman2 on 2020-04-28
It has not crashed since I installed ubuntu 20.04 64bit on Friday morning and yesterday used it for 6 hours or more watching youtube channels and it didn't crash then so it's looking like some previous advice on 64bit being with better ram might have done the trick.

---

### Post by mörgæs on 2020-04-28
Good, please mark the thread solved.

---

