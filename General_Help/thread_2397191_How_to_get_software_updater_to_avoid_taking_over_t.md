---
title: "How to get software updater to avoid taking over the UI?"
date: 2018-07-26
forum: General Help
---

### Post by jrpstonecarver on 2018-07-26
Hi All,

Really stupid question here, and there probably is no obvious fix, but here's the deal. 

I'm on 16.04 and pretty happy, intel hardware, nothing special. All is well.

I boot the computer in the morning and get started on something, say, answering an email. I'm typing along and a couple of minutes later the software updater pops up to notify me there are updates.

I am in the *middle* of typing something, and I touch type, so before I can even register the new window is there my browser has lost focus, and somewhere between 2 and 10 keystrokes have been sent off to the software updater window. Depending on what they are, it may start updating, do nothing, minimize, or who knows what.

This morning when this happened, I noted it said there were several things to update, but seemed to just sit there, so I thought I'd gotten lucky. I manually minimized it, and finished the email. Then I brought the updater back and it told me my computer was now up to date. In other words, something I'd hit had apparently managed to allow updates to apply.

I like automatic updates. I want my computer to be up to date, but the UI design choice that has that window pop up and take keystrokes from something else going on is a train wreck.

How do I avoid that? I don't see anything useful in the settings ... display immediately, download immediately, or automatically download and install. I prefer to review the patches before installing them just so I have a clue what might be affected, so that last one is out, the first is what is selected, and the middle one... what does that even mean? Download and ignore? Download and then popup to OK the install? 

This UI needs help. But forgetting that for the moment, is there some way to avoid this other than always remembering to manually launch the software updater myself every time I boot up?

Thanks.

---

### Post by dragonfly41 on 2018-07-27
System Settings (top menu bar far right gear icon)
System > Software & Updates
Updates tab > Automatically check for updates > Never

Then it is up to you when you choose to update.

---

### Post by jrpstonecarver on 2018-07-28
Alas that isn't what I want. I am fine with it checking regularly, and even popping up a window to drive the updates. I just don't want it taking focus (and keystrokes) when it does. That is extremely poor UI design for any system, but incredibly so for a software updater.

You are right, in that if I did that the problem would not occur, but then I'd have other issues.

This seems to be an issue of bad UI design. Unless there is some hidden way to change the behaviour in question.

---

### Post by Holger_Gehrke on 2018-07-28
I don't know about mainline Ubuntu, but in XUbuntu (which uses XFCE as it's desktop and xfwm4 as it's windowmanager) there a setting (Menu->Settings->Window Manager, Tab 'Focus', Setting 'New window focus') that controls whether newly opened windows get the focus. If I set this to 'no' and start a new GUI application, the input focus stays where it is - so this would stop your problem. Would probably take a bit to get used to, because you'd always have to click in a new window to give it the focus. I don't know if there's something similar in Unity or Gnome, but if there is it's probably in a program to set window manager options ...

Holger

---

