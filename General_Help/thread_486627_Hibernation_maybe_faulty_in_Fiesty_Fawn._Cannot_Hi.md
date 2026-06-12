---
title: "Hibernation maybe faulty in Fiesty Fawn. Cannot Hibernate on Desktop system."
date: 2007-06-28
forum: General Help
---

### Post by Snakes on a Plane on 2007-06-28
Cheers everyone,

I have this nagging issue in Fiesty Fawn. The system will not hibernate, eventhough i click on hibernate. Some random texts appear on screen and the system shuts down. But the next time i start the system it just does a cold boot. 

My system is a very old Pentium III
RAM is 512 MB
Swap is double of ram, 1GB
Dual boot Windows XP on the first partition and then Ubuntu Fiesty Fawn

I have no trouble hibernating in Windows XP though.

I even did not have any problems like this in Ubuntu Edgy Eft, but the only difference was when Edgy was installed it was the sole OS and the swap file size was 512 MB.

So i tried to hibernate using the terminal, it showed an error that Hibernate Package was not installed. So i installed it via apt. Still no success. The same cold start thing happened from the GUI. I get this error when i run this command from the terminal.....

```
sudo hibernate
```

After i type in the command the monitor blanks out and then comes back after a few seconds and gives me this error.

```
/bin/echo: write error: Operation not permitted
```

I don't want to open all the programmes every time i start my system, so this hibernation is very necessary.

HELP.

:popcorn:

---

### Post by Victoriakhf on 2007-06-28
Hi,

Sorry can't help, but just thought I ought to say I'm having similar problems - every time I try to hibernate it does strings of numbers (something like [345.3875984]) and mutters about USB still 2 or similar.

So, would be intersted in any suggestions too

---

### Post by Snakes on a Plane on 2007-06-28
> **Victoriakhf said:**
> 
Sorry can't help, but just thought I ought to say I'm having similar problems - every time I try to hibernate it does strings of numbers (something like [345.3875984]) and mutters about USB still 2 or similar.

Cheers Victoriakhf, for me it is something like this, 

I clicked on Hibernate option from GUI and, the same thing that i mentioned above happened. Here are some things i got from the System Log Viewer.

**debug**
```
[ 415.248645 ] PM: suspend-to-disk set to 'shutdown'
```

**kern.log **
```
[ 415.248645 ] ACPI: PCI interrupt for device 0000:01:09.0 disabled
[ 415.248645 ] PM: suspend-to-disk set to 'shutdown'
```

**messages**
```
gnome-power-manager: (U/N) Hibernating computer because the DBUS method Hibernate() was invoked

[ 415.248645 ] ACPI: PCI interrupt for device 0000:01:09.0 disabled
```

**syslog**
```
gnome-power-manager: (U/N) Hibernating computer because the DBUS method Hibernate() was invoked

[ 415.248645 ] ACPI: PCI interrupt for device 0000:01:09.0 disabled

[ 415.248645 ] PM: suspend-to-disk set to 'shutdown'
```

**user.log**
```
gnome-power-manager: (U/N) Hibernating computer because the DBUS method Hibernate() was invoked
```

So can anyone make any sense of this. 

By the way in gnome power management i have chosen never for both options, put computer to sleep if inactive and put display to sleep when inactive for. Also this is a fresh install of Ubuntu Fiesty Fawn.

:popcorn:

---

### Post by Snakes on a Plane on 2007-06-29
Anyone please HELP.

I have been desperately been trying to find a solution for this problem. 

I have applied all the updates for Fiesty using the update manager and still no positive results.

I searched the Synaptic Package Manager and found uswsusp and suspend2. Now i don't want to install anything that may cause harm to the system, besides i have installed the Hibernate package and it did not do anything. So can anyone who has these two other packages installed confirm that they actually work or not?

Come on, there must be someone, at least one expert out there who can help me with this issue.

---

### Post by nick_h on 2007-06-29
Is it just hibernate you are having problems with?  Does suspend to memory work?

---

### Post by Snakes on a Plane on 2007-06-30
Yep, it is only the Hibernate thing that i am having problems with in Fiesty. :(

And aside from the normal six options when i click on the shutdown button, i dont have an option for Suspend to memory. :(

---

### Post by nick_h on 2007-06-30
I've got problems with both suspend and hibernate in Feisty.

There is a configuration file, /etc/default/acpi-support, which is worth looking at.  From the command line you can run the hibernate script with:
```
sudo sh /etc/acpi/hibernate.sh
```
The hibernate.sh script runs the scripts in /etc/acpi/suspend.d before hibernating and the ones in /etc/acpi/resume.d when resuming.  I am going to take a closer look at these.

There also seem to be quite a few other threads relating to Feisty suspend/hibernate problems and bugs reported in launchpad.  I think it's time for some further reading. :)

---

### Post by Snakes on a Plane on 2007-07-01
/etc/default/acpi-support, I looked at this file, everything is enabled, none are commented out. 

_Update._

Clicking on hibernate did a shutdown and a cold start, that was before i installed **Suspend2-userui** and  **uswsusp** .Now clicking on hibernate, the screen blanks out for a while and i get an unlock screen prompt. Ran this command in the terminal............i got,

```
sudo sh /etc/acpi/hibernate.sh
```

```
 * Shutting down ALSA...                                                 [ OK ] 
Usage: suspend [-f config][resume_device]
Laptop mode disabled, not active.
/etc/acpi/resume.d/17-video-restore.sh: 11: cannot open /var/lib/acpi-support/vbestate: No such file
Function not supported
ifup: interface eth0 already configured
 * Setting up ALSA...                                                    [ OK ] 
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

```

Crap. Going back to Edgy. Fiesty is good but not without the hibernate function. Hope hibernate works on Gusty.

---

### Post by Di@blo on 2007-07-03
Yeah, I really think this thread should be stickied, because I have the same problem. By desktop, you mean the desktop build, right, because I have the same problem on my Toshiba Satellite Pro 4600.

---

