---
title: "Half-rant, half-question: Ubuntu's Biggest UI Failure"
date: 2008-05-21
forum: General Help
---

### Post by camerong on 2008-05-21
By far, in my opinion, the biggest UI failure of Ubuntu is that for some stupid reason the log off/shutdown button is in the top right hand corner of the screen. Which means every time you reach the mouse to close a program, you risk being prompted to shut off your computer. I can understand it from a "the entire OS is a program" standpoint, but it's pretty damn dumb as far as user-interaction goes.

So I want to make it so when i hit super-S i get that same log off choice box.. how do i make it pop up via terminal commands?

thanks, and is there really a half-decent reason for it to be there by default in the first place? Why not bottom right?

---

### Post by cdenley on 2008-05-21
That applet can be moved, removed, or added wherever you want. I always use System>Quit.

To bring up the "Quit" menu
```

gnome-session-save --kill

```

---

### Post by bingoUV on 2008-05-21
Lots of theoretical psychology and practical studies need to go into these things, but I will try :
1. Quit an application -> Top right. Quit the session -> Even more top right. So top right becomes associated with quitting things.
2. Developers are geeks. They customize their own system so much that they forget how the default looks. This may not be a valid excuse but could be a reason.

Me? My quit application is in top left of a window. Quit session is only in System menu, no panel icon. You can move around your buttons to your liking. It is not like Internet Explorer 7.

PS:
I do realize good defaults are important.

---

### Post by eentonig on 2008-05-21
Is there a button to shutdown? You mean I don't have to type 'gnome-session-save --kill' everytime I want to stop the computer? 


No seriously. I have no idea why it's there. But I agree it's annoying after a default install. But then, it doesn't bother me that long, as one of my first tasks after a new install, is to change the entire GUI to my liking. (loose bottom panel, group the menus under one icon, remove some unneeded buttons on the top panel, install awn...)

---

### Post by danwood76 on 2008-05-21
My solution, be more accurate with your mouse.
Ive never had this as an issue, though I suppose regarding the previous post I probably fit into this 'geek' category.

But as already said you can put that applet wherever you like, you can change shortcut keys in System -> Preferences -> Keyboard Shortcuts if you want to do what youve said

---

### Post by issih on 2008-05-21
As the above two have said, the button can be moved, just right click on it and select remove from panel.

You can also drag the whole top panel down to the bottom of the screen if you like, that way the very top right hand corner of the screen will be the close button of a maximised window,like in windows. These kind of things are inevitably a matter of personal taste, some love things some hate them, windows has bar at bottom, macs at top, ubuntu (by default) both. In ubuntu though, its entirely up to you, its all configurable...have it how you want it.

As for logout on super s, just go to System->Preferences->Keyboard Shortcuts
then set whatever you want to trigger the logout dialog

That ought to get you what you want

Hope that helps

---

### Post by superyounan1 on 2008-05-21
its only annoying because you're used to windows, if you were used to gnome for 10 years then switched to windows, you'd have just as many annoyances, except the difference with gnome is if you don't like it, you just change it. 

People are just plain used to having every computer look the same. It might be easier, but theres no law for this, I'd much rather customize my environment so that it suits me specifically, then I'll be more productive and I won't feel like i'm using a cookie cutter interface, in fact, there might not be ANY computer out there that looks like mine

---

### Post by aroch1 on 2008-05-21
If you don't like where it is, move it...check out your options before you rant, freedom is what it's all about.

Think first next time!

---

### Post by camerong on 2008-05-21
some people didn't get the question:

> If you don't like where it is, move it...check out your options before you rant, freedom is what it's all about.

Think first next time!

I knew how to move it, I wasn't sure how to modify the keyboard shortcut so I could launch the command. But thanks to some helpful people, I got that.

Anyways, I think it's a poor choice to have it there by default, even though it makes sense in a geeky way.

---

### Post by danwood76 on 2008-05-21
At the end of the day, geeks rule :-P
Hehe.

Its the GNOME default to have it there, KDE have all that stuff in a different place so you may want to try that out. (its more like windose)

---

### Post by strabes on 2008-05-21
This is funny because I **love** having the quit button on the top right of the screen. It's one of the few defaults that I **don't** change on a new install. :) Oh well - to each his own - that's what's great about GNU/Linux & FOSS!

---

### Post by Cap'n Skyler on 2008-05-21
move or re move the offending button:guitar:

---

