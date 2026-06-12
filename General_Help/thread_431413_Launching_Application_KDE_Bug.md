---
title: "Launching Application KDE Bug"
date: 2007-05-03
forum: General Help
---

### Post by odelay on 2007-05-03
I know this bug affects tons of people, but I've yet to see any conclusive fixes...just a bunch of one-reply "me too!" threads.

When using a link in one application to open another application, instead of properly opening the link, a new instance of the application is created in the taskbar.  This mystery task, stays there for about 30 seconds saying "Loading Application", and eventually disappears.  The actual link does load in the existing instance of the app, but this weird extra process slows down everything and makes using KDE a complete pain.

For example, in Kontact, I get dozens of emails a day containing URL's I need to visit (say, to reply to this post).  When I click the link, the page starts to load in my existing instance of Firefox tab, but a new Firefox process pops up in the taskbar, using tons of CPU and slowing everything down.  I pretty much have to wait 30 seconds for this to disappear before I can do anything.

Another example.  I've created a handful of executable shell scripts to carryout commands I use a lot.  When I select one of these, it executes properly, but the process remains in the taskbar an additional 30 seconds slowing everything down.

This is absolutely crippling Kubuntu for me (and many others).  Is this EVER going to get fixed?!?

Thanks

---

### Post by odelay on 2007-05-04
Anyone?  I'd even settle for a "me too." :D

---

### Post by AndrewNi on 2007-05-04
I turned off the loading feedback using an option in KControl to stop that from happening.

---

### Post by SigmundFreud on 2007-05-04
I think you mean, under 'appearance & themes', you set the 'startup indication timeout' to 0 seconds. I'll give that a try (yes, that's a 'me too!'). I hate that bug when I open a html file with Firefox opened. Does it help for you?

---

### Post by odelay on 2007-05-07
Sorry for the delay, I was out of town.

I'm having trouble finding this option.  I go KMenu > System Settings > Appearance, but I can't find anything in any of the submenus.

Thanks for the help.

---

### Post by hvbakel on 2007-05-07
try this:

KMenu > run command > type: kcontrol > appearance and settings > Launch feedback

---

### Post by odelay on 2007-05-08
Sweet...thanks!

You can also go into the kMenu editor to set individual launch properties for each application....however you can only enable or disable it (there's no way to set the time).

---

### Post by Chaotic Thought on 2007-08-15
I know this thread has been inactive for awhile, but I'm finding it just now. I've observed the same behavior as the OP describes. Here's whats happening: the KDE "busy cursor" thingy assumes that when you click the launcher, the program will eventually open a new window with a new PID (process ID). When the new program window opens, KDE is set to turn off the "busy cursor". But since your program is already running, it never opens a new window but simply re-uses the one that's already open, and so the "busy cursor" continues to wait, thinking that the program hasn't finished starting yet. After 30 seconds, the "busy cursor" gives up (in the KDE control center you can change this time limit if you wish).

The problem I think is that the busy cursor makes the mouse cursor movement very jerky and *seems* to be consuming CPU, but actually the busy cursor doesn't use any CPU (all it's really doing is waiting for a new window). In any case, the behavior is not good. Unfortunately, Linux currently does not have any decent launch feedback for applications. Some people put little CPU monitors on their desktop and similar stuff as an alternative.

---

