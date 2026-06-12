---
title: "Thunderbird 1.5.0.8 update is broken"
date: 2006-11-22
forum: General Help
---

### Post by phstpok on 2006-11-22
Earlier today automatic updater had a Thunderbird security bugfix update, as well as a pile of others. Worked fine until I checked my preferences. Edit>Preferences and nothing happened. No preferences window nada. Decided to file a bug report with Mozilla, so clicked Help>About Thunderbird to get the version number, but got an error window re: xml yadda yadda broken. I filed a bug report with Mozilla but was told to file with Ubuntu. The Ubuntu bug report page is down (error 503) so thought I'd post here to see if anyone else has had that problem. There are more. View>Themes and Extensions also have an XML error. I came here to post this earlier, but got sidetracked when I read about a workaround for the cpu goes to 100% in edgy, which resulted in my previous post [http://www.ubuntuforums.org/showthread.php?t=304686](http://www.ubuntuforums.org/showthread.php?t=304686) .

I'm writing this from the live edgy cd, about to do a re-install (unless I can find a repair install option). I will then install Tbird 1.5.0.8 before anything else and see if the bugs persist. If they do, I'll file a bug report and update this thread.

---

### Post by Unconscious on 2006-11-22
I also am experiencing this problem. I cannot forward anything.

Is there any way to back out that update?

---

### Post by Ramses de Norre on 2006-11-22
This will give you the previous version again:
```
sudo aptitude install mozilla-thunderbird/edgy
```

---

### Post by phstpok on 2006-11-23
After other problems manifested when I tried a workaround for the cpu 100% bug,

[http://www.ubuntuforums.org/showthread.php?t=304686](http://www.ubuntuforums.org/showthread.php?t=304686)

 I re-installed 6.10 then installed thunderbird via apt-get install thunderbird. This installed version 1.5.0.8, which runs fine without any of the problems in my original post. I then copied my entire thunderbird profile from the previous installation, which includes all themes and add-ons, conjecturing that one of these may have been incompatible with the update, but I could not replicate the behaviour previously experienced.


I have since re-installed automatix2, from there installing the same applications as previously, and still no problems. I've also installed all other apps previously installed with no trouble. The only difference between the two Ubuntu installations is that I tried a number of apps, installing and removing until I was satisfied with my choices.

I can't really draw any conclusion from this, but I hazard a guess that the original thunderbird update was itself flawed, or the actual update process itself damaged some of the xml files (I was getting various xml errors). I can't think of anything else I might have done in my previous Ubunbtu installation that would have caused the errors in thunderbird. That also was a fresh installation, not an upgrade from dapper. 

Might as well call this problem resolved, but with no clearly known cause and therefore no clearly known remedy.

---

### Post by Dr.Who on 2006-11-24
Attention, 1.5.0.8 seems broken anyway, deleting messages!

[https://bugzilla.mozilla.org/show_bug.cgi?id=360409](https://bugzilla.mozilla.org/show_bug.cgi?id=360409)

[http://forums.mozillazine.org/viewtopic.php?t=487248](http://forums.mozillazine.org/viewtopic.php?t=487248)

a downgrade is recommended.

---

### Post by A-star on 2006-11-27
and how should we downgrade?

---

### Post by pmgant on 2006-11-27
After updating Thunderbird I am also having a problem. I can read email from my ISP but I cannot send. Each time I try to send a message I get a request for the password but the information I give is ignored and no entries are made in the file signons.txt.

P M Gant

---

### Post by Dr.Who on 2006-12-12
downgrade is possible with synaptic to version 1.5.0.2

---

### Post by yabbadabbadont on 2006-12-13
Turns out that e-mail messages from launchpad.net, confirming the submission of a bug, has the referring messageid set to the id of that same message... which is one of the things that triggers the bug in thunderbird.  (The message is downloaded and stored, but not visible.)  I had to edit my Inbox file directly to see the message.  The only reason I knew it was there was that thunderbird showed that it was downloading two messages, but only one showed up...  Now I'm wondering if I've missed any other messages since, once the Inbox is compacted, the hidden messages are removed.

---

