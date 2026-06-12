---
title: "Can't resume from 'Suspend' [8.04]"
date: 2008-05-09
forum: General Help
---

### Post by Straw_Dog on 2008-05-09
I recently installed 8.04.

When I attempt to suspend my computer with Ubuntu the screen goes blank except for a flashing cursor in the top-right corner of my monitor. No keystrokes, mouse gestures, or button presses, etc. will wake it up.

Only a hard reset got me back up and running. I have not yet tried 'Hibernate'. The 'Restart' option works just fine. I've looked around the forums and the rest of the web for an answer but no one seems to have this particular flashing cursor problem.

NOTE: I have Windows [XP] installed on a separate drive and 'Stand-by' works just fine via XP.

I am new to Linux but I'm trying to learn it - being able to leave Ubuntu open but suspended will help me because that way I won't be in Windows as often. Thanks in advance for any help.

---

### Post by ajgreeny on 2008-05-09
It may not help, but try changing to a console tty with Ctrl+Alt+F1, then back to a gui with Ctrl+Alt+F7. I have read somewhere about this helping get back to a proper gui, but I can't promise it will work for you.  Seems this is something to do with graphics drivers not initialising properly when coming out of suspend.

---

### Post by bingoUV on 2008-05-09
Please provide hardware details. Especially wireless/wired LAN card, graphics, motherboard etc. 

Check BIOS settings. Try changing the value of 'Repost video after resume' or something like that.

Check the quirks site : [http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html)

---

### Post by Straw_Dog on 2008-05-09
What sorts of Hardware details?

Mobo is: AsusTek M2N32-SLI Deluxe (LAN and Wireless are built-in)

Video Card: is Geforce 6600 [512mb]

---

### Post by bingoUV on 2008-05-10
Did you check the BIOS settings, or the quirks site?

---

### Post by Straw_Dog on 2008-05-10
(Ctrl+Alt+F1 hasn't worked.)

BIOS:
I looked in my BIOS - couldn't see anything there that looked akin to what you suggested. Under the ACPI heading, currently, my suspend type is set to [S1&S3]. I can change it to just type 1 or type 3; listed as S1(POS) and S3(STR) respectively. There were various 'APM Config' options under the Power heading as well and I changed them to allow for resume with PS/2 mouse and PS2 Keyboard but those have not worked. There were options to resume via PCIe and via modem but those options seemed off base. I also disabled 'graphics card overclocking' just to be on the safe side (I'm not in need of that in any case).

Additionally - there is a sleep button on my Logitech keyboard and it works in-so-far as it will put the computer in suspension while in Ubuntu ... but it doesn't wake it back up.

I've looked at the quirks site and it looks a tad out of my depth but I'm doing this to learn so I will go back and check it out when I have more time.

Additional notes: my Windows clock jumps ahead 5 hours mysteriously after I reset from this hung-up suspend state in Ubuntu. And also, my BIOS' splash page, the one where it detects all the disk drives, takes an awfully long time when I reset during that hung-up state.

I appreciate all the feedback. Thanks for the help guys.
Any other suggestions will be gladly accepted.

---

