---
title: "Firefox mem leak? with extra info"
date: 2007-12-06
forum: General Help
---

### Post by wizardStan on 2007-12-06
Hi,
I know this thread exists quite a lot (that of Firefox eating a lot of memory) but I've yet to see one with the kind of testing that I just went through.  I need to know, with the following information in mind, what's the next step?
I apologize if these specifics may have already come up, but I searched and couldn't find anything more than generic "Firefox isn't freeing memory"

To start with, I'm on gutsy, regular x86, 2.4ghz, 512 meg ram, everything updated to latest, Firefox currently sitting at 2.0.0.11, but this has been a problem for some time now.
I've followed a number of tweaks to getting better performance, but there still seems to be a memory leak.  Here's what I did to track it:
I have a bookmarks subfolder titled comics.  It is all the webcomics that I read, about 30 or so.  At this point, Firefox is only using a little memory.  We'll say 40 megs, for the sake of a base point.  Choosing "open all in tabs" I get a memory spike, as expected.  Closing all the tabs (save one, obviously) recovers a lot of memory, but far from all of it.  10 to 20 megs is never recovered, leaving firefox using about 55 megs or so.
Interesting thing, if I then reopen every single tab, I get the same memory spike, but closing all the tabs again restores it to the 55 megs.  It's almost like it's caching something from each web page or something.
Here's the kicker, though.  If I restart firefox, I get back to just 40 megs, if I then open every page one at a time in a single tab, it remains at about 40 megs (give or take).   I then opened all in tabs again, and closed them, just to be safe.  Sure enough, jumped to 55 megs, never to return to 40.
So, it appears to me, opening new pages in tabs seems to somehow cache the tab or something, such that closing them doesn't return all used memory.  The first time they're opened, memory is effectively lost, but subsequent times it is not.  I did notice that, if the web page changes, then the memory leaks again.  I reopened the tabs several times as a few of the web comics were performing updates and noticed that the memory usage slowly crept up a couple of megs.

I've set browser.cache.memory.enable=false, browser.sessionhistory.max_entries=0, browser.sessionhistory.max_total_viewers=0, and browser.sessionstore.max_tabs_undo=0 in order to reduce memory usage as far as I have, but this last bit is troubling.  Over the course of a session, I might open hundreds of tabs (not counting the web comics I read) which typically with each one leaking a small amount of memory, even after all tabs are closed and the only tab open is google.  Like I said, though.  If I do all my browsing in a single tab, I never experience this memory leaking.  Weird.

So that is it.  Does anyone have any advice at all?  Is there another setting I don't know about?  Is it worth filing a bug report, and if so, (total noob question) how?
Thanks for your time.

---

### Post by somegirl on 2007-12-14
I've noticed this problem more in Windows XP than Ubuntu, mainly because it causes total system lag and I have to close Firefox to release the memory. 

Anyway, here's what I found via the Firefox forums: [http://plugindoc.mozdev.org/faqs/memusage.html#leaky-extensions](http://plugindoc.mozdev.org/faqs/memusage.html#leaky-extensions)

It covers plugins that cause leaks, what is and isn't a problem, and also to answer your question about filing a bug report, my suggestion would be no. They're aware of the problem and various causes.

---

