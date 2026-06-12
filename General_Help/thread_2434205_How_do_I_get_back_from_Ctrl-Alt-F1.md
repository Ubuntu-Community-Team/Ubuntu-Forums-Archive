---
title: "How do I get back from Ctrl-Alt-F1 ?"
date: 2020-01-01
forum: General Help
---

### Post by david503 on 2020-01-01
Ubuntu 18.04.02 (using it as desktop)

If my system freezes or hangs, and I know what's probably killing it (usually chrome, right), how can I kill it and then get back into the gui?

I know I can get Ctrl-Alt-F1 to get to drop out of the gui and I've been a developer for 20 years so I know how to run ps and killall etc.

My question is how do I get back into gui after Ctrl-Alt-F1?  I don't want to start a new session I want the same session just switch me back to the desktop after I killed stuff.

I couldn't find the needle in the haystack when I google- everything I found about Ctrl-Alt-F1 (or f2,f3,f4, for multiple virtual terminals, etc), just told me how to restart the system and/or session after I drop to terminal.  No, I want to stay in the the same session, just switch back to the GUI after I've killed chrome.  

Thanks

d

ps does anyone else have the problem in this form field where you double click a word to select it and when you start typing it does nothing (doesn't start replacing the selected text? This is the only site that does that it's so annoying...

---

### Post by The Cog on 2020-01-01
Alt-F7 normally gets you back to the the GUI (assuming it's working and able to re-draw).

No problem with double-click and type to replace words here (i.e. in this reply). But that's with Firefox on Xubuntu.

---

### Post by guiverc on 2020-01-02
I have found there are times when ctrl+alt+f7 doesn't switch back to desktop, but in most of these occasions ctrl+alt+f8 works (it's as if it restarts using the next... I've not bothered looking at why, nor detected when/why it occurs as it's only rarely occurring..).

Yeah I have issues where I highlight a word (using mouse) on this screen/site, and I cannot type to replace the word, but can press <del> to delete word & type away. Again i didn't explore why, just worked around it.  (FYI: I"m using chromium snap usually)

---

### Post by tea for one on 2020-01-02
In Ubuntu 18.04, there has been an alteration to the access of a tty.

You now have to use **Ctrl Alt F3** up to **Ctrl Alt F6** to reach a tty
**Ctrl Alt F2** or **Alt F2** will return you to the graphical desktop.

Info found here [https://askubuntu.com/questions/1033206/switch-to-console-in-ubuntu-18-04-how-to-leave-gui](https://askubuntu.com/questions/1033206/switch-to-console-in-ubuntu-18-04-how-to-leave-gui)

First answer by Stuart Caie is relevant.

---

### Post by david503 on 2020-01-05
Ok hold  on- I don't mean that I want to drop out of the session; I mean I want to drop to a raw terminal shell.  I was wrong- I thought  ctrl-alt-f1 gets me to a terminal but no, it just gets me back to the session login screen.  How do I get to a raw terminal screen?  No GUI windows; the raw black background white text terminal?

---

### Post by CatKiller on 2020-01-06
> **david503 said:**
> Ok hold  on- I don't mean that I want to drop out of the session; I mean I want to drop to a raw terminal shell.  I was wrong- I thought  ctrl-alt-f1 gets me to a terminal but no, it just gets me back to the session login screen.  How do I get to a raw terminal screen?  No GUI windows; the raw black background white text terminal?

You've already got the answer to that. vt1 to 7 is accessed by Ctrl-Alt-F1 to -F7. It used to be the case that the graphical environment was on 7, then it was the case that it was on 1, and now, apparently, it's on 2 with the login screen on 1. The other vts are text TTYs.

---

### Post by david503 on 2020-01-06
No that's not happening. Right now if I type Crtl-Alt-esc, I get to a (GIU) login to return to shell.  Not a raw terminal.  

I know you're going to say "no but I said Ctl-Alt-f1". 

Ok so If I do Ctrl-Alt-F1. Nothing happens. Nothing.  Or  ok now it's F2? : "Ctrl-Alt-f2" Or  "Ctrl-Alt-f3"Or  "Ctrl-Alt-f4"Or  "Ctrl-Alt-f5" Nothing happens. 

I mean even if I switch to other applications, or just to gnome desktop by itself; nothing happens.

Perhaps I should've phrased the question as "how do I get out of GUI to a raw terminal window and then get back in".

---

### Post by MoebusNet on 2020-01-12
On my machine, Ctl-Alt-F7 still returns me to the GUI desktop after using Ctl-Alt-F(3 through 6 or so) to open a TTY. I'm running Lubuntu 18.04 with current updates. I suppose different Desktop Environments could behave differently now; I haven't used others lately.

---

### Post by Impavidus on 2020-01-12
> **MoebusNet said:**
> On my machine, Ctl-Alt-F7 still returns me to the GUI desktop after using Ctl-Alt-F(3 through 6 or so) to open a TTY.

On my Xubuntu 19.10 laptop too (and ctrl+alt+F{1,2} also give the command line), but that may be because it was release-upgraded all the way from 16.10. Fresh installs may be different.

---

