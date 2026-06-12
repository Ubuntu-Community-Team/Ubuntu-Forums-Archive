---
title: "Firefox &amp; Gmail"
date: 2007-02-18
forum: General Help
---

### Post by the ev on 2007-02-18
I have a bit of a weird problem; for some reason, Firefox no longer loads Gmail.  It used to, but now it doesn't.  The loading text comes up on the upper left of the page, then in red on the upper right, and the little wheel turns, and the status bar flickers and updates its little messages quite rapidly (Transferring data, reading data, etc.) but nothing ever loads.  I'll let it sit there for five or so minutes, and when it finally says done, I'm presented with a perfectly white nothingness.  

I can get to Gmail just fine using Epiphany, so I believe it's a Firefox problem.  I've tried clearing the cache, but that didn't seem to work.  Help!

---

### Post by DJ_Peng on 2007-02-18
What version of Firefox are you running, and have you installed any new extensions right before you started having the problem? Also, have you applied any updates through Ubuntu lately?

---

### Post by the ev on 2007-02-18
I think Ubuntu might have updated Firefox a few days ago, but I don't remember for sure. Is there anyway to check that?

I've installed no new extensions, and I'm running ver 2.0.0.1.

---

### Post by DJ_Peng on 2007-02-18
Go to Help > About and check the build information at he bottom of the screen. Although if Ubuntu updated Firefox a few days ago I'd be curious to find out what they updated. We're currently testing release candidates for Firefox 2.0.0.2 and Firefox 2.0.0.1 came out back in December.

You may want to check in at the [MozillaZine Forums]("http://forums.mozillazine.org/index.php") if you can't find an answer around here. I can say that I'm having on problems accessing Gmail on my comp.

---

