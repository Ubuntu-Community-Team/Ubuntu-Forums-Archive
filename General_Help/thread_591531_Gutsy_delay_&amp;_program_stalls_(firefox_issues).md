---
title: "Gutsy delay &amp; program stalls (firefox issues?)"
date: 2007-10-25
forum: General Help
---

### Post by JoshuaJamZ on 2007-10-25
Wasn't sure how to search for this and not really positive how to post it either. But, am experiencing some problems after a Gutsy install.

I first did a Gutsy upgrade from Feisty. Had problems with my dualview not working, so did a fresh install. This fixed my dualview problem, but now have a couple other probs which may or may not be related and may or may not be easily solved :)

First of all, when I click anything, open a window, the top menu bar, applications, system, etc, I get about a 1 second delay before the window opens, menu pops up, etc... this is very annoying as it slows me down quite a bit overall. I did not have this delay in Feisty nor after doing the Gutsy upgrade, but do now after the fresh install. I've checked all the settings I could think of hoping there was a very simple solution... perhaps there is, but I am stumped.

The other problem I have is that I get very frequent program stalls. This happens quite a bit when using Firefox... I will be on a web page, just scrolling around and it stalls, going to black and white... sometimes it comes right back, but other times it stalls indefinitely and have been able to use xkill at times to kill the app, other times, though, have had to ctrl-alt-backspace... 

I'm not sure if the first issue and second issue are related ot not, but I get the feeling that Firefox is causing some probs and perhaps it is related to the second issue...

Of course, I have also used Opera a bit and seem to experience issues with it as well...

I did notice a thread referring to possible Firefox/Java problems.. but not sure if that is the problem I am having, thought it better to start a new topic...

I just want to comment also that even though I'm having some probs with Gutsy, I am still happy to have made the jump... once all the gears are properly oiled and moving, it should be good... 

Thanks in advance for any assistance...

---

### Post by scottmuz on 2007-10-25
On the menu speed issue try adding this like to ~/.gtkrc-2.0
gtk-menu-popup-delay=30

There is a known gnome issue that the first click on the main menu can be slow
(particularly on slower PCs like mine).

Strangely for me firefox is much stabler since upgrading to gutsy (I got at least 
once hang/crash a day on fiesty).

---

### Post by JoshuaJamZ on 2007-10-25
Thanks for the reply...

I do not have a .gtkrc-2.0 file in my home directory... :confused:

So, is there something I should have installed that is not?

Or should I just create it?

---

### Post by JoshuaJamZ on 2007-10-26
Ok, was messing with my second display, dualview SVIDEO out on NVIDIA GeForce and noticed that the delay is not present there. I've had System > Preferences > Appearance > Visual Effects set to Extra. This also causes the windows borders to disappear on the SVIDEO display. Not a major problem for me, since right now, just want that to watch movies and play games.

So, I switched Visual Effects  to None and the delay goes away. I like the Extra visual effects and hate to have to choose between them and having no delay. But, perhaps this bit of information will help someone else in identifying the problem and presenting a solution.

So, any ideas then? :)

---

### Post by scottmuz on 2007-10-26
Just create an empty ~/.gtkrc-2.0 file and add the line above.

---

### Post by JoshuaJamZ on 2007-10-26
> **scottmuz said:**
> Just create an empty ~/.gtkrc-2.0 file and add the line above.

Tried this last night, but didn't work. I think it's a problem with Compiz and NVIDIA. 

I can switch Visual Effects to NONE and it's fine. This also gets rid of another problem on my second display with the windows borders going missing. 

So, do I want my Ubuntu fast and efficient or do I want it pretty? heh... would really like both.

Any other ideas?

EDIt:

I don't want to make this thread a total mess by throwing a bunch of other problems in, but I'm experienceing other issues as well, like Firestarter for example which just crashed as I was scrolling through active connections. It has done this several times before, since the Gutsy install, I just hadn't tackled this issue yet. 

But, a thought occurs to me. I did the fresh install, but I renemed my home folder before-hand, created a new account of the same name, then after the install was finished, renamed the new home folder created during install and renamed my old home folder back.. so I am again using the old home folder. Is it possible that some old settings are causing me some problems?

---

