---
title: "annoying! guitar programs don't start, don't work, and don't die"
date: 2008-06-11
forum: General Help
---

### Post by bluepowder7 on 2008-06-11
so i have some old GP4 (guitar pro) files that i was hoping to make use of.

1 - installed DGuitar, but pain to use, no documentation, shows all tabs in one line, now doesn't actually play, and will not close / kill / die / go away.  sometimes loads CPU to 100% and gives me a system load of 6 (!!!)

2 - installed KGuitar, absolutely no sound, changing options and clicking "apply" doesn't do anything, oftentimes just freezes and needs to be killed, etc

so, how am i supposed to kill a program that will not kill?  i've clicked the x, i've killed it, and yet i can still browse the pull-down menus.

is there ANY guitar tab reader / player program out there for ubuntu that just WORKS?  i really don't want to revert to windows just to play some GP4 files...

---

### Post by KaliVoid on 2008-06-12
Hi

did u try [TuxGuitar]("http://www.tuxguitar.com.ar/") ? :guitar: when the house is rocking dont come on knocking

-to Kill a Process
find process ID:
open your terminal and type ```
top
```
when you see the process you want to kill press "Q" to stop the "top" command and look for the "PID" number of the process on the left side.
kill the process:
type in terminal ```
kill "PID"
```

example : to kill rhythmbox
top output
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                
 3914 kali      20   0  204m  38m  15m S  9.9 10.3  15:09.93 rhythmbox

the PID of rhythmbox is 3914 
to kill it ill type "kill 3914"

---

### Post by bluepowder7 on 2008-06-13
tried TuxGuitar - love it!  thanks!  works well, took a few tries to get sound to work (blasted MIDI schmidi), but it's lovely so far!

i also figured out how to kill that DGuitar thing - i had to kill Java so that i could kill DG.  ya see, after trying to quit, close, and kill DG, it was no longer showing in the System Monitor - Processes menu, and was seemingly in stealth mode clinging on to Java.  pain in the butt to kill it, and now i shall never have to use it again.

now to figure out how to remove KGuitar.  it isn't showing up as an installed package in synaptic, so there hopefully is another way of removing it.  and i can't even recall how i installed it in the first place.....

---

