---
title: "Boot failure, suspect harddisk problem, no KB or mouse"
date: 2023-12-02
forum: General Help
---

### Post by hans12345 on 2023-12-02
Ubuntu LTS

It all started on today's boot which stopped with "SGX disabled by BIOS" and dead KB and mouse

I have seen SGX disabled messages on forums and it seems this may mean a harddisk problem.

Boot attempt 1: looks normal, keyboard flashes and is working, GRUB pops up, all good, then "SGX disabled by BIOS". Now the KB and the mouse are dead.

Boot attempt 2: looks normal, keyboard flashes and is working, GRUB pops up, I navigate with the KB to any other entry, e.g. memory check, then PC dead. Now the KB and the mouse are dead too.

Boot attempt 3: looks normal, keyboard flashes and is working, switch into BIOS (yes I know its not BIOS anymore). Up pops the usual BIOS screen. Now the KB and the mouse are dead so I cannot do anything.

I also tried to boot from a Rufus USB, but the boot sequence never gets to the USB boot.

What can I try?

Help !

---

### Post by Autodave on 2023-12-02
KB and mouse dead in BIOS tells me that it is not a HDD issue.  You should be able to do anything you want in the BIOS without even having an HDD in the machine.  My first thought is a power supply issue.  When the mouse goes dead, flip it over and see if the laser light is still on.  If not, then we have a power supply issue.  Next step would be to disconnect EVERYTHING from the PC except for the mouse.  Turn the machine on and just watch.  Does the mouse's light die?  If not, connect KB (with machine still turned on) and just watch and see what happens.  You don't want to do anything but watch.

Report back.

---

### Post by #&amp;thj^% on 2023-12-02
SGX stands for "intel Software Guard eXtensions and is "a hardware-based isolation and memory encryption mechanism provided by modern Intel® CPUs".
You may get lucky enough by adding this to Grub  "nosgx"
```
sudoedit /etc/default/grub
```
Add to this line:
```
GRUB_CMDLINE_LINUX="nosgx"
```
And yes update-grub after saving the file change.
```
sudo update-grub
```
Reboot.

---

### Post by hans12345 on 2023-12-02
Good thinking !
"When the mouse goes dead, flip it over and see if the laser light is still on. " - Yes it is still on.
The KB Num lock light is still on too. But I cannot do anything to change the KB lights.
"disconnect EVERYTHING " - that is quite a lot. I'll experiment.

---

### Post by oldfred on 2023-12-02
Did you update UEFI firmware, which would reset many settings to defaults?
Many motherboards have settings for "full USB" support or enable USB keyboard & mouse. Check manual as often UEFI descriptions are very brief.
Grub normally requires UEFI for initial use of keyboard & mouse as it does not have its own drivers. Once booted Ubuntu's drivers are used for Ubuntu.

---

### Post by hans12345 on 2023-12-02
No disconnects - mouse lights work as before, even if PC frozen.

I disconnected the LAN and the mouse. In the BIOS the KB worked for a few seconds (arrow keys) then everything stopped. e.g. Num lock stays on even if switched off. Caps lock will not switch on.
I disconnected the loud speaker. In the BIOS the KB worked for a more few seconds then everything stopped.

Any more tests I can do?

---

### Post by hans12345 on 2023-12-02
Hi OldFred - good to see you.

To my knowledge there were no UEFI changes. Indeed no changes at all in the last days.

Any ideas?

---

### Post by hans12345 on 2023-12-02
Thanks for the suggestion.

Following the earlier suggestions it s starting to looks like the power supply.

e.g. even the BIOS (UEFI) is not working.

---

### Post by hans12345 on 2023-12-02
Apologies to all : I should be using 'Reply with quote' 

:o

---

### Post by hans12345 on 2023-12-04
Latest status report

This is clearly a power supply problem but probably not with the PSU.

I opened the case and played around with the power contacts and briefly got the PC to boot.

But now it has failed again.

The situation now:
- power on, KB and mouse good.
- switch to UEFI (BIOS)
- the UEFI is active, I can see the voltages and they are all correct.
- KB and mouse work for about 4-5 secs, then nothing can be done
- the fans keeps working

Does the UEFI start trying to power up the disks? Or does that happen only after you exit from the UEFI?

I imagine that the problem must be with the contacts? Could it be something else?

Any ideas on how to proceed?

---

### Post by MAFoElffen on 2023-12-04
> 
I opened the case and played around with the power contacts and briefly got the PC to boot.

So a bad power connector? On the female connector of motherboard has male terminals inside the socket and the female terminals of the male connector of the PSU... Sounds like either replacing the system board or the PSU. The PSU is female pins, so I would guess replacing the PSU. The system board has the male pins, so harder to go bad? The female terminals side is where the contacts would go bad. Sorry for your lose.

Backtrack, (FYI) the SGX message is a status message, not an error . Says that the SGX setting is not enabled in your BIOS. It can either be enabled and that message will go away, or disabled &  ignore it by 1fallens suggestion. Either way, that does not affect a not booting condition. It only affects the display of that message. But that does not matter when you have bigger issues.

---

### Post by hans12345 on 2023-12-05
> **hans12345 said:**
> latest status report

this is clearly a power supply problem but probably not with the psu.

I opened the case and played around with the power contacts and briefly got the pc to boot.

But now it has failed again.

The situation now:
- power on, kb and mouse good.
- switch to uefi (bios)
- the uefi is active, i can see the voltages and they are all correct.
- kb and mouse work for about 4-5 secs, then nothing can be done
- the fans keeps working

does the uefi start trying to power up the disks? Or does that happen only after you exit from the uefi?

I imagine that the problem must be with the contacts? Could it be something else?

Any ideas on how to proceed?

bump !

---

### Post by hans12345 on 2023-12-05
> **MAFoElffen said:**
> So a bad power connector? On the female connector of motherboard has male terminals inside the socket and the female terminals of the male connector of the PSU... Sounds like either replacing the system board or the PSU. The PSU is female pins, so I would guess replacing the PSU. The system board has the male pins, so harder to go bad? The female terminals side is where the contacts would go bad. Sorry for your lose.

Backtrack, (FYI) the SGX message is a status message, not an error . Says that the SGX setting is not enabled in your BIOS. It can either be enabled and that message will go away, or disabled &  ignore it by 1fallens suggestion. Either way, that does not affect a not booting condition. It only affects the display of that message. But that does not matter when you have bigger issues.

Thanks MAF - I just see your post now.

The PC has worked perfectly for 4 years. No obvious changes.
I suspect a bad connector.
The strange thing is this 4-5 secs period when it works in the BIOS, then all fails.
I'll report again soon.

---

### Post by hans12345 on 2023-12-09
Finally fixed if not completely understood.

After disconnecting the PSU from everything and restarting, it now works again.
I suspect a bad connector - main one from the power supply to the main board.

Thanks to everyone for their posts.

---

### Post by MAFoElffen on 2023-12-09
So, when I went to college for Information Technology, in one of the support courses, a complete cold power reset was:

[LIST]
[*]Turn off via the power button. 
[*]Turn off the power button for the PSU. 
[*]Unplug the graphics cable (so there was no chance of power coming from the Display) 
[*]Unplug the the power cable from the PSU 
[*]With the three prongs that the PSU connects to the power cable exposed, use a quater, and short between each of the contacts in pairs, to discharge the capacitors... 
[*]Connect everything together and turn everything back on. Retest. 
[/LIST]

---

