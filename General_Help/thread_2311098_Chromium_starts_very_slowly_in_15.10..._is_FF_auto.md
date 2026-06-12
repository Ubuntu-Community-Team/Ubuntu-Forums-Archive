---
title: "Chromium starts very slowly in 15.10... is FF auto preloaded? how to make faster?"
date: 2016-01-24
forum: General Help
---

### Post by anotherChris on 2016-01-24
I just installed Lubuntu 15.10 and Chromium is now taking about 8 seconds to start after I click on it (seems like a lifetime).  This is compared to about 2 seconds for FF.

(It's not just the first time after booting, it's every time, and I've run a number of "experiments" to see if the slow start is circumstantial. It doesn't seem to be.) 

My computer is a **Dell Inspiron 1545 laptop Celeron 2.16GHz 2GB RAM 160 GB hard drive**.  Previously, I had Lubuntu 11.10 and Chromium (older version) took about 1 second to start.

I installed Chromium using the Lubuntu Software Center.

I have looked at both Chromium and FF in Task Manager when starting and neither makes RAM go over 50%.  FF puts CPU at about 80% when opening, while Chromium goes up to 100%.

**Questions:**
(1) Since FF is the default browser, is FF somehow preloaded, and does this account for its faster start?
(2) If I use the Preload program, would it speed up the start time only after a boot or each time the browser is started?
(3) Besides the Preload program, is there any way to make Chromium start faster?  I noticed that in [this thread]("http://ubuntuforums.org/showthread.php?t=2301795"), the user fixed slow Chromium by re-installing Ubuntu.  This doesn't quite make sense to me.  My installation of 15.10 is competely fresh.  Would it make sense that re-installing either the OS or the program would make it start faster?

Thanks!

(PS. Before anyone says, "just use FF"... I like the way Chromium handles its start page (New Tab page).  It has a Bookmarks Toolbar that is non-persistent once you leave that page, unlike FF, which maintains the Bookmarks Toolbar even when you leave the start page.  By bookmarking the Bookmarks Manager and adding bookmark folders to the Bookmarks Toolbar, I can very quickly navigate anywhere in my extensive bookmarks while preserving the window space that is lost to the Toolbar in FF.)

---

### Post by midgleyi on 2016-01-24
I installed 15:10 yesterday and I'm finding the same with Chromium. Firefox loads OK - but that doesn't seem to perform as well on my old machine. Like yours, mine is a completely new/clean install so there seems no justification to just re-install.

Just timed it and its about 15 seconds on my old P4 2.4G/1G ram.

---

### Post by anotherChris on 2016-01-24
> **midgleyi said:**
> Firefox loads OK - but that doesn't seem to perform as well on my old machine. 

Yeah, I started using Chromium originally because it performed much better than FF.  This is a real bummer...

---

### Post by Christopher_Stayne on 2016-01-24
I  also use Chromium.  I installed it on a fresh install of Kubuntu 15.10 and it seems to take forever to load (probaby again about 8 secs.)  This seems to be an issue with Chromium itself.

---

### Post by sammiev on 2016-01-24
> **anotherChris said:**
> I just installed Lubuntu 15.10 and Chromium is now taking about 8 seconds to start after I click on it (seems like a lifetime).  This is compared to about 2 seconds for FF.

(It's not just the first time after booting, it's every time, and I've run a number of "experiments" to see if the slow start is circumstantial. It doesn't seem to be.) 

My computer is a **Dell Inspiron 1545 laptop Celeron 2.16GHz 2GB RAM 160 GB hard drive**.  Previously, I had Lubuntu 11.10 and Chromium (older version) took about 1 second to start.

I installed Chromium using the Lubuntu Software Center.

I have looked at both Chromium and FF in Task Manager when starting and neither makes RAM go over 50%.  FF puts CPU at about 80% when opening, while Chromium goes up to 100%.

**Questions:**
(1) Since FF is the default browser, is FF somehow preloaded, and does this account for its faster start?
(2) If I use the Preload program, would it speed up the start time only after a boot or each time the browser is started?
(3) Besides the Preload program, is there any way to make Chromium start faster?  I noticed that in [this thread]("http://ubuntuforums.org/showthread.php?t=2301795"), the user fixed slow Chromium by re-installing Ubuntu.  This doesn't quite make sense to me.  My installation of 15.10 is competely fresh.  Would it make sense that re-installing either the OS or the program would make it start faster?

Thanks!

(PS. Before anyone says, "just use FF"... I like the way Chromium handles its start page (New Tab page).  It has a Bookmarks Toolbar that is non-persistent once you leave that page, unlike FF, which maintains the Bookmarks Toolbar even when you leave the start page.  By bookmarking the Bookmarks Manager and adding bookmark folders to the Bookmarks Toolbar, I can very quickly navigate anywhere in my extensive bookmarks while preserving the window space that is lost to the Toolbar in FF.)

I can not say much for 15.10 as I was testing lubuntu 16.04 and FF gives no indication that it's even loading. I had it installed on a SSD so speed wasn't really an issue.

I found that anything selected didn't give an indication it was loading. So just saying.

