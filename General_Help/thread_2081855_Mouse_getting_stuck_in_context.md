---
title: "Mouse getting stuck in context?"
date: 2012-11-07
forum: General Help
---

### Post by dishe on 2012-11-07
I tried to revive some old hardware someone gave me (Lenovo 7757 laptop) with the latest build of Ubuntu (version 12.10). I ran it off the live CD first to make sure everything was good, and while I noticed some erratic mouse behavior, I chalked it up to user error / DVD drive lag, and went for the full install.

Now I'm noticing that the mouse gets stuck within application contexts. I'm not sure how to describe this properly, but lets say I'm in firefox and a dialog box pops up. I can move the mouse over the OK button, but I can't click it. Nor can I click anywhere outside of the browser (volume, settings, other applications, etc). Clicking on what I expect to be the OK button actually continues to click on the webpage behind it. The only thing I can do is use keyboard shortcuts to grab control of the dialog box and hit enter. With some clever navigation (using the super key to move to another application), sometimes the control of the mouse will make sense again, and I can click everywhere. Until an application is in the foreground and once again assumes control of my mouse (this behavior is not limited to firefox). 

I thought maybe it was faulty hardware with this laptop's trackpad (the right click button is broken), so I tried a USB mouse, and found the same results. The mouse seems to get "stuck" within context in or out of an application. Has anyone ever heard of anything like this before? I didn't try the LTS version (12.04), but would that make a difference? The Ubuntu installation is pretty much stock, stock desktop environment, etc, heck I even think I noticed this on the live CD. 

Anyone have any suggestions?

---

### Post by dishe on 2012-11-17
Just to update:
I tried 12.04, to see if maybe the LTS version would work better, and no dice.

Applications tend to seize control of the mouse (anything from firefox, system settings, Libre, to Ubuntu Software Center) and refuse to give it up unless I alt-f4 to kill the window.

I tried installing and using KDE (Kubuntu-desktop I think?) to see that made a difference. It appears to not depend on GUI either. So does that mean it is something deeper, such as part of the X-Windows layer or something like that?

Seems like it might be something funny about my particular hardware (Lenovo 7757). I found a thread elsewhere that implied changing the keyboard made the problem go away. But I can't change the keyboard on a laptop, or even figure out how to disable the one built it. any ideas?

---

### Post by dishe on 2012-11-19
Sorry to bump this again, but I have uncovered an interesting (albeit annoying) work around for now. 
I noticed that a log out / log in seems to fix it until I power down. When starting from a fresh boot, I have to remember to do that once in order to avoid losing mouse context again.

I would still REALLY like to get to the bottom of this and fix it for real- any help?

---

### Post by dishe on 2012-11-20
At this point, I would appreciate even someone chiming in just to say "stop bumping your own thread, dude".

Seriously- does anyone have any suggestions as to where I should even start to troubleshoot this kind of bug?

---

