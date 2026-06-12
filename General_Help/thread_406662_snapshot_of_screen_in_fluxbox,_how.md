---
title: "snapshot of screen in fluxbox, how??"
date: 2007-04-11
forum: General Help
---

### Post by r0ck80y on 2007-04-11
Hi

How can i get a snapshot of the screen in fluxbox ( no kde or gnome installed); is there something like ksnapshot for fluxbox??

Thanx in advance

---

### Post by kerry_s on 2007-04-11
I use scrot> sudo apt-get install scrot

[submenu] (ScreenShots)
 [exec] (Snap) {exec scrot %T.jpg}
 [exec] (Select) {exec scrot -s -b %T.jpg}
 [exec] (Wait 5) {exec scrot -d 5 %T.jpg}
[end]

Here's the keys entry if you want the print button to take snapshot.

None Print :Exec scrot %T.jpg

---

### Post by kc8hr on 2007-04-11
You could also use ImageMagick. It is probably already installed on your system.

Here is the line I use in my menu file:

[exec] (Screenshot - JPG) {import screenshot.jpg && display -resize 50% screenshot.jpg}

When you execute the 'import' command, your cursor will change and you have the opportunity to select either the entire screen or just an open window.

The image in the command above will produce a jpeg, but it also supports PNG, etc.

Good Luck!
Tim

---

### Post by kerry_s on 2007-04-11
> **kc8hr said:**
> You could also use ImageMagick. It is probably already installed on your system.

Here is the line I use in my menu file:

[exec] (Screenshot - JPG) {import screenshot.jpg && display -resize 50% screenshot.jpg}

When you execute the 'import' command, your cursor will change and you have the opportunity to select either the entire screen or just an open window.

The image in the command above will produce a jpeg, but it also supports PNG, etc.

Good Luck!
Tim

I forgot all about imagemagick.
Hey what's the setting for doing several shoots, example: in scrot i use %T which goes off the time so i can take several in a row and they won't overwrite the last 1?

---

### Post by RedSquirrel on 2007-04-11
> **kerry_s said:**
> I forgot all about imagemagick.
Hey what's the setting for doing several shoots, example: in scrot i use %T which goes off the time so i can take several in a row and they won't overwrite the last 1?

```
`date +%T`.jpg

```

---

### Post by kerry_s on 2007-04-12
Hey, thank you RedSquirrel. Got rid of my scrot and im using->

```
[submenu] (ScreenShots)
 [exec] (Snap) {exec import `date +%T`.jpg}
 [exec] (Wait 5) {sleep 5s; exec import -window root `date +%T`.jpg}
[end]

Print key:
None Print :Exec import `date +%T`.jpg && mogrify -resize 1024x768 *.jpg

```

My usual screen shot, resized to 1024x768 for yabadaba.

---

### Post by kc8hr on 2007-04-12
Excellent!

Here is my fluxbox desktop.

---

### Post by RedSquirrel on 2007-04-12
> **kerry_s said:**
> Hey, thank you RedSquirrel. Got rid of my scrot and im using->

```
[submenu] (ScreenShots)
 [exec] (Snap) {exec import `date +%T`.jpg}
 [exec] (Wait 5) {sleep 5s; exec import -window root `date +%T`.jpg}
[end]

Print key:
None Print :Exec import `date +%T`.jpg && mogrify -resize 1024x768 *.jpg

```My usual screen shot, resized to 1024x768 for yabadaba.


No problem.

By the way, you might want to look at:

```
import -help
```to see all of the nifty options you can use. Two that might interest you are: "-pause 5" and "-resize 1024x768".

I've been meaning to ask: what is that system monitor in the top-right corner of your screenshot? And which pager is that in your toolbar? (I like to keep my desktop as clean as possible, but... you know... I like to experiment too! :) )

---

### Post by RedSquirrel on 2007-04-12
> **kc8hr said:**
> Excellent!

Here is my fluxbox desktop.


Nice. Which calendar app is that? (on the left-hand side)

---

### Post by kerry_s on 2007-04-12
> **RedSquirrel said:**
> No problem.

By the way, you might want to look at:

```
import -help
```to see all of the nifty options you can use. Two that might interest you are: "-pause 5" and "-resize 1024x768".

I've been meaning to ask: what is that system monitor in the top-right corner of your screenshot? And which pager is that in your toolbar? (I like to keep my desktop as clean as possible, but... you know... I like to experiment too! :) )


Import -help, but i got you, why should i look it up? :lolflag:

I use conky for my monitor.

I'm using fbpager, i was using fluxter but i want to stay with repo apps only.

The others are wmdrawer, mixer.app and bbrun. I put the wmdrawer for my son he just hates the right click and i don't like icons on my desktop. it was a compromise. So i just have the most used apps in there.

Okay i fixed it->  [exec] (Wait 5) {exec import -pause 5 -window root `date +%T`.jpg}
and
None Print :Exec import -resize 1024x768 `date +%T`.jpg 

Thanks again.

---

### Post by kc8hr on 2007-04-13
> **RedSquirrel said:**
> Nice. Which calendar app is that? (on the left-hand side)

It is an adesklet:

[http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)

Similar to gdesklets, but does not require Gnome. I fiddled with the color scheme a bit.

Later--
Tim

---

### Post by RedSquirrel on 2007-04-17
> **kerry_s said:**
> Import -help, but i got you, why should i look it up? :lolflag:

I use conky for my monitor.

I'm using fbpager, i was using fluxter but i want to stay with repo apps only.

The others are wmdrawer, mixer.app and bbrun. I put the wmdrawer for my son he just hates the right click and i don't like icons on my desktop. it was a compromise. So i just have the most used apps in there.

Okay i fixed it->  [exec] (Wait 5) {exec import -pause 5 -window root `date +%T`.jpg}
and
None Print :Exec import -resize 1024x768 `date +%T`.jpg 

Thanks again.


Hey, no problem. :)

Ah, conky. I've heard its name here & there but I never bothered to look it up. Looks neat.

I kind of thought that was fbpager. I played around with that a while ago. I prefer a pager with thumbnail previews of the desktop (like enlightenment has, for instance), but I don't think there is a pager like that that I can use with Fluxbox. Back in the old days, when I had sawfish and GNOME, the pager had those previews and I got rather used to that look. The pagers these days that only have "icons" or just blank rectangles look pretty sad to me. :(

I don't use the right-click all that often. I've set the keys on my keyboard that are supposed to open the Windows Start Menu to open the Fluxbox menu. Here are the entries from my keys file:

```
Super_L :RootMenu
Super_R :RootMenu

```Those keys are within easy reach, so it's great (for me).

---

### Post by RedSquirrel on 2007-04-17
> **kc8hr said:**
> It is an adesklet:

[http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)

Similar to gdesklets, but does not require Gnome. I fiddled with the color scheme a bit.

Later--
Tim


Thanks for the info. I'll have to experiment with that. :)

---

