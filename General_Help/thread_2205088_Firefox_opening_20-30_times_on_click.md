---
title: "Firefox opening 20-30 times on click"
date: 2014-02-11
forum: General Help
---

### Post by Tristan_Williams on 2014-02-11
Sometimes it happens sometimes it don't.

I go to open firefox and 20-30 Firefoxs open at once, and I have to issue "sudo killall firefox" to kill them all or they all freeze in place.
Then I open it back up and it asks if I should reopen the following (30) tabs that I had open last time.

What do I do to stop this???

---

### Post by deadflowr on 2014-02-12
Have you tried making a new profile?
See how that works, and if the problem stops.

It's easy, just
```
firefox -ProfileManager
```
should open the profile manager where you can set/create a new profile, then set it as default and try launching it.

---

### Post by ppjdee on 2014-02-12
i need this problem :D im tired of opening each tab and window

---

### Post by pqwoerituytrueiwoq on 2014-02-12
i would guess ff is restoring your last session
this is the file that contains your saved session to restore
[[IMG]http://www.zimagez.com/miniature/screenshot-02122014-073746am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-02122014-073746am.php")
you can remove it or move/rename it to [FONT=courier new]sessionstore.bak[/FONT]
do this while ff is closed

---

### Post by Tristan_Williams on 2014-02-13
If any of you have this problem, I found the issue and solution.

It turns out that I had installed Firetray for Mozilla Thunderbird.
For some reason, it also got installed for Firefox.
This caused firefox to be "Minimized" rather than being closed.
Each time I closed out of Firefox and reopened it, it opened a new Firefox, plus the one that was already open.

So I simply went and removed Firetray from Firefox. It still worked in Thunderbird.

Problem Solved!

---

