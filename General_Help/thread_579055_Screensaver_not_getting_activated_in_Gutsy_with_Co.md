---
title: "Screensaver not getting activated in Gutsy with Compiz Fusion"
date: 2007-10-17
forum: General Help
---

### Post by sajahanm on 2007-10-17
I upgraded to Gutsy. When the Visual Effects is set to none I am getting the screensaver. But, when I set the Visual Effects, screensaver is not getting activated. Just blinks and comes to the normal screen.

I have Dell Dimension 8400 with ATI Radeon x300 video card. Any solutions?

---

### Post by Yv12345vY on 2007-10-19
Same here.  Not much info out there unfortunately.

---

### Post by atlas1 on 2007-10-24
I'm having a very similar problem:  with the visual effects off, the screensaver works... but when the visual effects are turned on, the screensaver stops working.  

However, instead of blinking on and off, the screensaver starts to run and then freezes - so the screen shows a frozen image of whatever screensaver was running.  That said, the system itself doesn't freeze: moving the mouse cancels the screensaver and everything (else) works fine.

I have a Radeon 9800 graphics card, and have tried changing to the proprietary driver (enabling compiz fusion by installing xserver-xgl and and changing the Composite line in my xorg.conf from "0" to "1") but encountered the same problem.

I have uninstalled the default gnome screensaver and replaced it with xscreensaver, and that encounters the same problem.  Interestingly, the cycle function for xscreensaver still works - but each time the saver changes it freezes until the next change. 
:(

---

### Post by ant1060 on 2007-10-24
I have exactly the same problem with gnome screensaver and also xscreensaver.  I have decided, while this gets fixed, to start xscreensaver running manually (xscreensaver-command -activate NB space before the -activate). This works well BUT it's kind of annoying....

---

### Post by Roger Carlssom on 2007-10-24
Same problem here..... Waiting for a soloution.
I am newbie with ubuntu I was running Suse before and I must say that Ubuntu is working very good except this with the screensaver problem.

---

### Post by Ridonkulous on 2007-10-24
yeah, i'm in the same boat as the op it seems.

If the screensaver is the only thing that never works though, I would be pretty happy.

First time Linux/Ubuntu user...so far so good.

---

### Post by Ridonkulous on 2007-10-24
Ok, not sure if this fix is a good one or not, but it seems to be working for me.

First I decided to remove all the screensaver stuff that was on my comp.  I figured they weren't working so I didn't need them just sitting around.  

I went to Synaptic Package Manager and removed gnome-screensaver, as well as all of the xscreensaver packages I had installed.

After searching the net it seemed that gnome-screensaver just doesn't work very well, so I decided to not even try to use that.  Seems it causes more trouble than its worth.  not sure though, someone may prove me wrong later

I went back to synaptic and searched for xscreensaver.  
I clicked all the packages, because I wanted all the extra stuff. 
(not sure what all they have in those extra packages besides other screensavers, but figured it couldn't really hurt)

So hit apply to install them, easy enough.

Then I opened a terminal and typed "xscreensaver &" 
(if that doesn't work try "xscreensaver-demo")

It popped up a nice little settings window for xscreensaver.  I chose my settings, set my screensaver to come on in 1 minute, went downstairs to put a plate away, and came back to a lovely screensaver. !!hooray!!

This next part is optional. 
As **atlas1** pointed out, when you install the xscreensaver, it should automatically add an entry to your Applications menu under Other.
I wanted to keep mine where the original screensaver settings were though.
Then I went to **SYSTEM>>PREFERENCES>>MAIN MENU**
Click "+New Item" when you are in the **SYSTEM>>PREFERENCES** section of the menu editor.

A small dialog box will pop up, it may be behind the window if you can't see it.

Type:  Application  (i originally chose app+terminal, but just app works also)
Name:  XScreensaver Settings   (or whatever you want to call it is fine!)
Command:  xscreensaver-demo
Comment:  XScreensaver Settings GUI 

I think you should be set after that.
Try it out and let me know.  The advanced tab has some power management features, but I disabled them as I was unsure how they might clash with the other gnome Power Management feature in the System>>Preferences menu.

Sorry so long, lemme know if this works, thanks

---

### Post by atlas1 on 2007-10-25
Thanks Ridonkulous - that's worked for me!

Have to say I wasn't expecting it to, as I had already swapped to xscreensaver.  I don't know whether it was the complete removal of all screensaver packages to begin with, or installing the extra screensaver packages that I didn't have before - but not sure I care!

One note - once it installed, I had a an entry automatically added to the applications menu (under 'Other') to access the xscreensaver settings (so I didn't bother with the menu editing after the package installation).

---

### Post by Roger Carlssom on 2007-10-25
Ridonkulous
Worked for me.... But it would be nice to see gnome-screensaver working also. Just one problem left. Dual Screens !!!

---

### Post by atlas1 on 2007-10-25
Roger - Just ran a quick test... if you want gnome-screensaver, this now also works for me (I simply uninstalled the xscreensaver package and reninstalled the gnome-screensaver package, leaving all the extra packages alone).

---

### Post by Roger Carlssom on 2007-10-25
That didn't work for me. So I use xscreensaver has you described before. 
Thanx for helping out !

---

### Post by TheIrishGuy on 2007-10-25
same problem here

screensaver merely flashes.

its like the screensaver window is trying to activate but the effects are affecting the window and as a result bringing it back out of idle!!!

---

### Post by Ridonkulous on 2007-10-25
Yeah, I never even noticed that there was an entry for XScreensaver in the Applications menu, I just wanted to keep my screensaver settings where they were originally so i did that not even thinking haha.

I will add that to the post.  I would try doing this with gnome-screensaver, but right now i don't see the point.  ElectricSheep is working flawlessly, so until Gnome-screensaver has some sort of obvious advantage, I am going to stick with Xscreensaver.

Glad I could help some people even though i'm completely new to this. 

peace

---

### Post by Ridonkulous on 2007-10-25
> **TheIrishGuy said:**
> same problem here

screensaver merely flashes.

its like the screensaver window is trying to activate but the effects are affecting the window and as a result bringing it back out of idle!!!

Even after following those cryptic steps I posted your screensaver is not working?
Not sure how to help really.  I think the OP and I have a very similar setup, and maybe yours is different enough that you are missing some other packages or something that while apparently essential...are.  

I have no idea though really, sorry.  If i think of anything, I will let you know.

---

### Post by Roger Carlssom on 2007-10-25
Hi ! Report back. I said that xscreensaver was working I was wrong. After 10 minuts of screensaving the screen wnt blank and no response from keyboard or mouse. Just the power buttom worked. Strange. I then disable any poermanagement funktion. But still the same....What the f-ck am I doing wrong... // Roger

---

### Post by Roger Carlssom on 2007-10-26
Hi !
Did you waited for 1 hour with the screensaver on ? If I leave the machine with the screen saver on. After 1 hour the screen is blank and no response at all..

---

### Post by penman242 on 2007-10-26
I have an intel core2duo 20-inch iMac (Late 06, MA589LL) and I am having the same problem.  While I'm waiting for a fix, I installed brightside, added it as a startup program in sessions, then configured it so the bottom left corner would start the screensaver.  To configure brightside, go to System, Preferences, Screen Actions.

Now if move the cursor to the bottom left corner, the screen goes black and a window comes up immediately asking for my password. I just click cancel and then my selected screensaver starts.   So, it requires my password to come out of screensaver, even though that option isn't selected in the screensaver preferences.  Not too big of a deal.

Can't say for sure if this will help any of you but it works on my imac.

---

### Post by Ridonkulous on 2007-10-26
No idea whats wrong guys.  My screensaver works perfectly.  I have it set to come on after 1 minute, and then turn off the screen after 20 minutes via the regular power management option in the system menu.  It comes on no problem and runs then the screen goes black when its supposed to, and i can move the mouse and my computer comes back to life perfectly.

Sorry I am no help guys.

---

### Post by fa99tty on 2008-02-14
Thanks Ridonkulous - this worked for me too. :guitar:

---

### Post by crazygopedder on 2008-03-11
Yea thanks Ridonkulous, that worked for me as well.  Gnome screensaver was crashing X with Compiz installed so I removed it, installed xscreensaver, and ran the following in the terminal:

$export DISPLAY=:0
$xscreensaver-demo

*Note - The xscreensaver window may show up with no window decorations; this is ok.

And it worked!  I never knew there were settings for all the cool 3d screensavers either lol.  
I think the problem is that gnome-screensaver conflicts with Compiz since Compiz integrates with the Gnome desktop.  Xscreensaver runs at the xserver level (from what I can tell, somebody correct me if I'm wrong) so it runs just fine with Compiz enabled.  Hope this helps anybody else who can't get their screensavers enabled.

---

