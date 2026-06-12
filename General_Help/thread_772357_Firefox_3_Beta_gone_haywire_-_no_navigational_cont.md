---
title: "Firefox 3 Beta gone haywire - no navigational controls"
date: 2008-04-28
forum: General Help
---

### Post by employeeno5 on 2008-04-28
Hi. I'm using Firefox 3 beta in Hardy.  Yesterday, midway through my day's computer use, all bookmarking support disappeared. At first I thought this was the the Beta being buggy and erasing my bookmarks (something it had done before). I quickly discovered though that it wasn't just my current bookmarks but the whole of support for them that had disappeared.
The star in the address bar is gone. If I bookmark a page through the right-click menu, or the bookmarking menu up top, nothing is actually ever saved or displayed in the bookmarking manager.

Also, all other navigational tools aren't working. Forward, back, stop and refresh don't work both through there toolbar buttons or any other means. 

I have no idea how this happened. The only change I can recall making is that I had installed Gecko for Wine for its internet explorer clone.

This is my best guess at what I've done to cause all this. If it's not this, I can't remember changing anything else to my setup between normal function and all of this.

I can't seem to uninstall gecko from wine. Uninstalling wine also doesn't solve the problem.

Also, I have uninstalled and reinstalled Firefox 3 through apt-get without results. 
I have uninstalled every package I could find related to FF3 in synamptic and then reinstalled them, also without result.

I installed Epiphany which is working fine. I also don't know why a Gecko issue would screw with Firefox's UI; webpages are still loading quickly and correctly, I just have no normal navigational tools apart from typing in an address or following a link on an open page. I just don't have any better guess at what could have gone wrong. 

I'm pretty lost on this one. I wasn't sure which board was best to ask about this one on.

Has anyone experienced anything similar? Any guesses? Any better way than my current methods to attempt a complete reinstallation of FF3  to see if it helps?

Thanks for any ideas. Let me know if I can answer any questions.

---

### Post by forrestcupp on 2008-04-28
Did you try a purge removal to get rid of your settings, too?
```
sudo apt-get --purge remove firefox
sudo apt-get install firefox
```

You'll lose all of your settings and bookmarks, though.  But since it doesn't work anyway, I guess that doesn't really matter.

---

### Post by employeeno5 on 2008-04-29
The purge went fine as did reinstalling. No errors.

However, there's no change. Firefox still has no bookmarking or navigational support.

I've searched everywhere about this. I can find nothing.

My options are looking like I either move to another browser permanently or reinstall the OS. Both seem a little extreme.

I hoping someone knows what could do this. If completely removing firefox and reinstalling leaves it the same way it leaves me to believe that something else is inhbiting these features rather than these features just being broken. 

That's just deductive thinking though. I've no ideas what this is all about.

Any help is hugely appreciated.

Thanks again, as always.

---

### Post by LosD on 2008-04-30
I have exactly the same problem.

I didn't do anything, I was just browsing, noticed my bookmarks were gone, restarted Firefox. No change. Killed .mozilla. No change. reinstalled Firefox. No change.

WTF?

Edit: Found a fix:


1. Delete all Ubuntu installed add-ons with synaptic if you installed them (not sure if it cured anything, but that's what I did).

2. Start Firefox from the command line with: "firefox -ProfileManager", delete the old profile, and create a new one.

That fixed the issue for me.

You can try 2. without 1., maybe it'll work.

---

### Post by TheLions on 2008-04-30
did you try to install Firefox 2????

---

### Post by employeeno5 on 2008-04-30
I'm sorry to hear you're having the same problem. However, I am glad to hear at least one person is having an identical issue. It makes me feel maybe someone out there knows what's going on.

I haven't yet through searching found anyone else with this issue though or even anything similar or any solutions.

I have not tried installing Firefox 2. To be honest I was just kind of assuming it would work fine given that all other browsers I've tried are working fine. I will try it later tonight though just to make sure.

I've still had no luck. I think it's clear that because clean installations of Firefox 3 produce the same results as soon as it's  opened (not to mention the lack of large number or other people experiencing this) that FF3 itself is not the problem. Rather it has to be that some other program or setting on my Ubuntu setup is breaking or suppressing this part of the interface. I have no idea what that might be though or how to isolate it.

Running Firefox 3 in the terminal produces no strange results or errors. 

I'm hoping this might sound like an adventurous problem to solve for someone much more knowledgeable than I.

I intend for Firefox to be my web browser. If this isn't fixed by the time FF3 is well out of Beta, I'm likely to just back up all my personal settings and reinstall Hardy. I'm hoping that whatever is preventing FF3 from working correctly would be eliminated by that. It seems a bit extreme though and if nothing else I'm pretty genuinely curious at this point about the hows and whys of this. After all, the learning process is one of my favorite things about Linux. It's just not quite as fun when I feel like I'm making no progress. 

Well, maybe someone else has some ideas?

Thanks again.

---

### Post by employeeno5 on 2008-04-30
Ah! I didn't see your edit at first because I read your reply though my email subscription to this thread.

Awesome. Thanks for the advice. I'll try this out later at home. I'm still worried it may not work because I'd previously deleted all my firefox info and uninstalled all extensions and removed all related packages including addons. 

I will try it out again using your steps though.

It won't be until later this evening but I'll report back.

Glad you found a solution for yourself if nothing else. :)

---

### Post by employeeno5 on 2008-04-30
That fixed it. Thanks! 

I wonder why my previous attempts weren't working and why any of this happened in the first place.

Still, I'm glad it's solved.

Thanks again!

---

