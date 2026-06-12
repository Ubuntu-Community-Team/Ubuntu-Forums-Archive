---
title: "Shell frustration"
date: 2006-07-24
forum: General Help
---

### Post by coolclassic on 2006-07-24
I like using the shell and I like using keyboard shortcuts so I find it very frustrating that the shortcuts for copy and paste are so diffrent in the linux shell. The desktop seems to have a standard for these shortcuts such as ctrl-c ctrl-v and this is followed in word processors, text editors and graphic packages, SO why is it not standard in the Linux shell.

---

### Post by mlind on 2006-07-24
> **coolclassic said:**
> I like using the shell and I like using keyboard shortcuts so I find it very frustrating that the shortcuts for copy and paste are so diffrent in the linux shell. The desktop seems to have a standard for these shortcuts such as ctrl-c ctrl-v and this is followed in word processors, text editors and graphic packages, SO why is it not standard in the Linux shell.

because ctrl+c and ctrl-v are reserved :mrgreen: 
It's not that hard to press additional Shift key when doing copy/paste?

---

### Post by coolclassic on 2006-07-24
You need two hands to paste in the linux shell

shift+insert ( I always use the left hand to shift)

ctrl+v one hand

---

### Post by JoWilly on 2006-07-24
The ctrl- keys are shell commands, so you can't use them as shortcuts in the shell.
I.ex: ctrl-c breaks a running process.

---

### Post by mlind on 2006-07-24
> **coolclassic said:**
> You need two hands to paste in the linux shell

shift+insert ( I always use the left hand to shift)

ctrl+v one hand

No you don't. Ctrl+Shift+V. With your pinkie press Ctrl and Shift, with index finger c or v. :confused:

---

### Post by JoWilly on 2006-07-24
> **mlind said:**
> No you don't. Ctrl+Shift+V. With your pinkie press Ctrl and Shift, with index finger c or v. :confused:

And what are you doing with your feet ? :p

---

### Post by coolclassic on 2006-07-24
> **mlind said:**
> No you don't. Ctrl+Shift+V. With your pinkie press Ctrl and Shift, with index finger c or v. :confused:

This does nothing for me!

JoWilly comment has highlighted something I didn't know regarding shell shortcuts. I now go and learn:D

---

### Post by dbott67 on 2006-07-24
> **coolclassic said:**
> You need two hands to paste in the linux shell

shift+insert ( I always use the left hand to shift)

ctrl+v one hand

Which terminal software are you using?  In 'gnome-terminal', it's CTRL-SHIFT-C & CTRL-SHIFT-V.  I've often thought the same thing though --- why isn't it the same convention as every other gui app?

Windows XP command prompt is also not standard. You have to access a menu to 'mark' the selection, then press 'enter' to select it, and finally select EDIT > PASTE to insert it.

Anyhow, I'd be interested in knowing why they can put a rover on Mars, but not have a standard convention in the terminal! :)

-Dave

---

### Post by JoWilly on 2006-07-24
> **dbott67 said:**
> Which terminal software are you using?  In 'gnome-terminal', it's CTRL-SHIFT-C & CTRL-SHIFT-V.  I've often thought the same thing though --- why isn't it the same convention as every other gui app?

Windows XP command prompt is also not standard. You have to access a menu to 'mark' the selection, then press 'enter' to select it, and finally select EDIT > PASTE to insert it.

Anyhow, I'd be interested in knowing why they can put a rover on Mars, but not have a standard convention in the terminal! :)

-Dave

You didn't read my post ?

The ctrl- keys are shell commands, and therefore cannot be used as shortcuts.

---

### Post by mlind on 2006-07-24
> **coolclassic said:**
> This does nothing for me!

At least it works on gnome-terminal. What terminal are you using?
You can also use Ctr-w (cut) and Ctrl-y (yank) if you feel adventurous.

---

### Post by coolclassic on 2006-07-24
> **mlind said:**
> At least it works on gnome-terminal. What terminal are you using?

