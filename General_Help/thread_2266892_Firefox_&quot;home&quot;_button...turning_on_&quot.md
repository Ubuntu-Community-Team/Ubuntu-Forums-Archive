---
title: "Firefox &quot;home&quot; button...turning on &quot;are you sure?&quot;"
date: 2015-02-26
forum: General Help
---

### Post by harelb on 2015-02-26
Hi,
I hope this is the right place on ubuntuforums.org for firefox questions...google "site:ubuntuforums.org firefox" did not turn up a specific forum area in the top links..so here goes.

Background: I keep on firefox anywhere between 20 to 40 tabs open as my "homepage" to be there when I launch. I know, not idea..and I do know html and sometimes combine several pages into a new page that links to them..but I have so many projects, research areas, work related, finances, hobby etc, that it's never going to be less than 20 and usually quite a few more than that.

So it's a small disaster when I accidentally hit the "home" button because then it tries to load and launch ANOTHER copy of each of those 20 30 40+ tabs! It happens only 2 to 4 times a year very roughly but it just happened again the other day and it's a real headache

The other day it wasn't even the usual reason (trying to click on the down-pointing arrow", or downloads button/icon, next to the home page icon) but instead "F11" button for full screen (into or out of) for firefox and it didn't do so I clicked again and the delay was just as I tried to click on a TAB, the entire Window for firefox moved up exactly in time for my click "on the tab" to become a click on the homepage icon.

If there's no way to use Config: how about an add-on? I could not find any anywhere..There are lots of add-ons out there, like Leechblock which I use for examples.. this would seem tob e 100 times less work (or 1,000 times) than creating Leechblock, for my very simple, even minimialist, proposed add-on: it would simply put a Dialogue box: "Are you sure?" with a Y or N/cancel option, that's it, after someone clicks on Homepage button (or slightly fancier if you want: it would do the above if and only if one had a Homepage that contained more than N tabs where the user chooses N, or more than 8 tabs let's say)

Also a separate question, I will keep a tab open (!) for this thread in the meantime, to look for replies, but to avoid needing to do so in the future, how can I get ubuntuforums.org to automatically send me an email when this thread gets a reply? Most online forums has a checkbox before one hits the Submit or Post button, but I see none there..
Thanks

---

### Post by Bucky Ball on 2015-02-26
Have you tried 'Session Manager'? You can install that in Firefox by going to Tools>Add-ons and searching for it. Might help you out. 

You can get emails sent when there is a new post on your thread by going to Settings>My Settings>My Account>Default Thread Subscription Mode. Change that to 'Immediately, using email'. 

It applies to new posts on ANY of your threads. You can't select just one to be notified about, as far as I know.

---

### Post by coldraven on 2015-02-26
This morning FF was upgraded to FF36 and now there is no Home settings so your problem is solved :)
But seriously, this must be a bug!

---

### Post by vasa1 on 2015-02-26
> **harelb said:**
> ...
So it's a small disaster when I accidentally hit the "home" button ...
You can use CSS to hide the home button. You could still open the open page with Alt+Home from the keyboard. Or you could relocate the home button.

---

### Post by harelb on 2015-03-13
Bucky, Coldraven, vasa, sorry for the late response. Replies to each of you, your name in bold, below:

**Bucky**: thanks for info on thread subscription. This I just selected daily email updates. It has one more step (this is not to complain, your summary saved me lots of time looking for it, but it's just to help the next person in more detail) namely your

> Settings>My Settings>My Account>Default Thread Subscription Mode. 

I looked at sessionManager...it is interesting, but, it doesn't look like it's  what I was asking for...looks like it's a whole different way to just have all tabs saved where they last were...sometimes I do not want that - even if I have 40 tabs saved in Home but I visit another 7, I don't want 47 next time...only the tabs that were open during the most-recent-time-I-said-save-all-current-tabs-at-my-Homepage...

for my browser at least, took one more step:

> Settings>My Settings>My Account>GENERAL SETTINGS > Default Thread Subscription Mode. 

but got it saved now, thanks :-)

**ColdRaven**, I don't think I like the idea of no homepage at all..! But maybe they have alternatives that will be just as good...either way, I'm puzzled because I just did Help-->AboutFirefox and it says "36.0.1" is what I have, but I still have a Home (to the right of the down-arrow (for downloadS) button and to the left of a Star, Clipboard, PaperAirplane and StartAConversation..

**vasa**, can you explain how to do what you said:
> You can use CSS to hide the home button.

assume I know nowthing about CSS let alone how to use it inside(??) or in conjunction with firefox...It will not solve everything (I sometimes even "hit the home button" by mistake by a keyboard shortcut...after all these years I still don't know what it is..something like control-R instead of control-t? (control-t opens new tab)) but it would partially help for sure.

---

### Post by vasa1 on 2015-03-13
> **harelb said:**
> ... assume I know nowthing about CSS let alone how to use it inside(??) or in conjunction with firefox...It will not solve everything (I sometimes even "hit the home button" by mistake by a keyboard shortcut...after all these years I still don't know what it is..something like control-R instead of control-t? (control-t opens new tab)) but it would partially help for sure.

Well, I don't know that there's any solution for clicking the wrong icon or pressing the wrong keys in any operating system :)

If you aren't familiar with CSS, you may find the "hamburger" or "three hot-dogs" route easier. In other words, click on the icon which looks like three horizontal lines stacked vertically and select "Customize" from there. Play around a bit. You'll see that you can drag some of the browser's icons around the place. See if that helps.

---

### Post by harelb on 2015-03-14
That is perfect vasa - I just "hid away" the Home button by dragging it, which solves things for me. I almost never have to use that button anyway, I just periodically Edit-->Preferences --> Homepage [Use current pages] and that's it. In a rare case when I need to click the home button, I'll just use those three horizontal lines Open Menu and re-access it...so this solves things, thanks!

As for 
> Well, I don't know that there's any solution for clicking the wrong icon or pressing the wrong keys in any operating system 

I will gently suggest that (well, if not all the time, then much of the time) there **is** a solution: namely the "are you sure?" Even at the shell, one can alias "rm" to stand for "rm -i", even I know that...and for clicking buttons, heck even back in the 1980s they would have "Are you sure you want to...?" dialog boxes, so Firefox developers could definitely add that kind of functionality to "if the user clicks on the Home button, and if they have more than N tabs" (let user pick N or let N=15 be preset, let's say)...they just haven't seen the light yet ;-) Or maybe I'm just a bigger tab junkie that most ;-) 

But either way, thanks for this low-tech but super fast and easy solution (if I accidentally keyboard in a Home, I'm still screwed but at least for accidentally clicking the button, which was my main concern) Have a great weekend!

---

### Post by Bucky Ball on 2015-03-15
Just a tip: you can hit alt+home on the keyboard to get to the homepage. ;)

Also, if you don't want the home button there at all, right click the icon and remove the home button. Good luck.

---

### Post by vasa1 on 2015-03-15
> **Bucky Ball said:**
> ...
Also, if you don't want the home button there at all, right click the icon and remove the home button. ...
Good one :)

---

### Post by harelb on 2015-03-15
> Also, if you don't want the home button there at all, right click the icon and remove the home button.

Maybe I wasn't clear...I already removed it entirely...but by dragging method..it's good to know about the right-click alternative method (I assume one can still get it back, just like this dragging method lets you drag it back). New firefox version and I "didn't have the time" to try to explore all the possible things (including right-clicking) one can do with those (back then) "new" icons on the top right..thanks again.

---

