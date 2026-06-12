---
title: "Laptop going into suspend mode after 30 seconds"
date: 2018-10-30
forum: General Help
---

### Post by wr1tr on 2018-10-30
Hi,

I have a problem with my freshly installed Lubuntu OS (18.04 32-bit alternative version). I installed it on an old laptop (the process went fine, without any problems), but now whenever I use the new system, it gives me exactly 30 seconds before it goes to suspend mode, no matter what I do.

I thought it had to do with the battery of my computer being pulled out (it's useless anyway), but that was not the case - after putting it back in its place the issue kept happening.

One thing that might be causing it is the inside temperature - the old man's building heat like crazy, however that neither made Windows XP perform a similar action, nor did it do the same with a live-USB booted version of Lubuntu 18.10 (which is the version I was going for with the installation, well, before I got shown the pop-up about it needing 1 GB of RAM) - these systems kept working fine.

Did I somehow manage to corrupt the installation? I remember selecting something like 'lubuntu-minimal' from the 'choose additional packages' window (or whatever it's called). Also, my CPU requires that I use the 'forcepae' flag to run the installation/system from live USB.
 Should I reinstall the Lubuntu OS on the laptop's hard drive? Or maybe install a different distro? If so, what's the best way of removing the currently installed version (and repartitioning the drive)?
Or will simply cleaning the laptop's insides solve the problem?

Computer specs if it matters:
Make: MAXDATA    Model: no idea
CPU: Intel Pentium M 735 @ 1700 MHz  (32-Bit)
GPU: no idea, probably some integrated one
496 MB RAM
60 GB Hard Drive (installed Lubuntu partition size - 20 GB)
Screen resolution: 1024x768

Could any of you please aid a newbie with a malfunctioning computer?
Any help would be much appreciated

---

### Post by wr1tr on 2018-10-31
OK, apparently it's always nice to try the reinstalling strategy. What  solved the problem in my case was to uninstall the OS (by clearing the  partition with Lubuntu using GParted), then remove GRUB (with  Boot-Repair), *then* install the - surprise, surprise - full version of Lubuntu 18.04.

Since I received no feedback here, I've started googling different solutions which worked for other people.

The first one I found suggested making /sys/power/sleep non-writable - I don't exactly remember why, but I chose not to try it.

Next,  somebody said to edit /etc/systemd/logind.conf - specifically, set  "HandleLidSwitch=ignore". That didn't solve the issue (but at least I  taught myself how to change file permissions via console).
Then, they  told me to set "HandleSuspendKey=ignore" in that same file. That didn't  help either, the computer would still go to sleep in regular intervals.

My  next move was to try and boot Windows XP (to see if it still works  after the installation of another OS) from the hard drive. I probably  should've done it a bit earlier, but it seems like I forgot to. You can  imagine my surprise when I saw the raw, unpolished wilderness of a black  screen with a cursor appearing and disappearing rythmically instead of  the Windows logo with a loading bar. It was truly an astonishing sight -  moreover, rebooting the PC yielded the same results every time. I was  on the verge of tears, but tried booting Windows via Plop Boot Manager  (I used it earlier because the laptop didn't want to let me boot from a  USB). Fortunately, it worked and I let WinXP run the auto-initialized  CHKDSK on both shrunk partitions.

In the meantime, some worrying messages "CPU pipe A (&B) FIFO  underrun" started appearing whenever I was booting ANY of the distros  (both on my hard drive and the live USB). Seeing how the systems would  still boot just fine, I decided to ignore it and hope for the best. (I  still don't know what was causing them/how to fix it, so feel free to  enlighten me)

Having solved (well, not really) the previous  issue, I returned to the main one. I saw somebody suggesting that I  should update GRUB with the "acpi=off" boot option. Back then I didn't  know how to do that temporarily (it's done by pressing E in the GRUB  menu, then typing your desired option and hitting Ctrl+X), so I  installed some rescue distro on my multiboot pendrive and ran  Boot-Repair from there, then added the previously mentioned kernel  option and rebooted the machine. This actually solved my problem - the  system finally stopped going into suspend mode and I was able to start  using my new OS. Well, partially. The solution came with a little side  effect - my touchpad was now disabled.

After cursing everyone and  everything in the world, I stopped to look at more solutions - for  instance, using other boot options like "acpi=oldboot", "acpi=ht" or  "acpi.power_nocheck=1". Since the Boot-Repair tool only allowed me to  add more options to the kernel at startup, I began trying to edit the  GRUB file and then run sudo update-grub. That attempt caused the command  line to spew out a very mysterious message: "Failed to get canonical  path of /cow". There were no quick solutions to this problem (or at  least I found none), so I decided to manually edit the GRUB startup  options at boot each time I wanted to try a new option. As for the  options - none of them helped in any way, the problem returned (hey, at  least I could use the touchpad again). Another option which was  suggested but I didn't bother trying was "noapic".

It was at this  moment when I snapped. I ran GParted from the rescue distro, deleted  the partition with Lubuntu OS and removed the remains of GRUB using  Boot-Repair. After that I proceeded to download the full Lubuntu 18.04  32-Bit ISO, set it up on the flash drive, then I booted it on the  laptop. I used some online tutorial to set up different partitions (ext4  twice - system (mounted /) & data (mounted /home); swap once) and  followed through the entire installing process. As mentioned before,  this time I chose the full installation.

When I booted it, I was  prepared to encounter some more sleeping - and I did. The laptop went to  suspend mode during startup. I woke him up and logged onto my account  (while counting from 30), yet when I reached 0 nothing happened. The  system was running stable without problems. Now the computer always goes  into suspend mode (both during startup and after waking up from a  user-initialized suspend mode), but **IT DOES IT ONLY ONCE**. After the boot-suspend-wake_up procedure it's working without an issue.

Well,  I guess I managed to deal with the problem (at least partially) by  myself. I'm posting the entire process - maybe it'll be useful to  someone.
If anyone knows the solution to the suspend-at-startup issue, I'll be more than welcome to see it.

---

