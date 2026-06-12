---
title: "Lost workspace selector and all windows are messed up"
date: 2007-05-25
forum: General Help
---

### Post by NeedMoreThyme on 2007-05-25
Okay, I am extremely new to using Ubuntu and I don't know much about technical stuff in general.    I've been running Ubuntu (fiesty) for several weeks without any problems.  Then yesterday I installed a new RAM card in my laptop (an hp pavilion ze4400).  I left the old memory card in there, just put a new one in the empty slot.  I don't know if that has anything to do with the problems I'm experiencing, but that's the only thing out of the ordinary that I've done, so...

When I opened Ubuntu later in the day and opened Firefox, first of all it opened over the entire screen, including the panels, which it used to leave uncovered.  Then I noticed that the buttons to close, minimize, etc, that usually appear in the upper right hand corner are gone.  I have to go through the File to close the window.  It's also running a bit slower.  Later I noticed that all the other windows that I open in Ubuntu are also missing the bar with the close, etc buttons, and they open in the upper left hand corner over the upper panel and I can't get them to move by dragging them.  And I can't open the Windows Preferences option under System to try to find out what's going on.

I've also lost the workspace selector from the lower panel.  When I try to add it, I just get a vertical white bar in the panel that I can't do anything with.

If anyone has any ideas, or can talk me through what to do to give them more information or anything, PLEASE help.

---

### Post by floke on 2007-05-25
Just a wild guess, but you haven't installed Beryl or 'desktop effects' by any chance have you?

---

### Post by NeedMoreThyme on 2007-05-25
No, I haven't.  Any istalling was done by the person who set this up for me and it's been the same since I started using it.

---

### Post by floke on 2007-05-26
Can you get to a terminal? If so, type

metacity

in it - this might bring back the window borders

(if this fails, you might have to enter 'sudo metacity' and enter your password when prompted).

Also, it could be a coincidence - your gnome settings might have gotten borked. Enable view hidden files in nautilus and rename all of the following (add a '_backup' or something to them)

.gnome
.gconf
.gconfd
.gnome2
.gnome2_private

This will reset all of your gnome settings; you could also do the same for the .mozilla file, which will reset your firefox settings.

To restore them, if this doesn't work, simply rename them again and remove the _backup bit.

(someone will probably come along with a far far simpler solution, but this is what springs to mind for me anyway)

Hope this helps

---

### Post by NeedMoreThyme on 2007-05-26
Okay, I now have the windows borders back--thank you so much!  What a relief. 
Now, I'm I little cofused about the second bit about renaming the files.  First of all--where do I find them again?  I just don't know where those particular files are located...

---

### Post by NeedMoreThyme on 2007-05-26
Scratch that, I figured it out and it worked wonderfully!  Thanks so much!

---

### Post by floke on 2007-05-26
Glad it's fixed. It's an inelegant solution, but works for me. Gnome can break sometimes; rarely, but it happens. So useful to know how to reset it.

Glad to have been able to help.

Just so you know, Metacity is the window manager for Gnome - the thing that draws the window borders. For some reason it wasn't being switched on at startup, so the terminal entry would have started it manually, So long as your sessions are automatically saved then you 'should' have no further problems. If you do, then you can always add it to your startup options, or start it manually again from the terminal.

---

