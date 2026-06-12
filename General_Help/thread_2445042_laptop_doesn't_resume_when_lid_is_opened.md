---
title: "laptop doesn't resume when lid is opened"
date: 2020-06-08
forum: General Help
---

### Post by EuclideanCoffee on 2020-06-08
I'm on Ubuntu 20.04 LTS. Typically the desktop should resume after I open my laptop lid, but it reboots.

Any idea on how to stop the rebooting behavior?

---

### Post by ActionParsnip on 2020-06-08
Does the laptop have a make and model?
If you press CTRL + ALT + F1, then press CTRL + ALT +F7 does the GUI come back?

---

### Post by EuclideanCoffee on 2020-06-08
It's a latitude Dell. Computer seems to be responsive only after a short while with the lid closed. I have to press the power button however. My systemd76 doesn't require this or any other Dell latitude I use.

---

### Post by ActionParsnip on 2020-06-08
Did you try what I suggested? Did it work?
What is the output of
```

sudo dmidecode -t 1

```
Thanks

---

### Post by TheFu on 2020-06-08
Any settings in /etc/systemd/logind.conf that seem out of place?

---

### Post by EuclideanCoffee on 2020-06-08
> 
[COLOR=#000000]Did you try what I suggested? Did it work?
[/COLOR]

No.

> 
[COLOR=#000000][INDENT]Any settings in /etc/systemd/logind.conf that seem out of place?[/INDENT]


[/COLOR]


Appears to be the same as my Systemd76, which has the correct behavior.

Not sure where else to check.

```

[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#InhibitorsMax=8192
#SessionsMax=8192

```

---

### Post by TheFu on 2020-06-08
Perhaps one of these settings can help?

```
#HandleLidSwitch=suspend
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
```
There's a manpage for logind.conf which explains what each should do.

```
       HandleLidSwitch=, HandleLidSwitchExternalPower=, HandleLidSwitchDocked=
           Controls how logind shall handle the system power and sleep keys
           and the lid switch to trigger actions such as system power-off or
           suspend. Can be one of "ignore", "poweroff", "reboot", "halt",
           "kexec", "suspend", "hibernate", "hybrid-sleep",
           "suspend-then-hibernate", and "lock". If "ignore", logind will
           never handle these keys. If "lock", all running sessions will be
```
Lots more.  Also, check that the BIOS uses ACPI mode. Think that is needed for any power-related events.
I searched for _acpi lid close events_ .... found some old posts in these forums and wiki.ubuntu.com from last decade, so probably not relevant. Booo.

My 16.04 Asus laptop has always worked with lid events. Don't know what to say.  Previously, all my laptops were on 24/7 and I didn't want them to do anything on lid events.

---

### Post by GhX6GZMB on 2020-06-08
> **EuclideanCoffee said:**
> It's a latitude Dell. Computer seems to be responsive only after a short while with the lid closed. I have to press the power button however. My systemd76 doesn't require this or any other Dell latitude I use.

Perhaps I'm misunderstanding this, but on all laptops I've ever owned I've had to press the "power" button to resume from suspend or hibernate. This is to me the normal behaviour.

If your "system76" laptop wakes up directly by opening the display, it's in my opinion not in suspend mode, but simply has the display turned off.

---

### Post by ajgreeny on 2020-06-08
> **ml9104 said:**
> Perhaps I'm misunderstanding this, but on all laptops I've ever owned I've had to press the "power" button to resume from suspend or hibernate. This is to me the normal behaviour.

If your "system76" laptop wakes up directly by opening the display, it's in my opinion not in suspend mode, but simply has the display turned off.From hibernate, probably, though I've  never used it in Linux.
From suspend it depends on how I put the laptop into suspension.
If I suspend using the Suspend button or it suspends from the power-manager settings, I have to use the power button to resume; opening the lid, if it's been closed after going into suspend does nothing.  If I suspend by closing the lid, and it is most definitely in suspend mode, not just with the screen off, the laptop resumes when the lid is opened.
That has always been the case on my laptops in the past and still is today on two that I still use.

---

### Post by EuclideanCoffee on 2020-06-09
Thanks for all the suggestions. I made some adjustments to the power settings. I turned off automatic suspension and set the button to do nothing when pressed. Perhaps there is a setting being overridden. I'll post back my results.

Another thing, ACPI is off. Thanks for pointing that out. I'll see what happens today and report back. Hopefully I won't need to rebuild the OS.

---

### Post by EuclideanCoffee on 2020-06-09
No fix.

I think TheFu is right. I may need to change the BIOS.

---

