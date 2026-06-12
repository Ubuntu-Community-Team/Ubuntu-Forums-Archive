---
title: "Clear any notifications via a cli command?"
date: 2022-05-04
forum: General Help
---

### Post by goemonburo on 2022-05-04
I am wondering if there's a cli (bash, ideally) way to get the notifications to clear.  I have a script that posts a notification via notify-send that I want to vanish when the program ends.  I can manually close it with the mouse but want to do it (ideally) with a terminal command as part of a bash script.

Thank you!

---

### Post by TheFu on 2022-05-04
You can use xdotool to search the titles of Windows and either activate the one you want and press <enter> or kill the window process.

I don't have an Activate command example, but here's a window move and resize for Firefox.
```
# move Firefox to a specific place and size
xdotool search --name "Mozilla Firefox" windowmove 100 143
xdotool search --name "Mozilla Firefox" windowsize 1612 663
```

That can give you an idea for how to use xdotool.
I don't know if it works with Wayland, but I wouldn't expect that it does.

Ah ... found a script with an activate ...
```
xdotool $FF_WIN_LOCATE $FF_MV_RE_SZ $FF_LOC windowactivate
```
This gives a specific window focus.  The variables are set elsewhere in the script. My desktop systems are setup so that the window focus is under the mouse pointer - no click needed.  This way, it is possible for the active window to be "below" other windows. I find that handy.

And to move the mouse to a specific location and click a button: 
```
CLICK="mousemove 0 0 mousemove 592 318"; xdotool $FF_WIN_LOCATE  $CLICK click 1
```

There are tools that can record all keyboard and mouse actions too, cnee does this.  But notify windows seem to shift each time, so the location for each would need to be moved so the button/<enter> are in the same screen location every time for a little script to handle it.

If it were me, I'd find the window, move it to a specific location, move the mouse and click the "Close/Ok" button.  Mousemove commands are relative, which is why I always move to the upper-left corner first.

---

### Post by goemonburo on 2022-05-05
Thank you, @TheFu I appreciate the help.  Not quite what I was hoping for but it might work. I'm familiar with Xdotool.  So it's a thought.  Ideally I'd like a "send-notify --clear-all" option.  :-D

---

### Post by TheFu on 2022-05-05
If you don't use the notify tool, you could open a tiny terminal with text that has a sleep inside it. When the sleep is up, close the terminal. xterms are perfect for this.

There must be 5 other notification messengers too.  I typically use a different sound for completed stuff, if I care that much.  But for anything more than a few minutes, I'll just submit the task into a batch queue that is easy to manage and check.  99% of the workloads I deal with just need to get done, but I've automated so much that the results get pushed where they need to be without my action.

---

### Post by goemonburo on 2022-05-06
Turns out, @TheFu, this suggestion worked fine.  Thanks for the idea, had been totally thinking in one small-minded way about it but this does the trick, and really wasn't at all hard to set up.  I didn't even have to identify the window, since the notification is in a static part of the screen so I just "xdotool mousemove" to the spot and "click 1"  

Thanks!

---

