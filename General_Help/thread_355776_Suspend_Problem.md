---
title: "Suspend Problem"
date: 2007-02-07
forum: General Help
---

### Post by dstein on 2007-02-07
Hello, I am running Ubuntu 6.10. When I click the power button on the top right then click suspend, my machine quickly enters a screensaver, then the monitor powers off for a second, then comes back on, and I am given a password dialog to unlock my machine. Any ideas why it can't enter the suspend mode? I'm not moving my mouse, if that's what you suspect. Also, I am unable to wake up from hibernation. My PC seems to boot alright, but then after trying to re-enter Ubuntu, the monitor powers off and doesn't come back on. Any help would be greatly appreciated. Thanks.

---

### Post by DagMan on 2007-02-07
More help will be to post the make and model of the laptop.

I was able to test the ability of mine to suspend when the scripts to do so weren't working by typing in a terminal ```
sudo pmi action suspend
```
I was able to which gave a better indication of where the problem was for my system.

---

### Post by laklare on 2007-02-13
I tried this on my PC running Ubuntu 6.10 and it died hard when waking up.  Gnome came up, but only with window borders drawn...nothing in them.  I was unable to kill gdm or restart my machine (including by sshing in), so I powered it off and back on.  When it came back up, something had crapped all over my drive and I had lots of manual fsck fixes to make.  Almost lost my entire ubuntu installation, so use caution with this command!  This could have been coincidence and unique to my hardware, but I've never seen this kind of thing happen before.

```
sudo pmi action suspend
```

---

### Post by dstein on 2007-02-14
I tried typing what was suggested from the terminal. My PC still would not sleep. I pasted the message I got. Why am I getting "grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found."? Thanks. I would really like to get this working so that I can make the permanent switch from Windows.

```
$ sudo pmi action suspend
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 6814
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:f2:1e:ca:b5
Sending on   LPF/eth0/00:15:f2:1e:ca:b5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 24.24.2.210 port 67
 * Shutting down ALSA...                                                 [ ok ] 
/etc/acpi/resume.d/15-video-post.sh: line 6:  7071 Segmentation fault      (core dumped) vbetool post
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
ifup: interface eth0 already configured
 * Setting up ALSA...                                                    [ ok ] 
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

```

---

### Post by DagMan on 2007-02-15
It's looking for the fan state but it doesn't turn up always in the same place from computer to computer, those files in /proc are created on the fly and your power management doesn't put them... mine does that too when I suspend from the command line and it isn't anything to worry about in my particular case.

From the looks of it, I think it's finding that the resume script is incomplete or is asking for things that it can not find and that's probably the reason.

If you're using feisty, I'd recommend just being patient, when I tried it out the bugs were squashed and then something else would be fixed and the bugs would be back again.  It's not ready yet.

Try searching through Synaptic for anything that might be helpful to your specific laptop, for example mine is a thinkpad and there's one or two packages that provide tools for thinkpads.  I don't know if that's likely the problem if you aren't using unstable feisty though.  Make a note of what you install though so you aren't left with conflicting packages and there's no need to go wild with things that don't sound like they apply... you will likely know when you see it.

What is the Brand and model of the laptop?

---

### Post by dstein on 2007-02-16
It's actually not a laptop. I like to put my PC into Suspend-to-ram to conserve electricity, considering I don't use it much during the day and prefer not to power down. Also, suspend does not work for even S1 (I believe that's what it's called). Anyhow, if it is searching for stuff that it can't find, any suggestions how I can redirect it where it should be looking? Also, what's "feisty"? Thanks.

---

### Post by wazzup on 2007-02-20
I have the same problem (also a PC)... no solution yet, but if you get it to work, please post it here.

Feisty is the upcomming release of ubuntu (7.04) 
[http://www.google.com/search?complete=1&hl=en&q=ubuntu+feisty](http://www.google.com/search?complete=1&hl=en&q=ubuntu+feisty)

---