I use konsole which appears to have diffrent shortcuts.

---

### Post by nix4me on 2006-07-24
Just highlight with mouse and then middle click to paste.

nix4me

---

### Post by dbott67 on 2006-07-24
> **JoWilly said:**
> You didn't read my post ?

The ctrl- keys are shell commands, and therefore cannot be used as shortcuts.

Actually, no.. :)

I got side-tracked when I started to post... there was only 1 reply at the time.  I've got to learn to type faster.  By the time I hit POST, there was 6 new posts! 

There are apps in Windows (i.e. TameDOS.com) that allow CTRL-C & CTRL-V to work in the command prompt.

To be honest, it's not an issue for me, however, I always wondered why.  

EDIT: > Not to beat this dead horse any further, but what is the difference between using CTRL-V & CTRL-CHIFT-V as it relates to being a 'shell command'?  How come CTRL-SHIFT-V is okay, but not CTRL-V?

NEVERMIND! :)

I re-read the thread & read post #4 --- right in plain sight!  Thanks.

Thanks,

-Dave

---

### Post by MarinaraOfDeath on 2006-07-24
Actually, it's not very difficult to remap the shortcuts if you want to maintain the consistency across applications ```
System -> Preferences -> Keyboard Shortcuts
```. In fact, you could easily swap Ctrl+C and Ctrl+Shift+C or Ctrl+V and Ctrl+Shift+V.

JoWilly, since when is it Ctrl+C instead of Ctrl+Z? Seriously...

---

### Post by JoWilly on 2006-07-25
> **MarinaraOfDeath said:**
> 

JoWilly, since when is it Ctrl+C instead of Ctrl+Z? Seriously...

Check your manual again :) 

ctrl-c kills the current process; ctrl-z sends it to the background.

You can list backgounded processes with "jobs" and bring them back with "fg".

---

### Post by mlind on 2006-07-25
> **JoWilly said:**
> Check your manual again :) 

ctrl-c kills the current process; ctrl-z sends it to the background.

You can list backgounded processes with "jobs" and bring them back with "fg".

ctrl-c sends a SIGINT signal, ctrl-z suspends a (foreground) job.

---

### Post by JoWilly on 2006-07-25
> **mlind said:**
> ctrl-c sends a SIGINT signal, ctrl-z suspends a (foreground) job.

Good to see you understand what we are talking about.

But don't mistake suspending a process with stopping it. Ctrl-z will not remove a process from the memory; it will put it in the background and you can call it back to the "foreground" with "fg".

If you just want to stop a process, kill it with ctrl-c.

---

### Post by mlind on 2006-07-25
> **JoWilly said:**
> Good to see you understand what we are talking about.

But don't mistake suspending a process with stopping it. Ctrl-z will not remove a process from the memory; it will put it in the background and you can call it back to the "foreground" with "fg".

If you just want to stop a process, kill it with ctrl-c.

hmm. last time I checked, ctrl-z was still for SIGTSTP signalling which is for suspending a process..

---

### Post by coolclassic on 2006-07-25
There is a printer driver from turboprint that supports your printer. This driver can bypass cups if there is a problem or work with cups.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

This driver provides ink quantity, cleaning, alignment and nozzle checks.

OOPS! Wrong thread

---

### Post by JoWilly on 2006-07-25
> **mlind said:**
> hmm. last time I checked, ctrl-z was still for SIGTSTP signalling which is for suspending a process..

Yes, it's "suspend in the background"

Just try this to see how it goes:

1. Open a terminal and start "gedit".
2. In the terminal do ctrl-z
3. You will see that gedit is moved to the bakground in a suspended state (but still there, in the memory and on your screen).
4. With "jobs" you see it is there.
5. With "fg 1" you call it back.

Yes I know it can be confusing as the shell shows a backgrounded-suspended process as "stopped". But mistakenly "stopping" processes with ctrl-z will only pile them up in the memory. So ctrl-c if you want to really "terminate" (kill) them.

---

