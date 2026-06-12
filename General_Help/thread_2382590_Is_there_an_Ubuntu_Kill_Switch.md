---
title: "Is there an Ubuntu Kill Switch?"
date: 2018-01-15
forum: General Help
---

### Post by heroquestelf on 2018-01-15
Hey guys,

First off, I am running a Dell Experion with a 4x Intel Core i5-4460 3.2 GHz  processor with 8088MB of RAM. My Distribution is Ubuntu MATE 16.04.3  LTS.

What I want to know is: is there an Ubuntu Kill Switch? What I mean by that is a function similar to what you get when you hit Ctrl-Alt-Delete on a Windows machine. Something that will stop all running processes and give you access to your machine again.

Last night, my computer froze up on me because it was trying to load a directory that had a LOT of files in it. The entire computer locked up. I left it and went and got a drink and a half hour later it had not moved. I could move my mouse, but other than that the entire operating system was locked down. Nothing on the GUI was responding. I couldn't even launch a terminal window.

My response, had I been working on a Windows Machine, would have been to pull up the control panel by way of the Ctrl-Alt-Delete, to see if I could shut down some of the processes that were jamming my machine up--**AND**--*in fact*, I did so, hoping that Ubuntu would respond to the Ctrl-Alt-Delete command the same way.

It did not.

I pressed Ctrl-Alt-Delete and there was no response from the machine at all.

After an hour of waiting for the log jam to clear, I wound up doing a hard reboot.

I was wondering what I did wrong, and if there is a way to avoid this in the future. I don't like doing hard reboots. I know it does not do good things for the operating system, but in a situation where the GUI is completely locked up and you cannot get any applications--including the terminal--to pull up, is there any other option?

---

### Post by deadflowr on 2018-01-15
REISUB
as in alt + print(sysrq) + R -E -I -S-U-B
press and hold the alt and print/sysrq buttons and then press the letter buttons listed one key at a time; try to give a second or two between letter key presses.
This will shutdown the system and restart it cleanly.

---

### Post by Impavidus on 2018-01-15
Placement of SysRq on the keyboard is a bit variable, it's usually on PrtSc, but on my laptop it's on Fn+delete. Not all SysRq actions are enabled by default on Ubuntu, but the important ones are.

There also the option of restarting the GUI with ctrl+alt+backspace, but I think that's disabled by default. That will not reboot the computer, but will kill all your applications and log you out. The least invasive course of action is ctrl+alt+F1 (through F6) to get to the console (if that still works), where you can try and find the offending process to kill it, or use the command line to cleanly reboot. Use ctrl+alt+F7 to get back to the gui.

---

### Post by again? on 2018-01-15
> **deadflowr said:**
> REISUB
as in alt + print(sysrq) + R -E -I -S-U-B
press and hold the alt and print/sysrq buttons and then press the letter buttons listed one key at a time; try to give a second or two between letter key presses.
This will shutdown the system and restart it cleanly.
Interesting... I always thought I had to hold down ctrl+alt+ print(sysrq) then type R -E -I -S-U-B. :-k
Thought you had forgotten the ctrl key, but testing here it doesn't seem to matter what other keys are held down with alt.
As long as I hold down the alt key then press and release print(sysrq) followed by R -E -I -S-U-B it works. :-)

---

### Post by mastablasta on 2018-01-16
> **heroquestelf said:**
> 
My response, had I been working on a Windows Machine, would have been to pull up the control panel by way of the Ctrl-Alt-Delete, to see if I could shut down some of the processes that were jamming my machine up--**AND**--*in fact*, I did so, hoping that Ubuntu would respond to the Ctrl-Alt-Delete command the same way.


ti sis only possible if the GUI in windows is not frozen. it doesn't bring up the control panel but system monitor. you can actually set up same combo to do it in ubuntu. but it will not work here as well if the GUI is frozen. 

in case of frozen GUI the best is to first try one of the other virtual consoles as [COLOR=#000000]Impavidus suggests.
If that doesn't work REISUB is the next course of action. 
if that doesn't work as well hard reboot is necessary.

so far i saw two PC's (one of which is from my wife) that do not clear all memory on motherboard (they clean the ram but something stays "occupied" inside the PC) even using hard reboot. so in that case turning it off for 15 seconds helps. in case of my wifes machine, even when i turn it off i can still hear buzzing in the speaker. after about 12 secs without current, that stops as well.[/COLOR]

---

