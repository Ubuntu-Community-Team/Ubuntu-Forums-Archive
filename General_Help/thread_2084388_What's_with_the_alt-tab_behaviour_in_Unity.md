---
title: "What's with the alt-tab behaviour in Unity?"
date: 2012-11-15
forum: General Help
---

### Post by k999 on 2012-11-15
Hi,

Does anyone know the reason Unity has such idiotic alt-tab behaviour? If I have a browser with a download window, and two terminals open, all in one viewport, it's fsck-ing impossible to switch to the window I want without clicking all over the place. Alt-tab to the correct group, then alt-down to see which window is selected, and alt-tab or alt-shift-tab or alt-left/alt-right to change to the correct window?

The old switcher which changed to the previous window when hitting alt-tab was MUCH MUCH better for working on something that requires changing windows often. My productivity is lower because of this annoyance, and I have no idea what the big idea behind this grouping business is. It's certainly not solving any of my problems.

Rant!

Please change the behaviour, Mr. Unity developer...?

---

### Post by Mr_JMM on 2012-11-15
You must have a different version of Unity than me..

I hit alt-tab, the window appears with all the apps, if I have more than one of teh same application running (common is Firefox or terminal) I highlight that app, pause and it splits into the different windows.

Granted, not as easy as showing every window individually but I persoanlly prefer it. No clicking involved.

---

### Post by k999 on 2012-11-15
What you describe is exactly what I have. But if I have two terminals and a browser on the same window, it takes too long to switch from one terminal to the other. And if I have 8 terminals, it's not easy keeping track of which is which! 

This all used to be much better. Switching to another window of the program I'm running almost always requires the waiting you say or alt-arrowdown, otherwise it often (but not always) stays on the same window. WTF, why did Unity think I clicked alt-tab in the first place? 

In my opinion, this new behaviour is a usability disaster. It is for me anyway, and it's certainly not simple to revert the behaviour. The recipes online using ccsm doesn't work out of the box for Ubuntu 12.10, so they're not much help either.

---

### Post by stinkeye on 2012-11-15
Hold alt and press tab.
When you come to grouped windows continue holding alt and press ~ (key above tab)to cycle through the grouped windows.

I find scale better to select windows.
Enable the **scale** and **scale addons** plugins in ccsm.

I set the top edge+button1 to initiate scale for all windows.
The scale addons[/B] plugin allows you to, while in scale mode, 
zoom windows with right mouse and close windows with middle click.

---

### Post by Mr_JMM on 2012-11-15
When I'm in a similar situation, with mulitple terminal windows open I put them on a different workspace and if they're not related I split them to different workspaces. You will still have the slight pause to slect a window but you won't have to worry about other non-related applications.

Other than that, you could go back to gnome, I believe that has the older style.

[edit] Wait, how long is your pause? For me it's barely more than a blink before the application splits and shows me numerous terminal windows which I can easily see the contents of.

---

### Post by k999 on 2012-11-15
stinkeye, thanks, I wasn't aware of the scale stuff. But I usually work on a laptop, so I really dislike having to use the mouse to switch windows. I work on the keyboard as much as possible, so that's not a good solution either.

Mr_JMM, splitting related tasks across viewports is possible, but working around Unity isn't really the best option. Fixing Unity is the way to go. 

It's not a long pause, but I lose the flow of what I'm doing every time I have to stop and search and do something like that manually. That opens up for mistakes. I often work on many things over a period of time, but when I'm focused it's often a matter of changing something one place, and testing another place. It works, but it's not good, and it's not an improvement.

Who thinks Unity's alt-tab behaviour is better than the old behaviour? And why? I just don't get it, help me out! Am I using it wrong, or is everyone working around it and just accepting it?

---

### Post by jerome1232 on 2012-11-15
I just wanted to note, alt+~ will switch between windows of one app, so if you're in firefox, and want that download window (get a status bar download addon *cough*) you can press alt+~ to easily get to it.
That also works while alt tabbing, so alt+tab over to terminal group, then alt+~ to tab through it's open windows.

---