### Post by jrpstonecarver on 2018-07-28
That's an interesting thought, Holger, and it makes me think. I'm using Unity (which I hate, but... it's a thing. Nevermind that) and I have it set to focus follows mouse from ages ago. In a previous life I used the system in ways that were best served by letting focus go to a window in the background (and being able to type into it there, without it coming to the front). I've kept that setup even though I might not need that now.

I don't know if changing that will fix it, or if Unity has a way to keep focus from going to a new window, but I can certainly look. Perhaps it is time to give up on focus follows mouse as well. If that helps avoid this, I can probably get by.

I'll go poke around at the relevant tools. Thank you!

--jeffp

---

### Post by dragonfly41 on 2018-07-28
I have not used this but searching further I read that CompizConfig Settings Manager
(System Tools > Preferences > CompizConfig Settings Manager)
offers some control against "stealing focus".

[http://wiki.compiz.org/GeneralOptions#Focus_.26_Raise_Behaviour](http://wiki.compiz.org/GeneralOptions#Focus_.26_Raise_Behaviour)

[Added notes]

Digging deeper the settings are found in Window Rules plugin

[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

---

### Post by jrpstonecarver on 2018-07-28
Well, colour me confused, but I don't have compizConfig on my system. Not installed. I can find an icon for it, but it isn't present. Compiz is running, of course, but there is no settings manager installed. Digging around I found an old post, here:

[https://www.howtogeek.com/101006/how-to-tweak-unity-on-ubuntu-with-the-compizconfig-settings-manager/](https://www.howtogeek.com/101006/how-to-tweak-unity-on-ubuntu-with-the-compizconfig-settings-manager/)

That talks about installing it, but when I do what it says - using the Ubuntu Software tool - it's not there. Not as "CompizConfig" nor as "CCSM". As far as I can tell, it's not available for 16.04. Am I wrong?

---

### Post by jrpstonecarver on 2018-07-28
Ah. Found it in the Synaptic Package Manager. Apparently you had to dig deeper these days to find it. 

I am looking around.

---

### Post by jrpstonecarver on 2018-07-28
In addition to turning on click to focus (through the Unity UI tweak tool) I have now installed the compiz-config settings manager and set the Focus Prevention Level to "Very High". I am dubious, but it may help.

There are lots of threads about focus stealing issues in various places here and elsewhere, now that I know what I am looking for. The problem is bigger than the software update tool, though that is clearly where I hit it most often. Time will tell if this is a real fix for me or not. Probably tomorrow morning I'll have a clue.

---

### Post by jrpstonecarver on 2018-08-03
OK.... so this is interesting.

With the changes, most windows now open behind everything else. If I have Chrome open and go click on something to launch it - say Nautilus - it opens behind the browser window, and thus invisibly. I have to move things around one way or another to bring it to the foreground and give it focus to do what I want. Not exactly stellar, but OK.

Oddly, however, the software updater opens up in front of other windows, not behind. I guess it uses some setting to force that regardless of what the UI is configured to do by default.

Thankfully, however, despite being in the front, it does not take focus. It may completely cover what I am typing, and thus screw me up in other ways, but at least it doesn't suck up the keystrokes and do unexpected things.

I'll call that half a win. It's not perfect because I have to change other behaviours - like rearranging windows to get the one I just opened up to be accessible - but it is better in that I don't get unexpected stuff happening thanks to unknown keystrokes going into the software updater.

I'd really like a full win, however. Something that avoids these issues entirely. Surely it is possible. This behaviour is pretty nasty, and there must be people unlucky enough to have been bit by it and have something wrong happen.

Any ideas out there?

Thanks.

--jeffp

---

### Post by dragonfly41 on 2018-08-03
Can you install docky to quickly select windows (perhaps hidden)
or just hit Alt+Tab

---

### Post by jrpstonecarver on 2018-08-03
Understood, and thank you. There are - of course - various ways to do the window selection thing. (I hate to admit it but I just use the mouse. Alt-much-of-anything never sticks in my brain. My bad.)

But even so, that's just another band aid on top of a band aid. That is, the underlying issue is the lousy behaviour of the software updater application. It should not force itself to the front and take keystrokes by design. That is poor application design. I might even be persuaded that any UI system that lets that happen has a fundamental design flaw. But that might be going a bit too far. I can't claim to have surveyed all applications and usage patterns. But I am convinced that the design of the software update program is wrong an dangerous. If there is no fix (other than what I have done or turning automatic updates off) there is a very serious problem with the way things are setup.

I really should have control over this. The fact that I don't seem to is the problem. Applying these changes to get around it isn't ideal. I was hoping there was an actual fix out there somewhere.

---

### Post by dragonfly41 on 2018-08-03
Accepted that these suggestions are band aids.
I have been reading other sites which argue the case that focus stealing is unacceptable.

In one site [https://blog.codinghorror.com/please-dont-steal-my-focus/](https://blog.codinghorror.com/please-dont-steal-my-focus/) .. (Windows biased) I read this ..
[FONT=Helvetica]> 
X hasn&#8217;t been mentioned yet, so I thought I&#8217;d mention it.[/FONT]
[FONT=Helvetica]With X, the application which gets focus is down to the X server, not the application. The window manager generally acts as guardian of the focus - deciding whether or not windows should be given it.[/FONT]
[FONT=Helvetica]This works beautifully in, for example, KDE, where the focus-stealing problem simply doesn&#8217;t exist[/FONT][FONT=Helvetica].

Now admittedly with zero understanding of KDE I wonder, from reading above, whether using Kubuntu (KDE based) would cure this problem.

[https://docs.kde.org/trunk5/en/kde-workspace/kcontrol/windowbehaviour/index.html](https://docs.kde.org/trunk5/en/kde-workspace/kcontrol/windowbehaviour/index.html)[/FONT]

---

### Post by jrpstonecarver on 2018-08-03
Interesting. Focus stealing is definitely evil, but I hadn't thought of changing UIs as a possible solution. It does happen in Windows obviously in Unity. I have no clue about Gnome, though. As for KDE, I used it for some time, years ago. It was a pretty heavyweight UI and I think I stopped when I had some trouble with it on some older (and now long gone) hardware. I guess I could reconsider it. Unity is going away with 18.04 (when that is finally upgrade ready... any day now, I think) so I suppose going to Kubuntu might work.

I will ponder that. Not sure if I want to try that or not. Or perhaps I try 18.,04 with Gnome and if that has the focus stealing issue I then consider Kubuntu.

So much to do in my life that has nothing to do with Linux. Oh well... I'll get by.

Thanks for your continued looking into this. I'll take another pass at it once the 18.04 upgrade is available.

--jeffp

---

### Post by dragonfly41 on 2018-08-03
Perhaps experiment with installing Gnome Flashback on your current setup? That does not use Unity.
[https://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/](https://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/)

---

### Post by Holger_Gehrke on 2018-08-03
Is the program you're having problems with the same one you get when running 'update-manager' from a terminal ? Because that actually has a manual page which lists an option '--no-focus-on-map', which makes it start without coming to the front and without getting the focus. Now you just need to find the place where it gets started and insert that option ...

Holger

---

### Post by jrpstonecarver on 2018-08-29
An update on this. 

I've upgraded to 18.04.1, which means unity is out of the picture. Now I am dealing with Gnome.

Focus stealing is less of an issue, but it still happens in this case. The software updater doesn't take the focus right away. Instead it pops up and there is a notification that there are updates, but it doesn't steal the focus.

However, it seems that if you leave it untouched for some time - a few minutes... I haven't timed it - it *does* steal the focus and move to the top. I think it's the same problem, just delayed.

If anyone knows how to configure the software updater not to do that in 18.04.1, that would be very interesting information.

Thank you.

---

