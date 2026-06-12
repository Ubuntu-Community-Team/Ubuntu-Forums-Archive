---
title: "Having trouble shutting down"
date: 2007-04-08
forum: General Help
---

### Post by Vurius on 2007-04-08
Hello all!  I've been using Ubuntu for a while now to the point where I am generally comfortable with it, and so I decided to install it on a nice rackmount machine I had lying around, so I could use it as a webserver.  Anyways, the machine works perfectly fine except for one thing: it will not shut down.

This is (well, eventually will be) a headless server, so I have a text-only install of Edgy without any fancy GUI or X or any of that nonsense.  Over SSH, when I told the computer to "shutdown now", "shutdown -p now", "shutdown -h now", "shutdown -hP now", "poweroff", or "halt", it would close my connection, do a little bit of activity, and then just sit there, powered on.

I was growing frustrated of this, so I plugged a monitor and keyboard into the machine and then tried to make it shut down.  The computer runs the shutdown scripts, stopping the webserver, sql server, the raid array, etc, and then gives the message "Will now halt".  After a brief moment, the computer prints: "System halted."  After this point, the computer remains powered on, but does not respond to any input.

My machine has dual Pentium III Coppermine @ 1.0 GHz processors in a Tyan Tiger LE mainboard.  As of now, I am running Edgy with the 2.6.17-11-generic (#2 smp) kernel.  Before making this thread, I checked out a few other threads for advice.  I checked the BIOS and made sure advanced power management was enabled.  I also tried editting my Grub menu.lst and removing "quiet splash" from the kernel line, as well as adding combinations of "noacpi acpi=off apm=on".  None of these seem to do anything, and the system will simply hang as described before.

I would write the whole thing off, but the funny thing is that "shutdown -r now", or anything related to restarting or rebooting the machine actually works.  As a server, having the option of rebooting will actually be more important to me than the ability to shut down or start up the machine remotely, at least once I get the machine running.  However, I would really like to have the ability to actually shut down the computer without physically flipping a switch if at all possible.

On a related matter, I'm fairly certain that the machine doesn't have ACPI support.  Besides ACPI not being listed in the BIOS, /proc/cpuinfo doesn't list acpi as supported module, and acpitool lists that acpi is not supported.

I'd really love to be able to shut my computer down in software without having to rely on physical shutdown if at all possible, so any help or insight would be greatly appreciated.  Thanks!

---

### Post by mac.ryan on 2007-04-09
Does this helps in any way?
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

---

### Post by Kuoi on 2007-04-30
Or this ... [Poweroff solution ?]("http://ubuntuforums.org/showthread.php?t=428363")

Kuoi

---

### Post by ivze on 2007-07-27
I have an old computer.
PII - 350MHz(manufactured in 1998).

I tried using "ubuntu-7.04-server", with similar results - the shutdown -h now did not work properly, the system could not send a command to switch power off after stoppig.
The problem, however, has been solved by:
1.adding "acpi=off apm=power_off" in the end of kernel line
After that the line looked like 
kernel ....... ro quiet acpi=off apm=power_off
2. adding a line 
apm power_off=1 
in the end of /etc/modules .
3. Switching apm on via BIOS (for some reason it was shut down).

Now i have the ability of switching the computer off without a help of the power button, what is especially significant for a stand-alone server.

I wish you have the same result.
************************************************************************************
ZelinskiyIS

---

