---
title: "Abnormal reboot issue - Ubuntu 12.04 LTS"
date: 2014-12-27
forum: General Help
---

### Post by delta410 on 2014-12-27
One day recently, my computer didn't shut down properly for some reason. When I attempted to reboot, I got the Debian "rainbow" screen, the one which asks if you want to reboot normally or into another mode (I believe this is properly known as GRUB). I attempted to use the up/down keys to select an option, as the screen instructed, but - no response. I tried a different USB keyboard, I even rebooted the machine with an old-fashioned PS/2 keyboard in place. Nothing, nothing, nothing. No response. I checked the BIOS settings and they were fine. 

The machine was irretrevably stuck at the "rainbow" (GRUB) screen with no way to input any kind of response. (The mouse would not work either).

Having no other options, I inserted a Knoppix live CD into my computer's DVD-ROM drive, used it to move my data onto an external hard drive (glad it wasn't encrypted), and then wiped the computer's hard disk and reinstalled Ubuntu 12.04 LTS from scratch.

How can I keep the above situation from happening to me again? Is there a setting I can use to make the "rainbow" (GRUB) screen time out automatically if it refuses to receive input? For that matter, is there a way around the no-response-to-keyboard issue?

---

### Post by Bashing-om on 2014-12-27
delta410; Hello;

Sounds like grub can not find it's boot files .. Maybe some corruption going on ? Presently can not tell.
The 1st thing to question is IF an update broke the system. -> what results when booting  from grub's advanced options an earlier kernel ?
Many times in such a situation the 'magic" sysreq is appropriate when the system does not boot, and it is desired to reboot the system gracefully:
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)
[http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)

One might also run a file system check in such a situation; Can you then boot to a terminal by the several means to do so ? ( IF yes, looking at a Xserver problem). Several ways to run a fle system check - always with the file system NOT mounted .

Else, looking at grub's files in a corrupted state, in that event (RE-)installing grub might prove to be effective.


[INDENT][INDENT]all in the care and feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by delta410 on 2014-12-28
First, thank you for replying.

> **Bashing-om said:**
> delta410; Hello;

Sounds like grub can not find it's boot files .. Maybe some corruption going on ? Presently can not tell.

That would appear to be the case.

> **Bashing-om said:**
> The 1st thing to question is IF an update broke the system. 

It wouldn't surprise me one bit. I've had programs like GIMP totally go crash city on me after upgrading. (This was GIMP for Windoze)

> **Bashing-om said:**
> -> what results when booting  from grub's advanced options an earlier kernel ?

I think I was able to just use the keyboard to navigate, unlike this latest instance where the keyboard wasn't recognized by Ubuntu at all. (KBD worked fine while machine was booting.)

> **Bashing-om said:**
> Many times in such a situation the 'magic" sysreq is appropriate when the system does not boot, and it is desired to reboot the system gracefully:
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)
[http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)

Even if the system won't respond to keyboard input? If this happens again maybe I will try it, but I'm not optimistic.

> **Bashing-om said:**
> One might also run a file system check in such a situation; Can you then boot to a terminal by the several means to do so ? ( IF yes, looking at a Xserver problem). Several ways to run a fle system check - always with the file system NOT mounted .

Never done that before. How is that done?

> **Bashing-om said:**
> Else, looking at grub's files in a corrupted state, in that event (RE-)installing grub might prove to be effective.[INDENT][INDENT]all in the care and feeding of your 'buntu[/INDENT]
[/INDENT]
[INDENT][INDENT]
How would I do that, especially if all attempts to use the keyboard fail?

Thank you once again.


[/INDENT]
[/INDENT]

---

### Post by grahammechanical on 2014-12-28
I do not think that you were seeing the Grub boot menu at all. If Ubuntu is the only OS on the machine then the Grub boot menu does not appear although Grub is there. With only Ubuntu on the machine Grub will automatically load Ubuntu after about 10 seconds.

I think that you are seeing Fail Safe mode. Did you see this message? "The system is running in low-graphics mode." This happens when Linux has problems loading a video driver. I consider this low-graphics mode to be broken and completely useless. So, I am not surprised that you did not have any success with it. I have tried to test low-graphics mode and I have found it to be useless.

You have solved your problem and want to know what to do if such a situation should arise in the future.

> [COLOR=#333333][FONT=Ubuntu]The user may be able to display the menu in one or more of the following ways:[/FONT][/COLOR]
[LIST]
[*=left]Holding down the SHIFT key early in the boot process until the menu displays.
[LIST]
[*=left]GRUB 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or GRUB 2 cannot determine the status of the key, the menu is displayed.
[/LIST]
[/LIST]


[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

At the Grub boot menu select Recovery Mode. If the boot menu has an Advanced Option for Ubuntu, then select that and then select Recovery Mode. At the Recovery menu select Resume. That will load Ubuntu using an open source video driver. At the desktop you can try changing video drivers and restarting.

You might want to become familiar with Recovery Mode and see what it has to offer. Note the answer to this question and note point 4

[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

> [COLOR=#333333][FONT=UbuntuRegular]In some cases failsafeX will load fine (You lucky dog), for others (Me) it will give an error along the lines of "The system is running in low-graphics mode" and will stay there forever. [/FONT][/COLOR]

Like i said: "Broken." I would suggest trying Resume first. 

Regards.

---