### Post by the ev on 2007-02-18
Here's what's on the About screen, about the build:

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.1) Gecko/20060601 Firefox/2.0.0.1 (Ubuntu-edgy)
```

I might have been wrong about Ubuntu updating it, I just seem to have a faint memory of seeing it on the list of updates.

---

### Post by DJ_Peng on 2007-02-18
Okay, that not a Firefox update, but it points out something that ticks me off about Ubuntu's Firefox builds. The date of 2006-06-01 is flat out *impossible*, especially for a 2.0.0.1 version. On the first of June of last year we weren't even out of the alpha stage for Firefox 2 (which was still called Bon Echo at that point). This is part of why I stopped using Ubuntu's builds for Firefox and Thunderbird, but that's another rant.

Check to make sure you're allowing JavaScript. When I have to check my Gmail on another computer that has JavaScrip disabled this is exactly the behavior I'd get.

---

### Post by the ev on 2007-02-18
I have Javascript enabled.  For kicks, I disabled it and tried to get to Gmail, and I got their little error page saying I had javascript disabled.  I then re-enabled it, and I got the same behavior. 

Back in Ephiphany, I switched my Gmail layout to Standard without Chat, and then tried accessing it again in Firefox, and it twitched for a lesser amount of time before leaving me with a blank window.

Any other suggestions?

---

### Post by DJ_Peng on 2007-02-18
You may want to get into the non-JS pages, then re-enable JS and try switching back. Other than that I don't know what to suggest so I'll let someone else pick things up from here.

And just as an FYI. it looks like Firefox 2.0.0.2 could come out pretty soon. It looks like Release Candidate 4 (the current RC) will become the version to be released, barring any last minute problems. That happened with RC3, but things look pretty good for RC 4.

---

### Post by Ramses de Norre on 2007-02-18
> **DJ_Peng said:**
> Okay, that not a Firefox update, but it points out something that ticks me off about Ubuntu's Firefox builds. The date of 2006-06-01 is flat out *impossible*, especially for a 2.0.0.1 version. 

I've got the same build date on edgy here, and I just checked and two friends of mine also have exactly the same line (I checked in apache's log).

---

### Post by the ev on 2007-02-18
Yeah, that didn't seem to work (as far as fixing the standard view), though I was able to load up the HTML view.  Oi...

I'll pick this up on Mozilla's forums, see if they have any input.  Thanks for your help!

---

### Post by DJ_Peng on 2007-02-18
No problem, The Ev. I hope I was able to help.

@Ramses de Norre:
Here's the thing: Firefox 2.0.0.1 came out on 19 December according to the [Release Notes]("http://www.mozilla.com/en-US/firefox/2.0.0.1/releasenotes/"). According to the [Firefox 2 project page]("http://http://wiki.mozilla.org/Firefox2") Firefox 2 shipped on 24 October. The build date you show is the same as was first used on the Edgy Live CD and has never bee changed. One thing we use on the MozillaZine forums is the build date in use to help us know which build is being used. A build date of 1 June for Firefox 2.0.0.1 is so bogus as to be useless.

For what it's worth, here's my build ID (for the latest nightly build):
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.2pre) Gecko/20070218 BonEcho/2.0.0.2pre ID:2007021804

---

### Post by the ev on 2007-02-18
The posted topic I created on MozillaZine can be found [here]("http://forums.mozillazine.org/viewtopic.php?t=521803"), if anyone cares to follow up on the problem.  

No one's responded yet; I guess they're not as quick on the draw as Ubuntu Forums is! ;)

---

### Post by DJ_Peng on 2007-02-18
Sometimes they are, sometimes they're not so quick. I can depend on who's on at a particular time, just like here. I'm sure some will get back to you before too long.

---

### Post by the ev on 2007-02-18
Oh I've no doubt they're just as good as Ubuntu Forums; the comment was meant as a compliment to Ubuntu Forums, not a knock at MozillaZine - thus the smiley. :D

---

### Post by the ev on 2007-02-19
Ahh - so I think I've solved it.

If I go to View --> Page Style --> Global Style and deselect "No Ads", Gmail loads.  

When I stumbled upon that option, I was reminded of ahelper1a's (from the Mozilla forums) post mentioning AdBlock/AdBlock Plus, and thought "what the heck, I might as well try it"; looks like it paid off.  I suppose the page style is built in to the browser, as I don't have either AdBlock or AdBlock Plus installed.

Don't know how or why that fixes the problem, but I'm just thankful I can check my Gmail in Firefox now.  Not that I have any qualms against Epiphany, but it's tedious to have two browsers open at the same time for stuff that I should be able to do in one.

I'm curious to know how that setting either got turned on, or started causing problems with Gmail; I've never changed that setting before, and yet there was a time when Gmail was working.  Maybe Google changed something on Gmail's page that makes Firefox think different of it? 

Or maybe I like to change browser settings when I sleepwalk?

---

### Post by DJ_Peng on 2007-02-19
You must have an extension that gives you that option. All I show under Page Style are No style and Basic Page Style, neither of which give me any options, and I have Adblock Plus installed on this box. I'm glad you have it fixed though.

---

### Post by the ev on 2007-02-19
Yeah, the guys over at MozillaZine pointed out the fact that I had a Global Sytle set through Stylish, and that when Google updated the source code for their page, they must have included something that Stylish was set to block.  I've since removed the filter and it works fine.  I had totally forgotten I had that loaded.  Silly really, but hey - whatever, it works.

So FYI to all you Stylish users: the global style "No Ads" breaks Gmail (as of today, at least). [-X

---

### Post by jcmhunting on 2007-03-01
I had the problem with Gmail crashing Firefox and fixed it with

Edit > Preferences > Content > Load Images Automatically > Exceptions > Allow mail.google.com

---

### Post by indeterminate on 2007-03-04
Hmm. I have this problem too, and none of these solutions helped. I'll keep looking.

---

### Post by indeterminate on 2007-03-06
Turns out it was a "glitch" on google's servers. It fixed itself after a day or two.

Good work, ubuntu team! :)

---

### Post by DJ_Peng on 2007-03-06
Coolness. Let's hope they won't have that glitch again for a while.

---

