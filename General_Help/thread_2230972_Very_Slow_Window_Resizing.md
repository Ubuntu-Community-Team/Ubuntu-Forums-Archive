---
title: "Very Slow Window Resizing"
date: 2014-06-22
forum: General Help
---

### Post by mooreted on 2014-06-22
I am running:

Ubuntu 14.04 x64
8 GB RAm
Intel Core i7 4770k
Nvidia Gtx 650 1 GB: Driver: 331.38
Direct Rendering: Yes

When I re-size a window by dragging and edge or a corner, it take about 1 full second for the window contents to update. 

Is there a fix for slow window re-sizing in Ubuntu 14.04?

---

### Post by mooreted on 2014-06-22
Well, I guess I will use Fluxbox for now. This is really annoying.

---

### Post by mooreted on 2014-06-22
Found a workable workaround. In CCM settings I changed the windows resize to "outline". No more 2D lag.

---

### Post by pme 72 on 2014-06-22
Thank you. Been having the same issue with my integrated Radeon HD3000 and that seems to have fixed the issue.

---

### Post by mörgæs on 2014-06-22
Good, please mark the thread 'solved'.

---

### Post by mooreted on 2014-06-22
> **mörgæs said:**
> Good, please mark the thread 'solved'.

Not sure "Solved" is the term I would use. "Solved" would mean that it works properly without the need for an ugly hack. With my computer there should be no graphical lag whatsoever.

Oh well, Linux is always a work in progress. It would be nice if someone had a hint as to why this happens and how to fix it properly.

---

### Post by bluplanet on 2014-06-24
I have a different perspective on a window resizing problem that makes it take too long.

The mouse location required to grab the window resizing handles seems to be about 1/10th of a pixel wide.

It takes extra time to concentrate and steady my hand enough to get my cursor to turn into one of those arrows, and more often than not, the muscle movement involved in left-clicking the mouse manages to move the cursor enough to trash my atempt before the click is complete.

...and forget actually clicking on a corner handle--that would be like winning the Powerball.

---

### Post by mooreted on 2014-06-24
> **bluplanet said:**
> I have a different perspective on a window resizing problem that makes it take too long.

The mouse location required to grab the window resizing handles seems to be about 1/10th of a pixel wide.

It takes extra time to concentrate and steady my hand enough to get my cursor to turn into one of those arrows, and more often than not, the muscle movement involved in left-clicking the mouse manages to move the cursor enough to trash my atempt before the click is complete.

...and forget actually clicking on a corner handle--that would be like winning the Powerball.

Yeah, they don't give you much of a target. You can ALT + Right-Click and select Resize. Also you might be able to change the window borders; I haven't tried that yet.

---

### Post by mooreted on 2014-06-24
Found something cool on Ask Ubuntu:

"ou can enable the Unity Grab Handles for easier window handling:

Install the Compiz Settings Manager (ignore if it's already installed)

sudo apt-get install compizconfig-settings-manager
Bring your run dialog and type

ccsm
The Compiz Settings Manager will open.

In the search box, type "png" and tick the PNG image loader checkbox.
Now search for "grab handles" and tick the box next to the Grab Handles item.

Now click the item itself; a new screen will appear.

Click in the button at the right of the "Toggle Handles" and pick your hotkey to toggle the handles."

---

