---
title: "Help, my application windows keep disappearing!"
date: 2016-03-23
forum: General Help
---

### Post by sns2 on 2016-03-23
Hi,

Ubuntu 14.04.

Its very strange.  My windows keep disappearing.  Different random apps.

File Manager, Kodi, qbittorrent, MythTV you name it

For example, the Kodi window will be there fine in full screen mode.  I press \ to switch to window mode.  The Kodi window disappears.  All I see is my desktop.

I can alt-tab to the Kodi icon, but it never shows anything but by Desktop.  

If I press \ again Kodi returns to full screen mode as I would expect.

The other apps, like MythTV I just cannot get back, because I have no full screen toggle key binding.   

Once again, I see MythTV in alt-tab, but once selected it never shows.

File Manager:  This window actually does come back when I Right-click its icon in the dock and select it.  The window appears to be coming up from the bottom of the screen.  As if I had a 2nd display below my display. (I don't).

Once I reboot, everything is good again.  Until it isn't.

Any ideas?

Thank you

---

### Post by sns2 on 2016-03-24
A little more background:

This is on an intel i5-2400 HD2000 graphics.  Ubuntu 14.04 LTS.

So I am a newbie to using Ubuntu as my daily driver for an HTPC so I don't know if this is a known gotcha with an easy fix or what.

But this OS flakiness is making Ubuntu impossible to use -- I have to constantly reboot, every day, to make the computer usable.

Is there a concept in Ubuntu of minimizing a window to the Dock like in OS X?

It's as if the apps are get minimized to the Dock, but without the ability to restore them and bring focus back to them.

I can see all the apps running in the alt-tab switcher, but switching to them brings nothing to the foreground.

Very frustrating.

---

### Post by Geoffrey_Arndt on 2016-03-24
Are you actually runninng Ubuntu-Unity?  When you talk about "dock" . . that infers a non-Unity desktop like xfce (Xubuntu?) or gnome2 (Ubuntu-Mate?) or even Lubuntu (openbox wm?) . . . pls clarify.

In Unity . . . a minimized app shows up in the Launcher (column on left of screen with all desktop icons displayed via an accordion scroll mechanism).   The minimized app has a white caret symbol on the left side of app icon, whereas the focused (active window/active app) has both the left caret, and a right caret indicating it is the active app.

Something is certainly screwed up . . . abnormal, as OS flakiness in Ubuntu is extremely rare (like one in a thousand bootups).   

How did you do the install (what source, what method, etc.) . . . so we can figure out how the OS got hosed.

EDIT:   one other quick thought . . . for folks really new to Linux (any distro) . . . perhaps the most common way to mess up the stability of their new install, is to get programs from "non-official" sources (that is, sources outside of the official ubuntu repositories).   Then, the risk is that the user is overlaying required xx-version of dependencies, libraries, etc. etc.   And the system starts getting more and more flaky - unstable.

---

### Post by sns2 on 2016-03-25
Thanks. Sorry, yes, I was using OS X nomenclature.  So I meant Launcher.  Its standard Ubuntu 14.04 LTS.

So yes, now I see the 2 carets.  In OS X there is only one to the left, no right caret, so that's a very nice feature Ubuntu has with the second caret.  I hadn't even noticed that until now.

I see now that that it is, and has been, minimizing correctly, ie I can minimize the terminal and it disappears into the Launcher.

So now the Terminal is minimized to the Launcher.  I click it. It re-exposes itself, so there is no problem with at least the Terminal app, at the moment.

OTOH, my MythTV Frontend is missing. It has the 2 active carets on it right now, but I can't get it to show.  It's in the alt-tab switcher, and of course in ps -ax.  

Now I will killall mythfronend.real

Now relaunch mythfronted.   And its good for now.

Now I'll launch Kodi.  It launches in full screen.  I press "\" to go to window mode, and Kodi disappears. It has the 2 carets to indicate it is in the visible forefront-- but it's gone.  That's the problem.  

I've installed all my apps through the terminal with sudo apt-get.

Is there some log I can look at that would show something about the window failing to be exposed?

I almost get the sense the window is being wrongly exposed onto some kind of 2nd display it thinks I have or some kind virtual display that I do not actually have.  Actually, what is this VIRTUAL1 i see?

```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 2037mm x 1146mm
   1920x1080      60.0*+   59.9     30.0     24.0     30.0     24.0  
   1920x1080i     60.1     60.0  
   1280x1024      60.0  
   1360x768       59.8  
   1280x720       60.0     59.9  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0     59.9  
   720x480i       60.1     60.1  
   640x480        60.0     59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```


Also I am wondering if my having to use:
[COLOR=#000000][I]xrandr --output HDMI1 --off 
[/I][/COLOR]and 
[COLOR=#000000][I]xrandr --output HDMI1 --auto

[/I][/COLOR]as per this thread are related?
[http://ubuntuforums.org/showthread.php?t=2317083&page=2](http://ubuntuforums.org/showthread.php?t=2317083&page=2)

---

### Post by yetimon_64 on 2016-03-25
This has me both baffled and intrigued at the same time. You keep repeating ...
 > I press "\" to go to window mode. 

Have you set up some sort of custom keyboard shortcut to a single key that would normally print a single character to get a window action occurring ?

If I have an editor open and press that keyboard key it will print that character. If no editor window is open and active and I press that key NOTHING happens. How do you get a window action occurring when pressing the backslash key on your keyboard? Beyond that the rest of your question becomes unfathomable to me.

Are you using mac hardware with specialized keys etc ? You do mention mac OS X etc.

---

### Post by sns2 on 2016-03-25
Sorry if I wasn't clear.

I confused the point by mentioning OS X's Dock behavior vs Ubuntu's Launcher behavior.

This is all on Ubuntu.

In the application called Kodi, there is a standard keyboard binding of "\" that toggles Kodi between fullscreen mode and windowed mode.

I only mention it because Kodi seems unusual, because when all other apps go missing, even though they have 2 carets in the Launcher indicated it is supposedly active, I cannot make them reappear whatever I do.  I must kill them and restart them.

Kodi, on the other hand, I can at least toggle back to Fullscreen mode (and yet Window mode remains mysteriously missing)

---

### Post by yetimon_64 on 2016-03-25
> **sns2 said:**
> Sorry if I wasn't clear.

I confused the point by mentioning OS X's Dock behavior vs Ubuntu's Launcher behavior.

This is all on Ubuntu.

In the application called Kodi, there is a standard keyboard binding of "\" that toggles Kodi between fullscreen mode and windowed mode.

I only mention it because Kodi seems unusual, because when all other apps go missing, even though they have 2 carets in the Launcher indicated it is supposedly active, I cannot make them reappear whatever I do.  I must kill them and restart them.

Kodi, on the other hand, I can at least toggle back to Fullscreen mode (and yet Window mode remains mysteriously missing)
Are you running Ubuntu on Apple Mac hardware ? I know you are using ubuntu, that is clear enough. I don't know how a key binding in Kodi, a single application can affect other applications like that at present. 

Sounds like kodi may be issuing a command that affects other open windows. Some window commands can do that at times, I have seen similar when using wmctrl to manipulate windows with scripting.

I have no idea what kodi is used for at the moment, just did an "apt-cache search kodi" for it and got a blank response. If you could quickly explain what it is/where it was installed from etc, may be a bit more helpful.

---

### Post by sns2 on 2016-03-25
Thanks... no apple hardware.  its just commodity x86 ECS motherboard.

Kodi is media center / video player software, formerly known as XBMC ("Xbox Media Center") here:

[https://kodi.tv/about/](https://kodi.tv/about/)

i got kodi latest minus 1 revision (v15.2) from ppa:
"add-apt-repository ppa:team-xbmc/kodi-old"


I *think* I see the source of your confusion.   The "\" is not a global Ubuntu keybinding, although it might seem that way because when I press it, no visible window is on the screen.   The difference is, that the Kodi icon in the Launcher has 2 carets, meaning it is supposedly the front most window, despite that fact that it is invisible.  At this point, with Kodi the active yet invisible window, Kodi is still able to respond to its own keybindings, and thus, able to process its own "\" trigger which tells the invisible Kodi "windowed" window to snap back into fullscreen mode... which it dutifully does.

IOW, if I press the "\" key in a text editor, it will simply make a "\" character.

If I click on the Kodi icon in the Launcher, the icon then displays 2 carets indicating Kodi is the front most visible window.  Although I cannot see it, it does, at that point, respond to the "\" character going back into Fullscreen mode.

Other apps, like qbittorrent, for example, I have no way to see their window again.   I must kill them in the terminal or reboot

---

### Post by yetimon_64 on 2016-03-25
> **sns2 said:**
> Thanks... no apple hardware.  its just commodity x86 ECS motherboard.

i got kodi latest minus 1 revision (v15.2) from ppa:
"add-apt-repository ppa:team-xbmc/kodi-old"


I *think* I see the source of your confusion.   The "\" is not a global Ubuntu keybinding, although it might seem that way because when I press it, no visible window is on the screen.   The difference is, that the Kodi icon in the Launcher has 2 carets, so although the "windowed" window is invisible, it is apparently still responding to keybindings, and thus, able to process the "\" trigger which tells the invisible "windowed" window to snap back into fullscreen mode... which it dutifully does.

IOW, if I press the "\" key in a text editor, it will simply make a "\" character.

If I click on the Kodi icon in the Launcher, the icon then displays 2 carets indicating Kodi is the front most visible window.  Although I cannot see it, it does, at that point, respond to the "\" character going back into Fullscreen mode.

Other apps, like qbittorrent, for example, I have no way to see their window again.   I must kill them in the terminal or reboot

Yes that is clearing things up a bit. 

It could possibly be related to Unity but really sounds more like a problem I'd be reporting to/investigating with, the devs of xbmc, if their keybinding in kodi is affecting other open windows, like qbittorent, the file manager etc, like you are saying. I suspect kodi is the problem mainly because the key binding in use is specific to that application.

As per Geoffrey_Arndt's post...
> ...perhaps the most common way to mess up the stability of their new  install, is to get programs from "non-official" sources (that is,  sources outside of the official ubuntu repositories) 
 ... PPA's are _*not official repositories*_ but are _*Personal*_ Package Archives.

We can add from such sources pretty simply in terminal but because they are developed and maintained by others, problems like this need to be reported to them eg [https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa). Note the line near the top ... > For questions and bugs with software in this PPA please contact           [Kodi]("https://launchpad.net/%7Eteam-xbmc").
You would need to open a launchpad account to do so.

I can't help much more here by the looks of it, good luck. yeti.

---

### Post by Geoffrey_Arndt on 2016-03-25
Just to clarify a bit further, two carets attached to a program icon in the Launcher do not necessarily mean that program is the "active window" . . . if the two carets are both on the LEFT side of the app icon, it just means there are two "instances" of the program running (but - - in the background . . . . OR . . . . in another Virtual Desktop).

Have you enabled "workspaces" (to toggle between Virtual desktops) via System Settings>Appearance>Behavior Tab?    If you do that, you'll get an icon in the Launcher with a representation of a quad display (of 4 desktops) . . . click it to see what I mean.    Maybe that's where your apps are hiding?

Note:   to solve this problem, after enabling Virtual Workspace displayer . . . try running Kodi and the other apps you described in their own workspaces, then toggle between them using the workspace switcher icon described above.

---

### Post by sns2 on 2016-03-25
> **yetimon_64 said:**
> 
It could possibly be related to Unity but really sounds more like a problem I'd be reporting to/investigating with, the devs of xbmc, if their keybinding in kodi is affecting other open windows, like qbittorent, the file manager etc, like you are saying. I suspect kodi is the problem mainly because the key binding in use is specific to that application..

OK, thanks, but hold on a sec... I did not say or mean to imply that the keybinding in kodi is what is affecting other open windows.

I have no idea what is causing the problem with other open windows.

All I am saying with Kodi is it is the only app that once it goes missing, I can get back, albeit only in fullscreen mode.

 That is simply because I memorized Kodi's fullscreen keybinding.  

If the other apps had a fullscreen keybinding, perhaps I could get those back as well.

But I have no data to link Kodi as the cause of the problem, other than the fact it is from a PPA.

That said, I have 4 other PPAs installed for this HTPC.

zfs
mythbuntu (for the latest mythtv app)
kodi.pvr.myth (a plugin within kodi to mythtv pvr integration)
qbittorrent

That said, do you still suspect Kodi?

Thanks

---

### Post by yetimon_64 on 2016-03-25
> **sns2 said:**
> OK, thanks, but hold on a sec... I did not say or mean to imply that the keybinding in kodi is what is affecting other open windows.

I have no idea what is causing the problem with other open windows.

All I am saying with Kodi is it is the only app that once it goes missing, I can get back, albeit only in fullscreen mode.

 That is simply because I memorized Kodi's fullscreen keybinding.  

If the other apps had a fullscreen keybinding, perhaps I could get those back as well.

But I have no data to link Kodi as the cause of the problem, other than the fact it is from a PPA.

That said, I have 4 other PPAs installed for this HTPC.

zfs
mythbuntu (for the latest mythtv app)
kodi.pvr.myth (a plugin within kodi to mythtv pvr integration)
qbittorrent

That said, do you still suspect Kodi?

Thanks

I'd test the suggestion from Geoffrey_Arndt with the workspaces first but I've never heard of using the "\" as a keybinding like that before now with any other packages. I really don't know to be honest and could very well have misread the situation. Try out fully what Geoffrey_Arndt is suggesting to rule out the system first of course. Those links may very well may not be needed.

The only keybinding I've ever come across with apps to send an app to fullscreen and return is the F11 key. But it doesn't minimize them as such to the launcher that I know of.

I am out of my depth with this question by the looks of it and will let Geoffrey continue and I will watch the thread for a bit. Cheers, yeti.

---

### Post by sns2 on 2016-03-25
Thanks Geoffrey,
Regarding the triple caret, that is tremendous info.  Thats another nifty innovation of the Ubuntu Launcher over the OS X Dock (OS X disallows simultaneous launches of apps).

Yes, I had thought of the the workspaces..  In fact, a few days ago, even though Workspaces were already off, I turned them on hoping my hidden windows were there.  But no luck, so turned it back off.  I will try your suggestion of purposefully clean launching kodi and other apps in their own spaces and toggling back that sounds like a good idea.     Will let you know.  Thanks

---

### Post by sns2 on 2016-03-25
> **yetimon_64 said:**
> The only keybinding I've ever come across with apps to send an app to fullscreen and return is the F11 key. But it doesn't minimize them as such to the launcher that I know of.

Thanks, I will try his tip and post back

Regarding the apparently more common F11 keybinding, this sounds like the same exact functionality of Kodi's "\" (when its working properly) -- it toggles between fullscreen and window mode, and it never minimizes it to the launcher either.   Right now, with the current seeming system wide problem, it toggles b/w fullscreen and limbo.

---

### Post by Geoffrey_Arndt on 2016-03-25
To further test the possibilities of this unusual/atypical behavior, perhaps best to setup a test environment and run all those apps based solely on what's in the official repos.   A clean environment is the first step to start eliminating factors.    This can be done using a Live DVD or USB Stick created with "persistence".   Best to use mkusb to create the live media.   I would also be interested to see if different window managers have any effect (besides Ubuntu, might be interesting to try at least one other distro like Xubuntu for instance).

Let us know if launching the apps in their own specific workspace makes a difference re accessability.

BTW .  .  . . . what does the Super + W key show when these apps are running as you've described . .  ?  Try it before minimizing any windows (but have them all runnning), and then try with selected (1 at a time) minimized.

---

### Post by sns2 on 2016-03-27
Hi,
Thanks for all the help.

I think I may have fixed it, not quite clear because it didn't always happen before. 

Just to recap:

Workspaces - the windows were not hidden in any other workspaces 

Super-W - this fails to gather any hidden windows, they remain hidden as if they are not running

mkusb and persistence - this is some good info, thanks.  I had been using an app called YUMI to do this in the past, and mkusb seems like a more ubuntu way, so i will try doing this at some point

So I think it was kodi after all.

After I removed the .kodi prefs folder and it seems to have fixed the problem.  Relaunching kodi creates a clean set of prefs.   I think it was one of the 3rd party kodi addons may have been causing this, not sure.

It might have been as simple as that...  I have held off running Myth so far as I am still trying to isolate things, so I don't yet know if it will come back once Myth is back in the picture. 

I also uninstalled the qbittorrent PPA.  I will add things back slowly and see if it can remain stable.

Thanks for all your help.

---

