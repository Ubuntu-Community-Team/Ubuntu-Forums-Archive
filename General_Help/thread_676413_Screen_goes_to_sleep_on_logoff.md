---
title: "Screen goes to sleep on logoff"
date: 2008-01-23
forum: General Help
---

### Post by plantboy1 on 2008-01-23
Well, i have seen many threads on blank screen on logoff, but nobody seems to be having the problem that i am.  I am running ubuntu 7.10 on a Dell Optiplex GX260.  All of the graphics work perfectly fine, i can see the boot screen, and i do not have any problems....until, that is, i log off or switch user.  Once i try to do that, the screen goes to sleep.  I do not know why.  Everything else seems to work though, just the screen stays asleep, and moving the mouse or typing does not do anything.  It does not appear to lock up, as you can still hear all of the system sounds, login screen sound, and all that.  I can even move to a terminal and the screen wakes up, but when i return to gdm, the screen goes to sleep again.  Even stopping and starting gdm does not have any effect, and i need to reboot.  Since it is a shared computer, this is a major inconvenience.  I prefer linux, but if this keeps up, i am gonna use windows more, becuase i dont need to reboot every time i logoff.

---

### Post by NT4usB on 2008-01-23
When the screen is black, can you Ctrl+Alt+F1 and switch to a terminal? Do you see anything on the display in terminal?

---

### Post by plantboy1 on 2008-01-23
Yeah, i can switch to any of the terminals.  If i do that, the monitor wakes up, and it shows whatever happens to be up in the terminal.  I can do anything in there, but as soon as i go back, the monitor sleeps again.  restarting gdm does not change anything.

---

### Post by NT4usB on 2008-01-23
I'm stumped... Just typing out loud the things I'd try to fix it.
Have you looked for clues in Xorg.log?
What video card is in it?

(...completely different black screen issue)
I've found killing gnome-power-mangler and gnome-screensaver as soon as I boot is the only way to get my Mythbox to stay awake. 
If I forget to kill them, and come home to a black screen, killing them at that point **does not** stop the screen from blanking after a while. 
Only restarting and immediately stopping them stops the blank screen. 
It always wakes up soon as I press the remote so that's not an issue.
Just weird that killing them once they've done their thing doesn't stop the blanking...

Long story to get to another suggestion. Reboot, end those two processes and see what happens.

---

### Post by plantboy1 on 2008-01-24
those two processes don't matter, the same thing happens with or without them.  i use fluxbox as my window manager, so they are not enabled by default when i log in.  Same thing happens regardless of whether i am logging out of fluxbox or gnome.  xorg does not tell me anything that could be causing it, as far as i can see.  the graphics card.....i don't remember what it is, it is the integrated one that comes with the GX260.  all i know is that it is made by intel.

---

### Post by plantboy1 on 2008-01-24
I want to add, ive looked around, it seems that a lot of people have some trouble with the GX260.  Maybe all it is is that i need to get a better driver for the graphics card.  right now it is an "intel expiremental modesetting driver"

---

### Post by NT4usB on 2008-01-24
Try the vesa driver.
Grafix will suck but if the problem goes away...

---

### Post by plantboy1 on 2008-01-24
Yes, i do know that the Vesa driver works, but i cannot stand the resolution being set at 800x400 or w/e that is.  BUT: it does not eliminate the prob.  well....it does, but makes a new one.....occurs when logging off or switching users, like the other one.  the screen goes really funky, it doesnt go to sleep.  Instead, it shows a mess of huge, colored pixels all over the screen, i mean....thats all you see, red, green, and a little blue, sometimes some odd characters.

---

### Post by NT4usB on 2008-01-25
Still out of ideas...
Did you see this?
[http://ubuntuforums.org/showthread.php?t=481558](http://ubuntuforums.org/showthread.php?t=481558)

In case you missed some of these in your googlings, lots more reading [here]("http://www.google.com/search?num=50&hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=Dell+Optiplex+GX260+linux+video+black+screen&btnG=Search")
The 8MB thing gets mentioned often...

---

### Post by plantboy1 on 2008-02-03
Alright.  Turns out that I was wrong.  If gnome-screensaver is killed, there is no problem.  I forgot that i had it running in fluxbox as well, b/c i use it to lock my session.  Would it be possible to automatically kill gnome-screensaver when a person logs in?  Not everyone in my family knows to kill it.  And on a side note, is there another way to lock a session, other than gnome's way?

---

### Post by NT4usB on 2008-02-04
I'm sure there's a way to disable it from starting but I don't know what it is. I'll bet a little googling will turn it up though...

ed: ok, how about this?```
$ sudo gconf-editor
```search for screensaver and uncheck startup. I'll let you test it to see if it prevents it from starting...*g*

---

### Post by plantboy1 on 2008-02-19
It's been a little while since i was last online.  Anyway, i have been looking through there and i gotta say, i cannot find the screensaver thing.  It's probably just me, and im overlooking it.... i dont know, ill keep looking :p

---

### Post by NT4usB on 2008-02-20
Well, I tried it and it doesn't work.
If screensaver is enabled, and I kill it, no black screen.
If I disable it, so it never starts... I get a black screen.
How screwed up is that?
So I'm stuck with letting it start when I reboot then killing screensaver to stop the screen from blacking.

---

### Post by plantboy1 on 2008-02-20
I still get a black screen if i kill screensaver.  I figured out what process is messing things up.  it's gnome-power-manager.  The thing is, it starts only when you bring up the shutdown options.  So i can kill it all i want, when i bring that up, it comes back.  If that one process is not running, then there are no problems.  Im not sure how to prevent it from starting though.

---

### Post by NT4usB on 2008-02-20
I've been killing gnome-power-manager all along with screensaver.

Even with killing it I got the black screen after I disabled screensaver from startup. Wait... maybe I brought up shutdown and started it without knowing. (didn't know that happened???)

Anyway, I let them both start, then kill them and no blackness...

No help to you if you log off though. I never do, so it works for me.

---

### Post by plantboy1 on 2008-02-21
Gnome-power-manager does not start with gnome for me, it doesnt show up anywhere.  But it only starts when i bring up shutdown.  So killing it does nothing for me (i have not tried logging out from a terminal, but i do not know the command for that).

---

### Post by plantboy1 on 2008-05-03
Upgrading to Ubuntu 8.04 fixed the problem.

---