---

### Post by anotherChris on 2016-01-24
> **sammiev said:**
> I can not say much for 15.10 as I was testing lubuntu 16.04 

Here's some feedback on Lubuntu development for developers...

I went from Mac to Windows around 2000, then Windows to Ubuntu 8.10 about 7-8 years ago.  Then I went to Lubuntu 11.10 around 2011.

Lubuntu 11.10 was super fast in loading and never gave me any problems.  I only upgraded because everything was starting to get completely broken, and I couldn't use Google Drive, watch videos, etc...

Upgrading to 15.10 is the first time I have ever noticed diminished performance.  Not only this Chromium issue, but the OS loads noticeably slower and the other programs are a little sluggish too.

I think my hardware should be adequate.  I'm a little disappointed.  Not that I would switch to anything else, but I'm just saying.  I was a very early adopter of FF, too, but I dropped it because of feature creep.  Would hate to see Lubuntu Mozillafied.

---

### Post by vasa1 on 2016-01-24
> **anotherChris said:**
> ... and I've run a number of "experiments" to see if the slow start is circumstantial. It doesn't seem to be.) 
...
(1) Since FF is the default browser, is FF somehow preloaded, and does this account for its faster start?
(2) If I use the Preload program, would it speed up the start time only after a boot or each time the browser is started?
(3) Besides the Preload program, is there any way to make Chromium start faster?  I noticed that in [this thread]("http://ubuntuforums.org/showthread.php?t=2301795"), the user fixed slow Chromium by re-installing Ubuntu.  This doesn't quite make sense to me.  My installation of 15.10 is competely fresh.  Would it make sense that re-installing either the OS or the program would make it start faster?

Thanks!

(PS. Before anyone says, "just use FF"... I like the way Chromium handles its start page (New Tab page).  It has a Bookmarks Toolbar that is non-persistent once you leave that page, unlike FF, which maintains the Bookmarks Toolbar even when you leave the start page.  By bookmarking the Bookmarks Manager and adding bookmark folders to the Bookmarks Toolbar, I can very quickly navigate anywhere in my extensive bookmarks while preserving the window space that is lost to the Toolbar in FF.)

Could you tell us what experiments you tried?

Maybe run Chromium via the terminal and post the output from the terminal here?

Have you played with chrome://settings, turning off what you don't want, including HW acceleration?

Have you tried a new user with Chromium? Does that start faster? Is your Chromium synced to anything?

Again, could you tell us what experiments you tried?

---

### Post by midgleyi on 2016-01-25
In my case, nothing in Chromium advanced settings seems to make the slightest bit of difference. Tried turning off HW accel, and all sorts in there. If I run TOP whilst Chromium is loading, the memory usage isn't that bad, but CPU is getting thrashed - I can see it hitting 99% for several seconds.  Firefox loading by comparison is a lot easier on the CPU.

---

### Post by anotherChris on 2016-01-25
> **vasa1 said:**
> Could you tell us what experiments you tried?

Maybe run Chromium via the terminal and post the output from the terminal here?

Have you played with chrome://settings, turning off what you don't want, including HW acceleration?

Have you tried a new user with Chromium? Does that start faster? Is your Chromium synced to anything?

Again, could you tell us what experiments you tried?

I tried typed ```
chromium-browser
``` into the terminal.  It opened Chromium like normal... in about 8 seconds... but there was no other output from the terminal.  It just went to another command prompt.

My experiments were things like plugging into a power source vs battery, opening before or after various programs, with other other programs running, from the panel vs. the menu, etc.  I think these are all things Ubuntu users normally wouldn't try.  Anyhow, nothing made any difference.

By new user, do you mean in Chromium or a new user account on my computer?  I don't sign in to Chromium, so there are no users in it.

I'm not sure what you mean by synced, but I think the answer is almost definitely "no".  I just installed Chromium and opened it, and it was slow.  I haven't changed anything since except for surfing the web.

I didn't try messing with hard ware acceleration.  I will try that after I post this message.  If it changes something, I will post again.  If I don't post again in the next few minutes, it means HW acceleration had no effect.

Thanks.

> **vasa1 said:**
>  turning off what you don't want, including HW acceleration?

Turning off hard ware acceleration reduced start time to about 6 seconds, and in a very specific way.  

Chromium used to appear in the panel without a window actually being open, then about 2 seconds later, the window would come up.  With hard ware acceleration turned off, the Chromium window appears at almost the same time that Chromium shows up in the panel.

This is better, but shouldn't programs just start immediately?  VLC media player comes up almost before my finger is finished with the mouse button.  And in Lubuntu 11.10, there was almost no wait time for Chromium to start.

Help me vasa1 kenobi. You're my only hope.

[IMG]http://www.techweekeurope.co.uk/wp-content/uploads/2010/12/Star-Wars-Leia-hologram.jpg[/IMG]

---

### Post by anotherChris on 2016-01-29
[IMG]http://36.media.tumblr.com/3e089c3ffd63117eda44f577206a9ae9/tumblr_nkifqneFzD1t0bw5uo1_500.jpg[/IMG]

---

