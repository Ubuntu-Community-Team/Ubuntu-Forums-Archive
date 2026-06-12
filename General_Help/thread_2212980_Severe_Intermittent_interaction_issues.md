---
title: "Severe Intermittent interaction issues"
date: 2014-03-24
forum: General Help
---

### Post by john_smith9 on 2014-03-24
Hello.

I've been trying to make the full switch from windows to linux but I'm having a very hard time trying to fix a problem i'm encountering on several distros i've tried (Linux mint,kali, now ubuntu)

It's been difficult for me to get help because the problem is not very straight forward and difficult to explain but i'll try my best here.

------------------

At seemingly random times I partially lose ability to interact with everything but the current active application.

The easiest to explain example is probably in Firefox but it happens in everything from terminal,xchat, and even the shell.

Lets say I'm browsing the internet in firefox and it happens...

The ability to left or right click anyware outside the firefox application is lost (I can still move the mouse) (I can also not interact with the very top part of firefox with the minimise,exit buttons etc)
The ability to alt tab, alt-f2 and most other keyboard shortcuts is lost. 
The only keys I can use reliably are TAB and alt-f4
Interaction with any new dialog boxes that pop up from the main application (Such as the close tab confirm dialog) can only be done using TAB,TAB, enter.
If I can manage to close firefox with alt-f4,tab,enter then the problem goes away about 60 percent of the time but sometimes I'm left stuck inside the next application or sometimes at the desktop.
Normally firefox continues to be usable and does not lag at all during the time its stuck.

This happens on cinnamon, Gnome,KDE and preferably everything else.

-----------
Sometimes I get stuck inside a particuler field in a particular application, while I was in linux mint I got stuck inside the xchat chat box and I could not interact with anything else on the computer.
----------

This happens between a few seconds and a large number of miutes after beginning normal interaction with a program so I can not do anything productive or enjoyable while this effects all of my linux experience.
There does not seem to be any slowdown, extra noise, heat or lag when this happens.
----------------

Hopefully I explained this well. I'm desperate for a permanent fix or even some ideas on things I could try.

Thanks for your time.

---

### Post by dragonfly41 on 2014-03-24
You say that you encounter these same symptoms on different linux distros .. not just Ubuntu.

Do you experience these symptoms on Windows?

Sounds like a hardware glitch.  As a first guess I would start with an exhaustive memory check.  If that passes we can think of other possible causes.  What is your hardware configuration?

---

### Post by john_smith9 on 2014-03-24
I've never encountered symptoms like this on windows.

I'll check into my hardware configuration tomorrow, right now I can remember having 16gb DDR3 ram, intel i7 processor, 120gb SSD (I don't use this for OS because SSD's corrupt everything) 1tb WD green harddrive and a 500gb WD black (My OS drive) I also have a ATI radion HD 5970 graphics card.

Are there any sort of live feed event loggers for linux like Sysinternals Process Monitor for windows that I could leave open to perhaps debug to problem.

I've got two keyboards and tried multiple mouses but there does not seem to be any problem there.

---

### Post by dragonfly41 on 2014-03-24
If you're looking for sysinternals type monitors (they are very useful in Windows) start 
installing **System Monito**r through Ubuntu Software Centre.

it should appear as icon / applet on the Ubuntu top menubar

When your system next hangs click on this to inspect cpu load.

Also from this dropdown open System Monitor

under Processes tab look for high cpu utilisation processes

Resources shows CPU and memory utilisation.

There are usually peaks if there is a problem in a library or app.

Look under other tabs for useful information.


**htop** is another similar useful process monitor tool.

You can "kill" processes using either of the above.

---

