---
title: "Problems Re-Installing Ubuntu"
date: 2008-01-23
forum: General Help
---

### Post by bluesrocker on 2008-01-23
Hi. I had my computer working fine with Ubuntu 7.10, but since I need to prepare for an A+ test, decided to create a partition with Windows XP. After the partition was made, it the XP never allowed me access Ubuntu. I formated the disk, and now when I try to install Ubuntu on that disk or another hard disk; it starts reading the disk (it gives me the option of installing cd, start from disk, etc.) Once it begins to read the disk, it simply says " Sync out of range". I know it was a mistake to re-install Windows, but I would like to re-install Ubuntu and forget about Windows. Is there anything I can do to have Ubuntu on my pc again? Please advice. Thank you

:guitar:

---

### Post by Metaljaz on 2008-01-23
If you are using a live CD you should just boot from the CD. Then you will get an option to install and when you get to the screen for partitioning your HD you can chose to use the entire disk. It should erase everything and install.

If you have tried the install with the same disk but different hard disk and you get the same error message you may have to try a different CD to install from. Download the ISO and then burn it to disk.

---

### Post by bluesrocker on 2008-01-24
Thanks Metaljaz. I searched google, and I found the problem. It's my monitor, for some reason it is the resolution of the OS. I am a bit confused, because I had installed Ubuntu before with that computer. here is the information I found.



[http://www.smartcomputing.com/techsupport/detail.aspx?guid=&ErrorID=33737](http://www.smartcomputing.com/techsupport/detail.aspx?guid=&ErrorID=33737)
Error Message:
"Sync out of range."
Translation:
When switching from small fonts to large ones, a reader was informed that the operation was not possible and was asked to reboot the computer. Doing so generated an error message, however, and the only way to get back into Windows was through Safe Mode until the display settings were all reset to their original values.
Solution:
Error messages that arise from tweaking display settings are among the trickiest to resolve because many throw the monitor out of whack and make it impossible to see what you're doing. In most cases Safe Mode is the answer; it loads video drivers that are known to be compatible with Windows, so you can make changes.

The "Sync out of range" message the reader received was referring to the monitor's synchronization rate or refresh rate, which is the number of times a monitor redraws the on-screen image every second. Every monitor has a range of refresh rates it can handle at a given resolution. For example, a monitor can typically handle high refresh rates of 85Hz to 100Hz (1Hz equals one redraw per second) at a relatively low resolution of 640 x 480 pixels (picture elements) but may only be able to deliver refresh rates of 60Hz at a higher resolution of 1,600 x 1,200. If a program or utility calls for refresh rates that are higher or lower than the refresh rate range the monitor can handle, it won't display anything but an error message.

The reader was concerned about long-term damage to the monitor, but that won't happen. The error message is designed to prevent bad things from happening to your monitor rather than popping up to let you know the damage has been done. The message was saying, "You've requested something that is outside the operating parameters of this particular monitor, and we're not going to deliver."

Adjusting refresh rates and resolution is easy if you ever need to do so in Safe Mode. Right-click the Desktop and then click Properties and the Settings tab. You can adjust the resolution using the screen resolution slider. To manage refresh rates, click the Advanced button and the Adapter tab and use the drop-down list to select from the available refresh rates. Always try to go with 76Hz or higher to reduce eyestrain because the monitor appears to flicker at lower rates. If you're using WinXP, click the List All Modes button to see the available refresh rates at each resolution.




Thanks anyways!!!

:guitar:

---

