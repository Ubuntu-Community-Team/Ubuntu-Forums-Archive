---
title: "Killing full screen games"
date: 2007-09-28
forum: General Help
---

### Post by Hideaki on 2007-09-28
Is there any way to kill a full screen game that has your mouse and keyboard captured?

I have gnome system monitor mapped to ctrl+alt+del but that doesn't help, since it appears that you can't get keystrokes across to the window manager. I've also tried to do ctrl+alt+f1, but that doesn't work half time either and when it does and i use top then kill to get rid of the game then I switch back with ctrl+alt+f7 I return to a black screen a mouse pointer.

So, is there any way to properly kill a single application or game that has frozen while still in possession of your mouse and keyboard input?

---

### Post by Vadi on 2007-09-28
Alt+tab doesn't work?

---

### Post by brennydoogles on 2007-09-28
> **Hideaki said:**
> Is there any way to kill a full screen game that has your mouse and keyboard captured?

I have gnome system monitor mapped to ctrl+alt+del but that doesn't help, since it appears that you can't get keystrokes across to the window manager. I've also tried to do ctrl+alt+f1, but that doesn't work half time either and when it does and i use top then kill to get rid of the game then I switch back with ctrl+alt+f7 I return to a black screen a mouse pointer.

So, is there any way to properly kill a single application or game that has frozen while still in possession of your mouse and keyboard input?

I have had the same issue. The only solution I have found is that occasionally you can restart X with ctr+alt+backspace , otherwise cut power to the system and restart (which sucks) I would love to find a real fix.

---

### Post by Hideaki on 2007-09-28
> **brennydoogles said:**
> I have had the same issue. The only solution I have found is that occasionally you can restart X with ctr+alt+backspace , otherwise cut power to the system and restart (which sucks) I would love to find a real fix.

That's what I've been doing to. Thing is Ctrl+Alt+Backspace only works half the time as well, sometimes you can't even do that with a frozen full screen game. Other than that I've just been pressing the power button to have the machine shut down tidily

---

### Post by FuturePilot on 2007-09-28
You might be able to kill it from a tty. If Ctrl+Alt+F2 isn't mapped to anything in the game it should drop you into a tty. Just login and use the killall command like so
```
killall game-process-name
```
Then to get back to X press Ctrl+Alt+F7

---

### Post by ryanVickers on 2007-09-28
> **Vadi said:**
> Alt+tab doesn't work?

not for me either - it always did in windows, but for fullscreen *games*, it doesn't seem to! :(  Does anyone know a fix for this!?

---

### Post by Hideaki on 2007-09-28
> **FuturePilot said:**
> You might be able to kill it from a tty. If Ctrl+Alt+F2 isn't mapped to anything in the game it should drop you into a tty. Just login and use the killall command like so
```
killall game-process-name
```
Then to get back to X press Ctrl+Alt+F7


I've tried that before. But for some reason I usually get a black screen with just my mouse showing when I go back to ctrl+alt+f7

---

### Post by FuturePilot on 2007-09-28
Do you have a Nvidia card and are you running Compiz Fusion or Beryl?
That used to happen to me when switching back to X and I found out that by disabling the SyncToVblank option in Compiz fixed it.

---

