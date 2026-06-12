---
title: "disk thrashing manual shutdown reguired"
date: 2007-03-23
forum: General Help
---

### Post by grimes on 2007-03-23
I installed Ubuntu 6.1 last night,
had everything up and running as i usually do on my pc,
with a talk show streaming through fire fox i listen to while going to bed.

i woke up at 7:00am this morning, and the pc's hard drive was thrashing.
i had to manualy shut it down.

i have a 256 meg of ram and a 128 meg of ram.
256 meg swap space on a 4 gig hard drive.

any ideas what the problem could be?
my guess was a cron job failed or?

any help would be appreciated.

thanks

---

### Post by Muzik83 on 2007-03-23
It could be all of your ram and swap are used up.  It has happened in the past where Xorg crashes on me and starts chewing up ram and swap space.  In the end, the hard drive light is stuck on solid because it is thrashing.

Perhaps install gkrellm, which is a graphical system monitor.  Leave that on the top of your screen, so if it does lock up you can see the time, the processor usage and the ram usage at the time when it locked up.

Was the system at all usable (like hitting num lock would turn the light off...this may take a minute if the above problem is the case).

If so, try to get yourself to a terminal (maybe the ctrl+alt+f1 terminal is easiest, then you're not launching a new gui program.  Type ctrl+alt+f7 to get back to the gui if you try this now), and type 

cat /proc/meminfo

see if all your swap is used.  

-sean

---

### Post by grimes on 2007-03-23
i tried that, i couldn't even get to a terminal.
nothing... i can't belive 384 megs of ram could get gobbled
up just sitting idle.. that's strange. :(

---

### Post by sudo_nym on 2007-04-18
Firefox or its streaming audio plugin (?) might have a memory leak (meaning; it asks for more RAM to load new data, but forgets to *unload* stuff it's not using anymore).  Did you leave it running overnight, with the streaming audio playing?

Or, just a guess (and a more likely leak...), did you have Xscreensaver running?  If so, what were the settings?  Is/was it set to choose a new screensaver at random every [x] minutes or so?

When looking to see which screensavers looked cool -- eg, loading lots of modules in quick succession -- I noticed it loads new modules just fine, but often doesn't *unload* the previous one, and that kind of thing would slowly fill up RAM while sitting idle.  Some of the GL ones can be real resource hogs too, on an older machine (mine, not yours.  By the way, I've only got 160 MB RAM, and as such tend to notice these things more  ;-) )

In fact there are a few leaky apps out there, so it helps to log-out / log-in every so often, and clear the old junk from memory.  Or just reboot.



Good luck with it,

Patrick.

---

### Post by sudo_nym on 2007-04-18
> **Muzik83 said:**
> [...]

If so, try to get yourself to a terminal (maybe the ctrl+alt+f1 terminal is easiest, then you're not launching a new gui program.  Type ctrl+alt+f7 to get back to the gui if you try this now), and type 

cat /proc/meminfo

see if all your swap is used.  

-sean

Yeah, I log-in fairly regularly on tty1 to 6 -- sometimes because the GUI's acting up, but much more often, just because I can.  ;-)

From these consoles, the following can help if your graphical interface is hopelessly fried, but please, USE WITH CAUTION, if at all.  For emergency purposes only.  (And moderators, please remove this post, with my apologies, if it's bad advice.)

Anyway, here's the command;
```
sudo killall Xorg
```

What this does is nuke the X server, and any graphical apps you have running at the time.  Your X session ends, and Xorg should automatically restart itself.  Then you should be returned to the (graphical) login prompt, same one you see at system startup.

If not, you can still ```
sudo reboot 
```from the console.

Well anyway, it's worked for me.  May be harmful in ways I'm not aware of, but seems better that a forced shutdown, especially while the disk is being accessed.



Take care,

Patrick.

---

