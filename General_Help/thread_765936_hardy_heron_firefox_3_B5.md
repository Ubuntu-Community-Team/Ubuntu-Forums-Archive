---
title: "hardy heron firefox 3 B5"
date: 2008-04-24
forum: General Help
---

### Post by terranz on 2008-04-24
I've been using Ubuntu 8.04 for a few weeks now and in the last few days Firefox 3 has started behaving very badly.

Every 10 to 15 seconds the browser fades to grey and becomes unusable.
I have system monitor running and the CPU usage spikes at the same time but after the spike the browser remains grey for most of a minute afterward.

This only happens when in firefox and and has only started happening in the past few days.

As far as I can tell this is the only problem I've had with this version of ubuntu.  8.04 seems stable almost to the point of being bullet proof

---

### Post by yaknowwat on 2008-04-25
1) Do you have any old firefox 2 addons in use in it or suspicious addons or upgrade from firefox 2 (bad profile then)

2) Do you have desktop effects / compiz / compiz-fusion enabled

3) none then list possible culprits and maybe system specs.

If  "1" make a fresh Firefox Profile and test it out.

Making a firefox profile : (make sure firefox is closed)
Alt-F2 or open terminal
```
firefox -ProfileManager
```
Make your profile and name it
Now to start that profile
(note: there is a variable you need to change in this command <profilename> with your profile name of course.)
```
firefox -P <profilename> -no-remote
```
Then test out that profile.

If "2" disable desktop effects / compiz / compiz-fusion

And see if that works.
If you need a composition manager to replace compiz you can use the one built into metacity as it doesn't need hardware acceleration and is plenty stable. It also has a few effects other than it being a small composition manager (usable with non compiz compatible cards such as some ATI's).

To enable:
Open terminal or Alt-F2
```
gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  true
```
to disable
```
gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  false
```

---

### Post by FredB on 2008-04-25
Or it could be a flash related problem... Go to Tools / Add-ons and try deactivating flash if you have it...

---

### Post by yaknowwat on 2008-04-25
> **FredB said:**
> Or it could be a flash related problem... Go to Tools / Add-ons and try deactivating flash if you have it...

Possibly but its reoccurring in specific time intervals according to him so I'm not sure its flash.

---

### Post by terranz on 2008-04-28
Sorry for the late reply.

I have since completely removed firefox 3 and installed firefox 2 but got errors when ever trying to instally an extension.

I removed 2 and did a fresh install of 3 again and started getting the grey out and this is before I had the chance to install any extensions.

I am using compiz (default install with 8.04) but had no problem for a week and a half following install.

I's 11:20 am now so ther's nothing more I can to till after work but I will try creating a new profile this afternoon.

I have 2.6ghz celeron D, 1GB RAM and 256MB Radeon 9600 pro - in answer to first post.

---

### Post by yaknowwat on 2008-04-29
alright when ever you get around to it going through the suggestion i put.

Chances are more than likely its Compiz though Disable Desktop Effects and see how it runs.

---

### Post by terranz on 2008-04-29
I tried it, that is creating the new profile and it seemed to work pretty well.  It only stalled once in 2 hours and that was when on a site the uses posting and insists I disable adblocker.

---

### Post by aheckler on 2008-04-29
Your problem might be that, once FF3 uses your profile (located in ~/.mozilla/firefox) FF2 can't use it anymore. You'll have to wipe it clean. So if you want FF2, first uninstall FF3 with "sudo apt-get purge firefox-3.0" then delete your Firefox profile with "rm -r ~/.mozilla/firefox" then finally install a fresh FF2 with "sudo apt-get install firefox-2".

---

