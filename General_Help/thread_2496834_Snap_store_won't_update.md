---
title: "Snap store won't update"
date: 2024-04-14
forum: General Help
---

### Post by cbiweb on 2024-04-14
Running Ubuntu 22.04, fully updated (except Snap Store of course)

Why won't Snap Store update?
I tried some terminal commands.
Tried clicking Quit in Ubuntu Software.

Rebooted, but no change.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293616&stc=1[/IMG]

---

### Post by hyperlinxe on 2024-04-14
The error message explains why it cannot update, because a related component is running simultaneously.

"...cannot refresh snap-store: snap snap-store has running apps (ubuntu software)"

It's confusing because of the language they use, so it repeats snap, snap, snap over and over, which makes it difficult for people to understand what the operating system is actually doing.

It even gives u the pid so you could use 

sudo kill -p 2618 && sudo snap refresh

to update

edit: ok so you tried closing it, and you still get the same error message? It must be open elsewhere if that is the case, check your taskbar.

Also try to slowly, read the error messages, and comprehend what they are communicating to you. They might not be the only thing important, but they should provide you with useful information.

edit#2: also if your software store is open, or whatever.. the software app, try updating snap from there

---

### Post by cbiweb on 2024-04-14
> **hyperlinxe said:**
> 

edit: ok so you tried closing it, and you still get the same error message? It must be open elsewhere if that is the case, check your taskbar.

How can anything else at all be running after a reboot?

---

### Post by hyperlinxe on 2024-04-14
It's probably automatic, if you have automatic updates on. I don't work with the default system that is shipped out to people, so I don't have to deal with most of the bugs that ... literally most people have to deal with.

If I wanted to help people use default Ubuntu I would learn about these specific kinds of bugs through using default ubuntu, but I don't play games like that right now personally. I customize the system as much as possible, to avoid these kinds of default problems.

It sounds like you have a process that is misbehaving, that is the description of a typical software bug.

Try a simplified google search of your exact problem.

(also I don't play games with snap either, I usually end up removing it after discovering how badly it's apps perform)

---

### Post by QIII on 2024-04-14
Do you have information demonstrating the ratio of the number of those who have problems to the number of those who don't?

---

### Post by cbiweb on 2024-04-14
I ended up doing this:
[FONT=courier new]
sudo killall snap-store
sudo snap refresh snap-store[/FONT]

And it worked.

---

### Post by Holger_Gehrke on 2024-04-15
And to explain why the 'killall' is necessary: snap-store can't update itself while it's running. To make matters worse, snap-store is a re-skin of gnome-software, a program that doesn't shut down when its window is closed (that's intentional behaviour; the idea is to make it faster to start up when run again after closing its window). So even after closing the snap-store window you still have to stop the still running snap-store before you can update it.

Holger

---

### Post by karyk on 2024-09-02
Thank you, those two terminal commands worked for me, but . . ..

App Store was no longer pinned to to my Dash for some reason, which made me think is wasn't running.  I think all I had to do was re-open and re-pin it, but I did a reboot first instead, so I don't know if that's a necessary step.  And I don't care enough to repeat the process to find out.

Also, the App Store is new, and the Updates area is no longer a tab at the top, but instead under "Manage Installed Snaps" at the left, which in my system only says "Manag . . ." so that was not immediately apparent.  I prefer the old layout.

---

### Post by jbl85 on 2024-09-03
This worked for me as well.  Thank you!

---

### Post by jbl85 on 2024-09-03
> **cbiweb said:**
> I ended up doing this:
[FONT=courier new]
sudo killall snap-store
sudo snap refresh snap-store[/FONT]

And it worked.

This worked for me too.  Thank you!

---

### Post by karyk on 2024-09-03
> **Holger_Gehrke said:**
> And to explain why the 'killall' is necessary: snap-store can't update itself while it's running. To make matters worse, snap-store is a re-skin of gnome-software, a program that doesn't shut down when its window is closed (that's intentional behaviour; the idea is to make it faster to start up when run again after closing its window). So even after closing the snap-store window you still have to stop the still running snap-store before you can update it.

Holger

Just a guess, but I suspect it stays open so that it can continue to look for updates.

---

### Post by deadflowr on 2024-09-03
> **karyk said:**
> Just a guess, but I suspect it stays open so that it can continue to look for updates.

Partially.
But really because it takes a long time to load the database so startup time is long.
So they set it to always be running in the background.
Otherwise it can take minutes to open and fully load instead of seconds.

---