### Post by snowpine on 2012-11-15
Use Alt+TAB to switch between different apps.
Use Alt+` (the key above TAB) to switch between different windows of the same app (different terminals, browser windows, etc.)

It is SO EASY and exactly the same as Mac OS. (by which Unity is heavily insipred) If you take a few minutes to **read** the Unity shortcut keys (maybe print them out and tape them to your desk/wall) then you will not be so confused/frustrated. :)

---

### Post by k999 on 2012-11-15
jerome1232, thanks, but to get ~ on a Norwegian keyboard I have to click:

Alt-Gr-<umlaut> space

so that doesn't work well. But if I can reallocate that, it could be useful. But I still feel it's a workaround for the ****** unity behaviour.

---

### Post by snowpine on 2012-11-15
> **k999 said:**
> jerome1232, thanks, but to get ~ on a Norwegian keyboard I have to click:

Alt-Gr-<umlaut> space

so that doesn't work well. But if I can reallocate that, it could be useful. But I still feel it's a workaround for the ****** unity behaviour.

I'm sure it can be allocated but I'm not sure how (I'm not an Ubuntu/Unity user myself).

It is not ****** but rather a usability enhancement/improvement borrowed from Apple. If you have 8 browser windows and 12 terminals open for example, now you can switch from browser to terminal with 1 keystroke (whereas before you might need 9 or more keystrokes). Obviously we can debate whether this change is easy/effective but at least now you know the reason why. :)

---

### Post by jerome1232 on 2012-11-15
By ~ I meant ` see snowpines post, not sure if that's a difference on your keyboard.

You might like the scale feature super+w

---

### Post by k999 on 2012-11-15
snowpine, on a norwegian keyboard, ` is on: 

AltGr-\ space

so it doesn't work. But it seems alt-| might work to switch between windows in the same group. That's a start...

But again, does anyone actually think Unity's behaviour is an improvement over the old behaviour? Why is it better, and how does it help you work more efficiently??

---

### Post by jerome1232 on 2012-11-15
A resounding yes for me. When I have 3-4 browsers open, 5-10 terminals open, and 10 tomboy notes open, I don't have to tab through all of that to get to a place, I have 3 tab groups (4 including show desktop), so I can quickly tab to the group I want and go through only it's windows, so no tabbign through 20 windows to select between my 3 browsers windows.

It's a god send.

---

### Post by snowpine on 2012-11-15
> **k999 said:**
> snowpine, on a norwegian keyboard, ` is on: 

AltGr-\ space

so it doesn't work. But it seems alt-| might work to switch between windows in the same group. That's a start...

But again, does anyone actually think Unity's behaviour is an improvement over the old behaviour? Why is it better, and how does it help you work more efficiently??

As I mentioned above, it gives the user **more control** by splitting "switch to a different app" and "switch to a different window of the same app" into separate keystrokes. We can debate whether/why giving the user more control is a good thing, but it is pretty much the core of the open-source philosophy. Also the new Alt+` paradigm is used by Apple (a company generally lauded for their usability/design) and by the upstream Gnome developers. So in order to NOT use Alt+` and go back to the old Alt+TAB behavior, Ubuntu would have to deviate from the upstream desktop environment. :) (I haven't tried Windows 8 yet so I'm not sure which they use.)

---

### Post by snowpine on 2012-11-15
Another way to explain it is that Ubuntu is trying to provide a consistent interface and easy learning curve for users who might be transitioning from Mac OS or from other Linux distros that use Gnome. :)

---

### Post by deserthowler on 2012-11-15
If you mostly switch between terminals, you might like quake.  It's in the repo.  It activates with F12 as a dropdown and allows tabs.  Works for me.

Earl

---

### Post by gcbzzzz on 2013-02-22
> **jerome1232 said:**
> A resounding yes for me. When I have 3-4 browsers open, 5-10 terminals open, and 10 tomboy notes open, I don't have to tab through all of that to get to a place, I have 3 tab groups (4 including show desktop), so I can quickly tab to the group I want and go through only it's windows, so no tabbign through 20 windows to select between my 3 browsers windows.

It's a god send.

i have one browser, 2 or 3 terminal. and want to use the keyboard only. A much more common use case if you allow me to guess so.

i'm either alt-tabbing from terminal 1 to terminal 2, or from browser to a terminal... having to expend brain resources to everytime remember which alt-tab i need is retarded. "am i at the browser? do i press alt-tab or alt-`? duh pressed the wrong one, now do i press the same again or try the other? duh! wrong again!"

now, your use case is perfect and i always used it, and you can use something much better than that let's-copy-osx-like-we-can't-think-for-ourselves... if have several windows of a class open, and you need to go to that class of window, just press flag-N, N being the number you assigned for that application on the dasher.

So in your case, you need to go to a terminal window, press flag-1 and all terminal windows will open. Need to go to one of the 100 stick notes, press flag-3 and they will open up.... but again, zero for usability. it's impossible to change windows using the keyboard alone. why doesn't it clycle windows? because no unity developer actually uses the keyboard! and since they decide features for themselves, you have to use the mouse as well.

summing up, you now have 3 ways to change windows using the mouse, and one broken for using the keyboard.

yeah, i know, if people think there's something better they will write a patch. well, i've written patches for metacity and compiz for even smaller things. now i'm just using Mate.


> **snowpine said:**
> Another way to explain it is that Ubuntu is trying to provide a consistent interface and easy learning curve for users who might be transitioning from Mac OS or from other Linux distros that use Gnome. :)

