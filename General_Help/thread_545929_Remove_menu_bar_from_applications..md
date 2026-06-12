---
title: "Remove menu bar from applications."
date: 2007-09-08
forum: General Help
---

### Post by Tautoa on 2007-09-08
Hey all, 
I'm going through a phase of making the whole appearance of my computer very minimalist, so I've been going through all the apps I use, configuring the toolbars to contain the functions I need, and then hiding the menubar (the File, Edit, View thing, not the 'start' menu, as Windows would call it).

Problem is, some apps don't seem to allow you to hide the menubar. I'm using KDE, and usually hitting ctrl+M will hide the bar, but some apps (Kontact, for one) won't do it.

It's not exactly a major problem, but it's gonna bug me, so any help is welcome :)

---

### Post by kidders on 2007-09-09
Hi there,

I don't think I'd like menu-less application windows personally ... but that doesn't mean *you* shouldn't be able to do it, imo. I took a quick look around the web, and you're not alone ... the inability to hide the menu bar in certain applications irritates some users, but half the time, they just seems to get laughed at when they bring it up. :confused:

Initially, I felt pretty confident I could find a dcop call, a config option ... *something* that would help you out, but I couldn't. Would it be ridiculous to experiment with patching certain KDE apps to hide their menus?

---

### Post by Tautoa on 2007-09-09
Actually, I was thinking about getting into programming...
My only relevant experience is "Hello World" type things in Visual Basic, and some macros I wrote in VB for my IT A-Level (just before I discovered Linux), but I'm definitely willing to learn.

Because the ability to hide the menubar exists in some KDE apps (Kopete springs to mind), then the relevant code already exists, so it should be a simple matter of pasting the code into other apps, adding and editing a little bit, and then building the program again... am I right?

If so, it sounds like a great place for a newbie programmer to start, if someone could give me a gentle prod in the right direction? (there's probably webpages designed to teach people like me somewhere, right?)

I'm glad I asked now, thanks :)

---

### Post by kidders on 2007-09-10
Lol that's an interesting response! I was expecting something along the lines of "Patch KDE?! Don't be daft!".

If you want to try it though, there are a few things to be aware of.
[LIST]
[*]Distros like Ubuntu are not really designed with users like you in mind. For example, be sure you understand how things like system updates work, so you can learn to defeat attempts they may make to overwrite your changes.
[*]Try not to make significant code changes, as these can interact badly with the rest of your system.
[*]VB is (was?) an extremely high-level language, so exposure to the way code execution *really* works, is quite limited. Coding in C, on the other hand, gives you real scope to destabilise your system, so you need to be that bit more careful.
[*]It's important _not_ to use source code from KDE's official website ... or at least not to *mix* it with code (or compiled code) that doesn't. Stick to Ubuntu's official repos if at all possible.[/LIST]I would suggest investigating the possibility of using a dcop call to set the height of an application's menu bar to zero or something ... you know ... the kind of change that wouldn't force you to alter every single code fragment that interacts with the menu.

In terms of prodding you in the right direction...

KDE's devs, like Gnome's, have evolved their own development architectures and ways of doing things over time. Consequently, the www is littered with APIs and other documentation specifically designed to help people interested in tinkering with KDE. Don't forget that it's often possible to get into direct contact with software developers (on IRC, for example) ... but I would strongly recommend *against* doing that until you have a pretty good idea of what you're talking about.

Since you mentioned VB, I should add one more (albeit totally random!) note. When you're coding in C, always think *memory*. It's easier than you might think to create code that will eat up all your RAM, or upset your system & start crashing things. Getting into the habit of being ruthlessly memory-efficient should help you side-step any land mines.

Anyhow, I hope that's at least sort of helpful! Hopefully you can get away with rebuilding only small parts of something like Kopete. Having built KDE from source more times than I care to count, I can tell you it's a *mammoth* piece of code hehe.

---

### Post by Tautoa on 2007-09-11
Haha, thanks for the advice.
Rather than continue to bombard you with questions, I'm gonna go google a whole bunch of things and see what I come up with...
Trial and error has taken me to some interesting places using (K)ubuntu, (its also forced me to reinstall from LiveCD twice in one day before now...), so I'm sure I can have fun with this :)

Thanks again, and I'll post again if I solve the menubar problem :) (first, I'm gonna go find out what you mean by dcop... I hear it a lot but never had a reason to find out what it meant) :)

---

