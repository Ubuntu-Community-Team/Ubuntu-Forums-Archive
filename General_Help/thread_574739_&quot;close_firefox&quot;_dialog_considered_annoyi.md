---
title: "&quot;close firefox&quot; dialog considered annoying"
date: 2007-10-13
forum: General Help
---

### Post by jakoblund on 2007-10-13
This dialog, shown by firefox on startup at seemingly random times:

[INDENT]**Close Firefox**
Firefox is already running in another window, but is not responding
[/INDENT]

annoys me. This happens, to my experience, when one of three situations occur:
[LIST=1]
[*]There's already an open window
[*]There's a zombie firefox-bin process that needs to be killed (this is when the appearence of the dialog seems unmotivated :-s )
[*]Under KDE, if a former windows user doubleclicks the firefox icon, KDesktop wants to open two windows simultaneously (which is silly, but its even sillier that firefox can't cope with it in a non user-hostile way)
[/LIST]

When the user clicks a desktop icon, he/she expects a new window will open, so how come firefox doesn't simply respond to each of the three situations appropriately (1:spawn a window, 2:silently kill the unresponsive process, 3:as (1), or, more elaborately, assume that if there's two requests from the same user to open a window in, say, less than 1/3 of a second, it would be ok just to open one).

My four year old daughter, who happens to like some on-line kid's game (at [www.dr.dk/oline](www.dr.dk/oline)) that can be played in firefox really well, can switch the computer and monitor on, log in by double-clicking (I have allowed this in the login-manager-configuration for the "guest" account, the one with the cute penguin logo :-) ), but she can NOT start firefox (I have of course configured the start page to be the one she needs, so the browser would just start, she could be playing) because she can't handle these stupid useless dialogs!


My questions to this forum are:

[LIST=1]
[*]Am I really the only person who finds this annoying?
[*]Can the behaviour I want be acheived just by changing firefox's settings? (there is something here [http://ubuntuforums.org/showthread.php?t=292121](http://ubuntuforums.org/showthread.php?t=292121), but it doesn't seem to do all that I want)
[/LIST]

Cheerios
Jakob :^)

---

### Post by pheeror on 2007-10-13
use konqueror

---

### Post by jepes on 2007-10-13
I have the same problem but seems like it started when my kernel was updated. also, new pages opens in a new windows even if my settings tells it to open in a new tab.

---

### Post by pheeror on 2007-10-13
Yeah, definitely the kernel problem! :-D

I wasn't kidding about konqueror. If you use KDE, konqueror will suit you more then any other browser. And it's not slow as hell(ish firefox).

---

### Post by jakoblund on 2007-10-13
I use Konqueror myself, and when I hit one of those (rare) pages that Konqueror can't display, it's no problem for me to use another browser for just that page. My homebanking, Gmail and Google Maps are such pages.

For the rest of my family (the not nerds), making this distinction doesn't make sense -- for them it makes more sense to use the same browser all the time. Firefox would be the easy choice, IF IT WASN'T for this darn dialog...

---

### Post by pheeror on 2007-10-13
Ok, now you can get my (not helpfull) answer ... ;-)

3) It's really not silly. kcontrol.Mouse and set "double click to open files ...."
Rest of your problems you can solve with defaulting to konqueror instead of firefox for the rest of your family. Mozilla's devs are MScentric. There are tons of bug issues about thinks like this, but they don't care. 
In other words, this can't be solved easily. Anyway, there are some workarounds - wrappers for firefox binary. Check out ```
cat `which firefox`
``` ...

btw. Man who can't appreciate power of konqueror _is_ nerd :-D and that AJAX version of gmail is rubbish, html one is awesome technology like the rest of google :-D

---