they are blindly forcing users to use ubuntu like mac. in compiz it was already possible to configure it like the mac. So if your idea was true, they would simply ship with a pre-configured compiz with defaults like the mac.

But no, they ship with the defaults like the mac alright, but they also removed every personalization option to make it better than the mac (as it always was). Why? beat me. if i had to guess, i'd say someone is being very well paid by apple under the table to make this so :D

---

### Post by jerome1232 on 2013-02-24
> **gcbzzzz said:**
> 
now, your use case is perfect and i always used it, and you can use something much better than that let's-copy-osx-like-we-can't-think-for-ourselves... if have several windows of a class open, and you need to go to that class of window, just press flag-N, N being the number you assigned for that application on the dasher.


I have a lot of applications on my launcher, more than I have numbers, and I don't want to memorize what order they are in. That method also doesn't allow me to tab through the windows of that application, it just brings up the most recently used window, or opens it if it's not already open.

It doesn't take me much brain power to know that I'm Mozilla and want another Mozilla window and to press alt+` instead. Or to know that I'm in rhythmbox and want to get to a terminal. I get it, you don't like it.

In what way is it impossible to use the keyboard alone? You don't need to involve the mouse one bit with the alt+tab/alt+` method. I'm not sure why you would even suggest you have to use the mouse, I wasn't even aware you could use the mouse with the switcher.

Last this change came from the gnome-devs, so your suggesting the gnome-devs are being paid off to use their window switcher method... ok. sure. :eyeroll:

---

### Post by CaptainMark on 2013-02-25
I agree on the behaviour not being a good thing, you can however just open a tabbed terminal session, pressing ctrl+shift+t in gnome-terminal will open a new tab and then you can use ctrl+pageup/pagedown to switch tabs. 

Your other option (and my choice) is to ditch unity all together and use cinnamon or mate desktop environments, they return to you the control over your desktop that you used to have in the days of old before unity came and made me hate ubuntu

---

### Post by bugbear6502 on 2013-04-26
I too hate this behaviour - my normal mode of work is a large number of GVIM windows and a large number of xterm command windows.

There will commonly be 2-3 GVIM windows and a command window to a particular "project" (e.g. a couple of source or config files and a shell to run them).

The "stodgy old" behaviour with the "LRU" stack property on the windows allowed the windows of any particular "project" to be easily accessible via alt-tab.

The point being - the "natural" grouping for my windows is NOT NOT NOT via application, but Unity is forcing that upon me.

  BugBear

---

### Post by k999 on 2013-04-27
> **bugbear6502 said:**
> I too hate this behaviour - my normal mode of work is a large number of GVIM windows and a large number of xterm command windows.

There will commonly be 2-3 GVIM windows and a command window to a particular "project" (e.g. a couple of source or config files and a shell to run them).

The "stodgy old" behaviour with the "LRU" stack property on the windows allowed the windows of any particular "project" to be easily accessible via alt-tab.

The point being - the "natural" grouping for my windows is NOT NOT NOT via application, but Unity is forcing that upon me.

  BugBear

I couldn't agree more. This is how I work too, and exactly how I experience the problem. I've been using this for months now, and it is absolutely horrible. I dislike it with a vengeance, and one day I'll probably switch away from Unity simply because of this. And it's not because I've not tried, it just doesn't do what I need.

---

### Post by bugbear6502 on 2013-05-07
I've re-read the thread, and I now think I see the problem.

For many people, their task does indeed group by application, and thus the two "modes" (switch application/switch window) are nicely usable.

But for some people (including me) tasks do NOT group by application. And this breaks the unity model utterly, rendering it horrendous.

 BugBear

---

### Post by k999 on 2013-05-07
Yeah, and I'm with you on this. I still don't see how this is so great. Browsers for example have moved from multiple windows to multiple tabs, and ctrl-tab/ctrl-shift-tab can be used to flip through those easily. Now I have alt-tab, ctrl-tab AND alt-|. How many levels of this stuff do we need? And with this behaviour, I'd hope it was at least consistent by making alt-| switch windows within application and alt-tab switch between apps. But no, in some cases alt-tab and alt-| bring me to the same window (eg firefox's download window when using firefox).

I do see how some applications perhaps have multiple windows that you'd want to switch between, then perhaps use a browser a bit, and then return to your app and flip through app windows later. But I certainly don't think unity has made my life easier in any way at all. And it must be so easy to add an option for MRU alt-tab behaviour... It's very frustrating.

---

