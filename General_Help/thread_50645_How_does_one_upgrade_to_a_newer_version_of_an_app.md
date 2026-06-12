---
title: "How does one upgrade to a newer version of an app?"
date: 2005-07-20
forum: General Help
---

### Post by minghai on 2005-07-20
Hi all,

   Have a newbie question about upgrading apps.  Say I have an app like Firefox 1.0.2 and I want to upgrade it to 1.0.6.  What is the correct process?  Do I just make sure its in the repositories and then "apt-get install firefox"?  Does this remove the old version?  If so, how do I keep both versions?  For example, I might want to have both OpenOffice 1.1.4 and 2.0 beta at the same time.  Thanks!

Ming Hai

---

### Post by adwait on 2005-07-20
Yes, apt-get will auto-magically remove the old version and install the new version. No idea about keeping the old version.....but I guess you can't do that with the apt-get. You will have to download the deb package and install to a different location than the older version.

---

### Post by uniko on 2005-07-21
Well you can have two versions of open office installed as they use different names, not just different version number. I have 2.0 beta and 1.1.3 on my machine. No clue about the rest, sorry.

---

### Post by Jet2k5 on 2005-07-21
Sometimes you can't even remove the old package.  For example firefox.  When you try to get rid of firefox it takes just about your whole desktop with it.  So on your icon you just have to point it to the newest file path.  For me I installed firefox 1.5 I believe in my /home/user.  

( don't mind me if I got the wrong firefox version, doing this from the top of my head)

---

