---
title: "How to change the default suspend mode?"
date: 2013-04-14
forum: General Help
---

### Post by snowweb on 2013-04-14
I read [here]("http://askubuntu.com/questions/61708/automatically-sleep-and-wake-up-at-specific-times"), that there are these available modes of suspend:

standby[INDENT]ACPI state S1. This state offers  minimal,  though  real,
                 power savings, while providing a very low-latency transi&#8208;
                 tion back to a working system. This is the default mode.
[/INDENT]

          mem[INDENT]ACPI state S3 (Suspend-to-RAM). This state offers signif&#8208;
                 icant  power  savings  as everything in the system is put
                 into a low-power  state,  except  for  memory,  which  is
                 placed in self-refresh mode to retain its contents.
[/INDENT]

          disk[INDENT]ACPI  state  S4  (Suspend-to-disk). This state offers the
                 greatest power savings, and  can  be  used  even  in  the
                 absence  of  low-level platform support for power manage&#8208;
                 ment. This state operates  similarly  to  Suspend-to-RAM,
                 but  includes  a final step of writing memory contents to
                 disk.
[/INDENT]

I use 'sleep' on my laptop all the time instead of shutting it down, but according to the article I read, when I do this it uses "state S1". How would I change this behaviour so that it uses the "state S3" (above)?

Thanks.

---

### Post by Paqman on 2013-04-15
Have a look in your BIOS.

---

### Post by snowweb on 2013-04-15
> **Paqman said:**
> Have a look in your BIOS.

Thanks Paqman, but my reading up about this leads me to believe that this is a setting which the OS can set at the time it suspends. For example, I can already command the computer to goto 'S4' by telling it to hibernate. Ubuntu then instructs something to goto S4 in the same way that it does when I tell it to sleep, it then goes to 'S1', which must have been commanded by Ubuntu.

I want Ubuntu to command 'S2' instead of 'S1', but don't know where the setting I need to change is stored.

---

### Post by raja.genupula on 2013-04-15
look at file section of this man page link 

[http://manpages.ubuntu.com/manpages/quantal/en/man8/pm-action.8.html](http://manpages.ubuntu.com/manpages/quantal/en/man8/pm-action.8.html)

---

### Post by Paqman on 2013-04-15
> **snowweb said:**
> Thanks Paqman, but my reading up about this leads me to believe that this is a setting which the OS can set at the time it suspends. For example, I can already command the computer to goto 'S4' by telling it to hibernate. Ubuntu then instructs something to goto S4 in the same way that it does when I tell it to sleep, it then goes to 'S1', which must have been commanded by Ubuntu.

I want Ubuntu to command 'S2' instead of 'S1', but don't know where the setting I need to change is stored.

Nevertheless, there also often a setting for this in BIOS. It would be worth checking there first, just in case that is the problem.

---

### Post by snowweb on 2013-04-15
> **raja.genupula said:**
> look at file section of this man page link 

[http://manpages.ubuntu.com/manpages/quantal/en/man8/pm-action.8.html](http://manpages.ubuntu.com/manpages/quantal/en/man8/pm-action.8.html)

Thanks Raja, looks like that has the information I need. Just need to experiment now with the different settings mentioned there, to ascertain what's supported by my hardware.

Thanks again.

---

### Post by Toz on 2013-04-15
@snowweb, the article you reference is in respect to rtcwake - a utility that is used wake the system up after a certain time in suspension. The default system suspend function is different from this utility. 

@Pacman is correct. You can configure how acpi acts against sleep states by configuring them in the bios. From an acpi sleep perspective, it will use the default sleep state as defined in the bios.

To see which acpi sleep modes are supported by your system, run:
```
cat /sys/power/state
```
Then review this code at /usr/lib/pm-utils/pm-functions:
```
if [ -z "$SUSPEND_MODULE" ]; then
	if grep -q mem /sys/power/state; then
		SUSPEND_MODULE="kernel"
		do_suspend() { echo -n "mem" >/sys/power/state; }
	elif [ -c /dev/pmu ] && check_suspend_pmu; then
		SUSPEND_MODULE="kernel"
		do_suspend() { do_suspend_pmu; }
	elif grep -q standby /sys/power/state; then
		SUSPEND_MODULE="kernel"
		do_suspend() { echo -n "standby" >/sys/power/state; }
	fi
fi
```
In a nutshell:
1. *"if grep -q mem /sys/power/state;"* -> if your system supports the mem state, then use it
2. *"elif [ -c /dev/pmu ] && check_suspend_pmu"* -> if your system supports pmu (apple?), then use it
3. *"elif grep -q standby /sys/power/state"* -> else if your system supports standby, then use it.

To see which state is actually being used, you can obtain an extended debug log of the suspend cycle by:
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```
...and on resume, look through the /var/log/pm-suspend.log file for an "echo ??? > /sys/power/state" command (where ??? is one of the supported modes).

As I understand it, when acpi echoes "mem" to /sys/power/state, it will use the sleep state as defined in the bios.

---

