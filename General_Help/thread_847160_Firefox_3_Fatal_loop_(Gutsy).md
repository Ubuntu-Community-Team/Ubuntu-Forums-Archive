---
title: "Firefox 3: Fatal loop (Gutsy)"
date: 2008-07-02
forum: General Help
---

### Post by acl123 on 2008-07-02
Hi, I'm running Gutsy.
I installed Firefox 3 (final release) by downloading it from mozilla and it ran fine for a couple of days, but now whenever I try to open it crashes with this error:
```
Error: in guard: symbol required but got: Error: fatal: looped fatal error
```
I think it may have had to do with the "Add Bookmark Here" extension, which I installed the last time before it started crashing.

I deleted the directory containing firefox (i.e. ~/firefox), then unzipped a fresh copy from mozilla. I tried deleting the ~/.mozilla folder. I also opened the old version of Firefox 2 (which runs ok) and uninstalled "Add Bookmark Here". None of these things have worked though, I still can't run Firefox 3.

Does anyone have any suggestions?

---

### Post by NT4usB on 2008-07-02
After deleting all that, were you prompted to create a new profile?
If not, run ```
$firefox -p
``` and create a new one. See if that breaks too.

---

### Post by acl123 on 2008-07-03
Hi, yes, I deleted .mozilla then created a new profile using the command **firefox -p**.
So now Firefox 2 had no extensions installed. I also now have Firefox 3 beta 4 (out of the repository) and that works fine too.
But the full release of Firefox 3 from the mozilla site does not work - it gives me the fatal loop error.

---

### Post by heatblazer on 2008-07-03
The most sucking thing in ubuntu universe was that FF3 :S Sorry to flame it, it`s just true! So much bugs and craps :(

---

### Post by acl123 on 2008-07-04
Yes I must agree, the firefox situation on Ubuntu is terrible.
Every edition of Firefox I have on Ubuntu is filled with crippling bugs that just don't occur on Mac or Windows, even Vista.
I am trying desperately to get away from Firefox 2 because it is still buggy on Ubuntu (address bar doesn't update, back button doesn't work etc). Firefox 3 beta 4 in the repo is unusable after surfing for longer than 5 minutes. Firefox 3 final won't even start. Before this it was freezing flash videos...

---

### Post by acl123 on 2008-07-07
I have just resolved this issue - the problem was with the version of UIM in the repositories. I uninstalled it and Firefox works again.

---

### Post by Master Chief on 2008-07-09
I feel your disappointments, but let's be fair about Open Source software and its developers/maintainers shall we?

If there's anything failing for you, you the user will have to jump in and help with bug triaging.  That's step one.  Complaining won't help anyone.  But again, I know where your pain is coming from.

Note: the versions installed by Ubuntu's Synoptic Package Manager are not the same as the versions available from the MoCo servers so guess what. Download and install UbuntuZilla and see what that brings you. Joy to me ;)

BTW anyone tried SeaMonkey or Flock already?

---