### Post by markbl on 2013-05-08
> **bugbear6502 said:**
> 
But for some people (including me) tasks do NOT group by application. And this breaks the unity model utterly, rendering it horrendous.
The Unity (i.e. modern) way to do that is to put related windows into their own workspace. It works very well. Then you alt+tab/backtick between windows in the current workspace and ctrl+alt+up/down to "context switch" yourself between tasks, i.e. between whole groups of windows in workspaces. Remember also that shift+ctrl+alt+up/down moves the current window to another workspace.

I use GNOME-shell rather than Unity but the above also applies to GNOME-shell. I much prefer GNOME-shell's "dynamic" linear workspaces to the traditional Unity 2D static workspaces. It's a really smart idea.

Seriously guys, don't just look for what you had before. We have moved on and the modern DE can improve the way you work. You have to make an effort to learn new ways however.

---

### Post by coldraven on 2013-05-08
> **stinkeye said:**
> Hold alt and press tab.
When you come to grouped windows continue holding alt and press ~ (key above tab)to cycle through the grouped windows.

I never knew that, it works really well.

---

### Post by pompel9 on 2013-05-08
> **k999 said:**
> snowpine, on a norwegian keyboard, ` is on: 

AltGr-\ space

so it doesn't work. But it seems alt-| might work to switch between windows in the same group. That's a start...

But again, does anyone actually think Unity's behaviour is an improvement over the old behaviour? Why is it better, and how does it help you work more efficiently??

What Norwegian keyboard do you have? If I press AltGr-\ space it only makes a space (If there are any open windows where you can write). I use a Norwegian keyboard as well.

To access `I have to press Shift + the key that is to the left of backspace.


Edit: I have had many different keyboards, and they have all been the same way.

---

### Post by k999 on 2013-05-24
pompel9, when I hit Shift-backspace, nothing happens. Then, when I next hit space, the ` appears.

---

### Post by k999 on 2013-05-24
>  Seriously guys, don't just look for what you had before. We have moved on and the modern DE can improve the way you work. You have to make an effort to learn new ways however. 

markbl, I think you're bordering on trolling, and you're certainly not very constructive. Why don't you think I've made an effort? I've been using Unity since it arrived, and after a couple of years I still don't find it suitable for my workflow. The old "most recently used" works much better for the way I work, it lets me switch to the window I want much faster. Of course, I'm sure you think I work wrong.

---

### Post by markbl on 2013-05-24
> **k999 said:**
> markbl, I think you're bordering on trolling, ...
2 weeks to reply and that is it?!

I'm not criticizing anybody specific. It's just human nature to resist change with most things in life, not just DE's. The GNOME and Canonical guys have thought hard about this stuff and have made changes to improve the way we work. They are not idiots.

---

### Post by Paper Bag on 2013-06-02
If there is one thing I really like about Unity, it's the switcher. Sometimes it is more complicated, but most of the times I find it better. But:

- I would like to be able to switch between windows of the same application that are *on the current workspace *only (and not on all workspaces), without first pressing Alt+Tab* and then Alt+`. This is possible by enabling "Bias alt-tab to prefer windows on the current viewport" (ccsm / unity plugin / switcher tab), but this causes behaviour that makes alt-tabbing as a whole just unusable (=> [launchpad bug]("https://bugs.launchpad.net/unity/+bug/928145")).

* I have changed it to "Key to start the Switcher for all viewports" (is it just me or this name for the shortcut confusing? :D It's like it suggests the opposite of what it actually does... i.e. shows only the applications on the current workspace)

- Another thing that I really don't get is the logic how the windows of the same applications are arranged and rearranged once you flip to some of them and cycle to another one etc. The logic seems different to the old Gnome 2.x era alt-tab? I just can't do it intuitively at all, I always have to look at the window title/preview thumbnail.

- I don't like how 13.04 made the space between the icons wider vs. 12.10 (pic below). Would be nice if you could actually adjust the size of the icons too...

- The "pips" (do they have another name? Omgubuntu calls them "pips" - the small silver/grey icons in below screenshot that also appear in the launcher): why on earth are they limited to three?! In practice they are only useful for indicating whether you have more than 2 windows/instances of the same application open, since you will see three "pips" if you have 3 windows, and you will see three "pips" if you have 30 windows open. So pointless! Also, they still look ugly especially against certain background colors.

[IMG]http://www.omgubuntu.co.uk/wp-content/uploads/2013/04/pips.png[/IMG]

---

### Post by Paper Bag on 2013-09-21
I made a bug about those useless "pips" a while ago: [https://bugs.launchpad.net/unity/+bug/1211065](https://bugs.launchpad.net/unity/+bug/1211065)

WontFix'd because design decision. Somehow I wasn't surprised at all.

And finally figured out what is so confusing about the alt+tab "preview windows" view: somehow my brain expects that when I press alt+tab and then alt-down, the window selected is the one I have already open/active. So this makes it feel like the cycling goes counter-clockwise. I just can't do it intuitively. :confused:

---

