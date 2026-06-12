---
title: "Firefox: Two Windows, Can't Click"
date: 2014-10-08
forum: General Help
---

### Post by wyth on 2014-10-08
In recent iterations of Firefox, if I have two windows open, I can only click or type in one window. The other window is useless unless I close the other window, or drag the tab out of the useless window to a third window -- which renders one of the other windows useless. 

Example: I'll have one window open with a news article, and another window open with Wikipedia. I read something in the news article I want to look up, so I got to the Wikipedia window, but I can't click into the search bar or type anything -- nothing happens. If I drag that Wikipedia tab out to a third window, then I can type in it, but the previous window or the original window will be useless. 

It doesn't matter what the sites are, this happens as soon as a second window is opened, and it doesn't matter if it's a normal window or private. It's also the same in unity or gnome, and it's happened on multiple machines, one running an Intel GM965 gfx card, the other running an Nvidia GeForce 8600GT gfx card. 

I've noticed this for a few months now, so it's been happening for quite a few iterations of the latest Firefox. Is anyone else having a similar issue? Is this an easy fix and there's something in the about:config I'm just not aware of?

---

### Post by vasa1 on 2014-10-09
Operating system? Version? Desktop environment? Window manager?

You say it happens on both Unity & GNOME? Are these separate installs or do you have both desktop environments installed side-by-side?

Just to be clear, I can't replicate your problem and don't recollect experiencing anything like it or reading about it happening to others.

---

### Post by sgt.fish on 2014-10-15
I'm having the same, or similar, issue.

Having multiple windows of Firefox open occasionally bugs it out such that I cannot get my cursor to focus in all but one window.

Things I have noticed:
[LIST]
[*]Keyboard shortcuts input to any non-functional window will direct to the functional window 
[*]Frequency of bug seems to correlate with number of windows/tabs (although I may just always have many open) 
[*]Closing the functional window passes functionality (randomly?) to one non-functional window 
[*]Consolidating all tabs to one window (via dragging or closing out) returns normal functionality to any new window that is made after 
[/LIST]

I'm running Ubuntu 14.04, Unity 7.2.2, Compiz 0.9.11.2, and Firefox 32.0.3

---

### Post by wyth on 2014-10-26
> **vasa1 said:**
> Operating system? Version? Desktop environment? Window manager?

You say it happens on both Unity & GNOME? Are these separate installs or do you have both desktop environments installed side-by-side?

Just to be clear, I can't replicate your problem and don't recollect experiencing anything like it or reading about it happening to others.
Operating System and Version: Ubuntu 14.04 (in the sig)
Desktop Environment: Gnome Shell 3.10 and Unity 7.2.3
Window Manager: Well, Mutter 3.10 in Gnome and Compiz 0.9.11.2 in Unity
Firefox: 33 (but the issues began a few versions back)

Unity was installed first, and the problem first began happening there. I installed Gnome Shell alongside it -- i.e. I can choose either one from the login greeter. 

And it looks like I'm not the only one who's experienced it. Maybe time to file a bug?

---

### Post by wyth on 2014-10-26
I can confirm all four of your points -- same things happen to me when Firefox loses the mouse.

The only thing I've noticed recently (and may be a way around the issue) is when I can't use the mouse or type in a tab, I move that tab to a new window -- which gives it functionality -- and then move it back to the original window, which returns functionality to that original window. 

Sometimes that removes functionality from the other window, sometimes it doesn't. At this point, I haven't noticed a pattern either way.

---

### Post by wyth on 2014-11-11
Hey, are you still having this problem? If so, I have a couple of questions:

First, did you notice any difference after the latest updates? I'm not on version 34.0, and although it's still happening, it took hours before it occurred. (I almost responded back to this thread that the problem was resolved with an update, and when I tried to open this thread in a new window, I lost the ability to click on it again.)

Second, have you tried starting the browser in safe mode (with all the extensions disabled) and see if it's something there? I'm doing that now, and after about an hour of two-window use, I've noticed no problems. So maybe this is an extension issue? If so, time to narrow down which one. I haven't found any mention of this problem outside of our two examples, and since we're both on Ubuntu, I wonder if it isn't an issue with one of the Ubuntu or Unity auto-installed extensions.

**EDIT:** An hour after I posted this, I lost clickability in safe mode -- so it's not an extension. The only other thing I did was play a video in totem, otherwise I've just been surfing between the two windows, trying to respond in forums in both. (The video was already open when I went into safe mode, but paused; only noticed I lost clickability after I hit play.)

If it's not an extension, it's either an issue with Firefox, or the way Firefox is interacting with something else. Since it happened after I opened totem, maybe it has something to do with totem-mozilla? Removing now and will respond back here if it makes a difference.

---

### Post by sgt.fish on 2014-11-11
Pretty sure I'm still getting this problem on FF 33.0.

I've noticed hitting ctrl+J to open the downloads window, then closing it, seems to allow focus back into a particular window temporarily.

It's not the greatest fix but at least it's something.

---

### Post by wyth on 2014-11-12
WHOO-HOO! 

Cheers, I'll try that trick and keep looking.

---

### Post by wyth on 2015-02-26
_**UPDATE**_

Opening the downloads window does not make a difference with this issue, which persists in Firefox 36.0.

However, clicking on the insensitive window's **site identity button** *does *make a difference, although the fix doesn't always persist. the **site identity button** is the little button in the url address bar to the left of the actual url. On this page, the icon is a little globe; on some pages it's a padlock, on others it's a warning sign. 

[IMG]https://support.cdn.mozilla.net/media/uploads/gallery/images/2014-06-26-21-38-46-78f915.png[/IMG]

[IMG]https://support.cdn.mozilla.net/media/uploads/gallery/images/2014-09-10-16-56-42-1aa573.png[/IMG]

Click on the site identity button, and a bubble will pop up saying whether the site is secure or not, and there will be a **More Information **button in that bubble. You must click on **More Information** for this trick to work. 

When you click on More Information, yet another bubble will pop up showing **Website Identity**, **Privacy & History**, and **Technical Details**. 

[IMG]http://s12.postimg.org/4megrtcct/Screenshot_from_2015_02_26_03_03_13.png[/IMG]

Close this second bubble, and you will regain possession of the  insensitive window, enabling you to once again do things like click in search  boxes and type words on that page.

If you go back to the other window that was not insensitive, it may have become insensitive. Just do the same thing -- click on the **site identity button***, *then click on the pop-up bubble's **More Information** button, and then just close that window.

What a weird issue. Firefox seems to have really upped its game in recent versions, and this is an odd problem that I don't recall ever happening in the past. I still don't know if it's just a Linux issue, or even just an Ubuntu issue. It's not happening on my Windows machine, and I don't think it's even happening in Firefox 33.0 on a live disk. Just strange.

---

### Post by William_Ashton on 2015-08-11
Has there been any news regarding this issue? I started noticing these same symptoms yesterday. Unfortunately, they didn't occur in the same place at all. If the cause was similar I might be able to port a fix.

I had the symptoms on Fedora 20, Gnome 3 yesterday using Google Chrome, and again after updating to Fedora 22 this morning. One other difference: while the problem seems to be triggered by having multiple windows of Chrome open, the symptoms affect all open windows even outside Chrome. I did notice that unplugging my external monitor reset things enough that it fixed the problem, but it didn't take long for it to come back. (A minute and a half or so)

Very sorry for posting a Fedora/Chrome problem in an Ubuntu/Firefox thread, but I'm not really seeing anything like this anywhere else.

---

