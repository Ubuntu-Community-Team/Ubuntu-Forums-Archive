---
title: "xkill not running, application hanging computer"
date: 2008-07-03
forum: General Help
---

### Post by sgleason on 2008-07-03
I'm writing a C program using Code::Blocks and very often I manage to crash the entire system.  It only happens when I use the debugger.

The problem is I can't find the bug in my program if the whole of Ubuntu crashes every other time I debug in Code::Blocks.

xkill will not run, either using alt-F2 or from the panel. I need to power the machine off every time and its only a matter of time before it does not wake up again.

I can reach the console using ctrl + alt + F1 (I think) but don't know how to shut down Code::Blocks from there (or return to normal if I manage to kill it). How can I list the programs running from the console and kill one?

Or if someone has a better idea, I'm open to it. I need a big hammer to knock out Code::Blocks when it flys into neverland basically ...

Thanks,
Scott

---

### Post by Gunman1982 on 2008-07-03
If you can get to the console with ctrl+alt+F1 than you can login, and kill the process with 'killall program_name' to find out which programs you have running you can use 'ps aux'. If the program still runs even after you do a 'killall program' you can try 'killall -9 program' that will have some more momentum but shouldn't be used without reason because it doesn't leave the program time to tidy things up.

Oh and you can go back to your graphical session with ctrl+alt+F7

---

