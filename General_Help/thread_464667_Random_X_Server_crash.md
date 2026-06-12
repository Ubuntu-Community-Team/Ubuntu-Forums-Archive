---
title: "Random X Server crash"
date: 2007-06-04
forum: General Help
---

### Post by Zeikcied on 2007-06-04
I had the X server, or at least I assume it was X, crash.  It seems to be random.  I had it happen once before, in Edgy.  And now in Feisty.

I run Kubuntu.  And when the crash happens, the display goes blank.  My monitor goes into power saving mode, as if the video signal stops sending.  And the keyboard stops responding.  I can't enter a TTY terminal to attempt to debug anything.  Ctrl+Alt+Backspace and Ctrl+Alt+Del won't work.  I can't even change Caps Lock or Num Lock, or other keyboard settings.

The only way I can get back to Kubuntu is to shut the computer down manually (by holding the power button until it shuts off).

The only other thing that I can think of is, looking in the syslog, I see this error several times, including right before the "restart" is listed: "APIC error on CPU0: 40(40)"  A Google search for this term doesn't really give me any solid information.  It seems to be caused by a variety of things, and I'm not even sure if it has anything to do with this crash.

Anyway, I have no idea what causes it.  So, I guess that's what I'm looking for.  Why does this happen, and how can I prevent it again?  It's been a couple months since it last happened to me, and it's as annoying now as it was then.

Thanks.

---

### Post by aparigraha on 2007-06-05
My exact problem as well... including the "APIC error on CPU0: 40(40)".
Read through a huge amount of threads but nothing really seems to help. Since it is so random, it's kind of hard to pin it down. I go down sometimes once a week, sometimes 3-4 times a day.

Have you seen these threads?
[http://ubuntuforums.org/showthread.php?t=75281]("http://ubuntuforums.org/showthread.php?t=75281")
[http://ubuntuforums.org/showthread.php?t=412125]("http://ubuntuforums.org/showthread.php?t=412125")

Didn't help me one bit. But it might help you out.

---

### Post by Zeikcied on 2007-06-05
> **aparigraha said:**
> My exact problem as well... including the "APIC error on CPU0: 40(40)".
Read through a huge amount of threads but nothing really seems to help. Since it is so random, it's kind of hard to pin it down. I go down sometimes once a week, sometimes 3-4 times a day.

Have you seen these threads?
[http://ubuntuforums.org/showthread.php?t=75281]("http://ubuntuforums.org/showthread.php?t=75281")
[http://ubuntuforums.org/showthread.php?t=412125]("http://ubuntuforums.org/showthread.php?t=412125")

Didn't help me one bit. But it might help you out.
Those posts seem to be more about mouse cursor freezes.

The crash I'm talking about is the X server completely crashing.  Or, rather, Xorg as a whole.  Keyboard and mouse input, as well as video and sound output, completely cease.  Due to this, I believe, it doesn't recognize my attempts to switch to a TTY terminal, as the keyboard input is no longer registering.

The video output crashes, leaving a blank screen and my monitor going into Power Saving Mode (like what happens when I turn off the computer, or when a power saving setting on the computer kicks in and turns off video output).  As I said, no input or output functions at that point, and I have to shut down my computer with the power button.

It's only happened twice, and it thankfully seems to be a rare occurrence.  I do have an Athlon 64 chip, but I run the 32-bit version of Kubuntu.  But I don't think the problems in those threads are necessarily related.  That is, just by reading the first post, of course.

---

### Post by Zeikcied on 2007-08-07
> **Zeikcied said:**
> Those posts seem to be more about mouse cursor freezes.

The crash I'm talking about is the X server completely crashing.  Or, rather, Xorg as a whole.  Keyboard and mouse input, as well as video and sound output, completely cease.  Due to this, I believe, it doesn't recognize my attempts to switch to a TTY terminal, as the keyboard input is no longer registering.

The video output crashes, leaving a blank screen and my monitor going into Power Saving Mode (like what happens when I turn off the computer, or when a power saving setting on the computer kicks in and turns off video output).  As I said, no input or output functions at that point, and I have to shut down my computer with the power button.

It's only happened twice, and it thankfully seems to be a rare occurrence.  I do have an Athlon 64 chip, but I run the 32-bit version of Kubuntu.  But I don't think the problems in those threads are necessarily related.  That is, just by reading the first post, of course.
It just happened a third time, and now I'm starting to get a little more desperate for an answer as to what is happening, why it's happening, and how to prevent it from happening again.

As I said, all X functions (audio, video, keyboard/mouse input, etc.) cease.  And I'm forced to manually reboot the computer (hold power button until it shuts down).  It still seems to be a rare occurrence, but it's happened three times now, and I just want to know why.

---

### Post by aparigraha on 2007-08-07
Well I've been having the same issue continuosly. Sometimes it's 2-3 times a day, other times I can go for weeks. But I think I've found a solution... maybe.

I've noticed that running Opera and Firefox at the same time has caused the opera/firefox pluginwrapper to crash since both browsers are using it. It has brought down X with it.

I'll get back if it happens again... which it probably will.

---

### Post by Zeikcied on 2007-08-07
> **aparigraha said:**
> Well I've been having the same issue continuosly. Sometimes it's 2-3 times a day, other times I can go for weeks. But I think I've found a solution... maybe.

I've noticed that running Opera and Firefox at the same time has caused the opera/firefox pluginwrapper to crash since both browsers are using it. It has brought down X with it.

I'll get back if it happens again... which it probably will.
I don't have Opera, though.

Anyway...I put the bug up on Launchpad.  But, I don't know what logs to attach to it.  Should I just wait and have someone comment asking for logs, or should I just attach some?  As I said, I don't know which ones to attach :(

---

