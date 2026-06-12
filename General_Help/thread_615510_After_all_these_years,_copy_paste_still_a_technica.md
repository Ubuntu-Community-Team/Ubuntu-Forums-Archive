---
title: "After all these years, copy paste still a technical hurdle"
date: 2007-11-17
forum: General Help
---

### Post by milliamp on 2007-11-17
I use putty for windows pretty often and when I must use cmd.exe I get by with "quick edit mode"

I like highlight or highlight+enter to copy and simple right click to paste. It is fast when you are working from command line. 

In gnome terminal I see no option to enable a 'quick edit' feature.
When I middle mouse click to past it usually pastes 3 copies.

I can't use control-c control-v either (tried gnome terminal, xfce terminal, Konsole, and linux putty) 

The only way to copy and paste is to right click and select copy, then right click again and select paste.

Sometimes when you copy from one application and close it before pasting to another the clipboard data is lost. 

After billions of dollars of spending, millions of hours and lines of code, basic copy-paste functionality in Linux remains badly broken. What seems to be the problem? How hard can it be?

Now I have to kvm over to the Windows box and ssh to the Linux box with Windows putty in order to get any work done, and that is just f*cking sad.

</rant>

---

### Post by mahousaru on 2007-11-17
ctrl insert to copy
shift insert to paste

---

### Post by bingoUV on 2007-11-17
And I thought it is cmd that is broken. In gnome-terminal, just highlight to copy in the select buffer. Now middle click to paste from this buffer. Doesn't get quicker than this.

---

### Post by milliamp on 2007-11-17
"When I middle mouse click to past it usually pastes 3 copies." 

I am using a 5 button mouse.
(has front/back buttons on side)

Middle mouse click does not work but highlight + 'back button' does what I need.
still not perfect but much better than constantly digging through the right click context menu.

I guess when you consider the separate clipboards it makes sense why they don't just bind right click to do this.

---

### Post by bingoUV on 2007-11-17
Imagine a new user. Seeing right click bringing up context menu in all other ubuntu applications, would he even guess in his wildest dreams that right click could paste from clipboard? Then, gnome-terminal has a functional context menu unlike cmd.exe. How do you propose to open it if right click pastes?

If you still feel this, you could file a bug. If this gains enough traction, you might see some action. 

Middle click not working for you is a bug or a misconfiguration. Have you discussed this here?

---

### Post by CatKiller on 2007-11-17
> **milliamp said:**
> I can't use control-c control-v either

Use Shift-Ctrl-C, Shift-Ctrl-V and Shift-Ctrl-X.

Ctrl-C does something else.

---

### Post by meatpan on 2007-11-17
> **milliamp said:**
> 
After billions of dollars of spending, millions of hours and lines of code, basic copy-paste functionality in Linux remains badly broken. What seems to be the problem?

PEBKAC

Also, linux is not a windows emulator.  You must learn new techniques and keystrokes for accomplishing similar tasks.

---

### Post by daengbo on 2007-11-17
> **milliamp said:**
> I can't use control-c control-v either (tried gnome terminal, xfce terminal, Konsole, and linux putty) 
In Gnome, keyboard shortcuts are always shown next to the menu item, if they exists. Open Gnome terminal and go to the Edit menu. 
Copy is Shift-CTRL-C
Paste is Shift-CTRL-V
This works flawlwssly inside the terminal. If you go to another app, you'll need to check the copy/paste commands there.

You can also use sleect and middle-click, which you rtried. Your mouse pasting three times implies that your mouse is senstitive and is registering three clicks. Check your mouse sensitivity, then try again.

Copy/paste is so good in some desktoops that you can keep ten items in an extended clipboard.

Copy/paste works and works well. Gnome apps even recognize the difference between functions. Paste HTML into the text editor and you can edit it. Paste HTML into Epiphany, and you'll get the rendered HTML.

Linux is not Windows. Don't try to make it so.

---

### Post by atlfalcons866 on 2007-11-17
what about KDE

---

