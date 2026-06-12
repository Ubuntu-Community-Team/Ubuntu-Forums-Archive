---
title: "dimmed screen when idle"
date: 2023-08-24
forum: General Help
---

### Post by ulrichmuc2 on 2023-08-24
In power managment i have set 
put computer to sleep: when idle for 10 min
put display to sleep: never

In screensaver preferences: Regard computer as idle after 9 min
Activate screensaver when computer is idle

What happens normally: when computer is idle, the screensaver shows pictures, then after a while, the computer goes into suspend mode.
When it is awakend, I see the last screensaver-picture.
So far so good.

However, sometimes, instead of starting the screensaver, the displays (laptop-display and external monitor) are dimmed. The only way I can get out of this state is by rebooting.
This happens after upgarding from 18.4 to 22.04.3.

Any ideas?

---

### Post by wyattwhiteeagle on 2023-08-26
Wow, this trips me up.
but not too bad though.

Your terminology seem's to me like you are trying to make changes to the *buntu from within MS Windows.

You're dual-booting, aren't you? :popcorn:

---

### Post by ulrichmuc2 on 2023-08-28
No, this is a pure Ubuntu (mate) system. I try to keep maximum distance to anything Microsoft-related.

---

### Post by #&amp;thj^% on 2023-08-28
You can try this:
```
sudo apt install dconf-editor
```
Now open it, and  navigate to:

**org.gnome.settings-daemon.plugins.power.sleep-inactive**

There you can change that mode, at least in theory.....LOL
I'll include a screenshot to help

---

### Post by ulrichmuc2 on 2023-10-29
My solution: I programmed one F-key to issue "xrandr --output HDMI-1 --bightness 1.0".
So I don't need to reboot, just hit the F-key.

---

### Post by MAFoElffen on 2023-10-29
My curiosity in the logic of that, if the computer goes to sleep after 10 minutes, how does the display stay active? It would just go off with the system going to hibernation/suspend right?

Hitting your "remapped key" with the macro, there is activity because you pressed a key (your hot-key), so that idle timer resets to that point... and starts over again. So doing that is not really doing what you think it should, it is avoiding it through your manually injected activity/interaction. Pressing the <Escape> key at that point would do the same, without that macro... Because it is no longer idle. You see that right?

Just an observation from working through the logic of that.

Or am I missing something?

---

### Post by #&amp;thj^% on 2023-10-29
> **MAFoElffen said:**
> My curiosity in the logic of that, if the computer goes to sleep after 10 minutes, how does the display stay active? It would just go off with the system going to hibernation/suspend right?

Hitting your "remapped key" with the macro, there is activity because you pressed a key (your hot-key), so that idle timer resets to that point... and starts over again. So doing that is not really doing what you think it should, it is avoiding it through your manually injected activity/interaction. Pressing the <Escape> key at that point would do the same, without that macro... Because it is no longer idle. You see that right?

Just an observation from working through the logic of that.

Or am I missing something?

+1
I wasn't going to say anything the poster seemed content with that....wink wink

---

### Post by ulrichmuc2 on 2023-10-30
The computer is not in suspend mode, but in a state where it reacts to keys and mouse. Just the screen is dimmed in a way that it is barely readable and the mouse pointer hard to see.
Before I found the trick with the remapped key I had to reboot using the power button to get out of this state.
Why the dimmed state is entered is a mystery for me. I happens sometimes when the computer is idle, but not always. Most of the time the screensaver starts and after a while I get suspend mode, as expected, but once in a
while I get into the dimmed mode.

---

### Post by #&amp;thj^% on 2023-10-30
Check your power settings, on both Battery and Plugged in, Look for Dim Screen when Idle.

---

### Post by MAFoElffen on 2023-10-31
Do this
```

gsettings set com.ubuntu.touch.system dim-timeout 0

```
> 
Timeout in seconds for dimming the screen if there is no user activity. A value of 0 disables auto-dimming.


---

### Post by ulrichmuc2 on 2023-10-31
[COLOR=#000000][INDENT]"Dim Screen when Idle" is off for "On AC power". Laptop IS plugged in. Note, that I'm talking about a spurious error.[/INDENT]
[/COLOR]

---

### Post by #&amp;thj^% on 2023-10-31
We are only here to help or try, but your free to run your system how you see fit. ;)

---

