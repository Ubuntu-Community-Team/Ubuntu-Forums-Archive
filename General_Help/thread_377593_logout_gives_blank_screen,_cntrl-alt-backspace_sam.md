---
title: "logout gives blank screen, cntrl-alt-backspace same"
date: 2007-03-06
forum: General Help
---

### Post by sdowney717 on 2007-03-06
logout gives blank screen, cntrl-alt-backspace same

What should I check for.
At the blank screen, it appears to lock up, 
(keyboard numlock light wont change etc...)

At which point all I can do is pull the plug and reboot system.

I had installed beryl and XGL but then removed it
Also, why then is the beryl manger still in the panel and it still runs the beryl manager?
How do I really get rid of it.
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL)

I had followed this link

---

### Post by Kateikyoushi on 2007-03-06
Search for beryl in synaptic, it should show up and right click remove.
I am not convinced beryl is behind your logout lockup.

---

### Post by sdowney717 on 2007-03-07
yes, you are right!
I restored my partition  back to where I could log out ok,

Then I used apt-get install kde

Everything worked fine in kde and gnome
I do not have beryl anymore

BUT the logout problem has returned. When I logout, all I get is a blank screen
And all I can do is hold in the power button to force it to turn off.

So what can I do?

---

### Post by sdowney717 on 2007-03-07
I carefully watch the screen when I logout, it goes black, then lightens slightly with it totally blank.

Then the keyboard is locked, the numlock button cant toggle the numlock light, computer seems to completely hang.

---

### Post by sdowney717 on 2007-03-07
I can shutdown normally.
what exactly happens when you logout of a session, what happens with xwindows ?
what is the login page running in, is it running in a different setting than your desktop?

---

### Post by castoroil97 on 2007-03-17
I have the same problem.  It is my own noob fault.

Through the theme window I had clicked on install then I applied it.

At that moment I lost all icons and panels and it froze.

I rebooted and could only get back to the GUI if I started in a previous session

I changed the theme and deleted comix cursor stuff from .themes and .icons and rebooted

I was able to sign in normally, but have not been able to log out properly.

There is no error messages, it just goes to a black screen and hangs.

I had gotten the cursors from here
[http://www.gnome-look.org/content/show.php/ComixCursors?content=32627](http://www.gnome-look.org/content/show.php/ComixCursors?content=32627)

---

### Post by dacool25 on 2007-03-17
I kind of have the same problem, first of all because i'm logged in under the xgl session i have to log out first, and then click shut down.  Then once i click shut down it goes through its stuff to do, and it finally gets to stopping system message bus dbus, and hangs on that.  I can press ctrl alt delete and it will just restart the process (but still hang) or i can push the power button once and it will restart the process.  Even so i have to do a hard shut down every time.  Anyone else experiencing this?  Or know how to fix it for that matter?

---

### Post by EminNew on 2007-03-18
I have the exact same problem.

I do NOT have beryl installed, and have not been fiddling with Gnome goodies and eyecandies (much).

Don't know the answer, but next thing I'll check is Sessions preferences. Could be some screen/keyboard locking on logout option that's enabled.

In the meantime - help us, somebody!

---

### Post by Sanchopinky on 2007-03-18
Yep same problem here, but I do have beryl. Whenever I try to log out.. it just goes black..

---

### Post by castoroil97 on 2007-03-18
well, it seems half of us had beryl and the other half did not.  That would tell me that either beryl is not the culprit.  if it is though, it be different causes resulting in the same symptom.

I had used envy to install my ATI driver in my laptop, I had not tried to log out since I did that, so it is a possible ATI driver problem.

I am but a grasshopper, we need a master

---

### Post by Sanchopinky on 2007-03-18
Maybe it is envy because that's what I used t install the ATI drives~

---

### Post by castoroil97 on 2007-03-19
or the ATI driver.. I tried everything else to get that in and Envy was the only thing that worked...worth the price in my opinion, but it would be handy to log out every now and then
:)

---

### Post by chickan on 2007-03-19
I am also suffering from this, and since I'm messing with xorg.conf and having a b|tch of a time with it, logging out would be useful.

I have a dual monitor setup, but once the second monitor just displays the same as the first.  When I log out, the first goes blank, says no input, but the second is left with the login back drop, but nothing else there, numlock/keyboard are unresponsive.  I am also struggling with the ATI drivers, can't seem to get them to work right (eventually trying to get beryl installed)

EDIT: So after some more tinkering, I think the problem lies in fglrx drivers, as when I switched to radeon, the problem went away and I could log out successfully.  Still no direct rendering though, bleh, giving up for the night.

EDIT2: some more searching turned up this topic: [http://ubuntuforums.org/showthread.php?t=379397&page=2](http://ubuntuforums.org/showthread.php?t=379397&page=2) and the first post on the second page sums up the solution, add AlwaysRestartServer=true to the Daemon section of /etc/gdm/gdm.conf-custom  

Hope this helps.

---

### Post by castoroil97 on 2007-03-19
That worked for me!!!

Thank You very Much!!!

Now if I can only get the headphone jack to work on my Toshiba Laptop.

Great Job!

:popcorn:

---

### Post by rubbsdecvik on 2007-03-20
I am having the same problem but with the nvidia driver.  Has anyone figured out what is causing it?  If I absolutly need to, I can get rid of the driver, but I like it because I do play some games with wine, and it works better with the prop. driver.

Any insight would be wonderful, because I have no idea where to start.

---

### Post by atdi4ever on 2007-03-20
same problem but only after installation of beryl. not after i installed my ati drivers

---

### Post by castoroil97 on 2007-03-21
post # 13 of this thread fixed it for me, I am able to log out now

---

