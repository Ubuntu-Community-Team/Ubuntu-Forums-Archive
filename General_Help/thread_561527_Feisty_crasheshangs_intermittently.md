---
title: "Feisty crashes/hangs intermittently"
date: 2007-09-27
forum: General Help
---

### Post by jeph36 on 2007-09-27
I have a fairly new fresh install of Feisty on a Compaq F572US laptop.  Occasionally the computer will simply freeze with no mouse, keyboard, or other response.  The fan will periodically spin up and down as it normally does, but the computer otherwise shows no signs of life.  The screen will remain frozen at whatever it was last showing (even a blank screen if the screen had turned off).  This can happen a few times a day or every few days.  Usually the only thing open is FireFox and occasionally a terminal window.  I am using the Wifi with wifi-radar, but I usually close the program after I get my connection.

I checked the /var/log/messages file, but it showed nothing useful (to me).  At the point of the crash it was just giving a "MARK" heartbeat.  Can anyone help me out to get this system a little more stable?  I am not a power Linux user by any means, but I am fairly proficient at digging through these kinds of things with some guidance.

Thanks.

---

### Post by mootpoint on 2007-10-02
I've experienced the same thing. Maybe we can cooperate in isolating the problem.

What BIOS version is on your machine, what kernel are you running, and what options are on the boot line in /boot/grub/menu.lst? I'll post mine when I'm @ home tonight.

m00t

---

### Post by p_quarles on 2007-10-02
One thing you (both) might try is looking at a few additional log files. I'm thinking specifically /var/log/acpid (in case it's heat- or power-related), as well as /var/log/syslog and /var/log/kern.log.

I could be wrong (<--understatement), but it strikes me as possible that an error could be recorded in one of these logs, and then the system crash takes place before it gets a chance to write to the messages log.

---

### Post by jeph36 on 2007-10-07
OK, I am finally getting around to replying.

My BIOS version is F.18.
My boot options line is:
[FONT="System"][COLOR="Blue"]kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=50efd280-6d58-441c-b8bc-783a6a6e8ea1 ro quiet splash [/COLOR][/FONT]
which indicates I am using 2.6.20-16 kernel (is there a better way to check?).

Here is a snippet from my /var/log/messages file which shows nothing useful at the time of the hang:
[FONT="System"][COLOR="Blue"]Oct  6 23:56:56 Compaq-Laptop -- MARK --
Oct  7 00:16:56 Compaq-Laptop -- MARK --
Oct  7 00:36:57 Compaq-Laptop -- MARK --
Oct  7 07:15:02 Compaq-Laptop syslogd 1.4.1#20ubuntu4: restart.[/COLOR][/FONT]

All I have in /var/log/acpid is:
[FONT="System"][COLOR="Blue"][Sun Oct  7 07:24:57 2007] logfile reopened[/COLOR][/FONT]

My /var/log/syslog starts at 7:25 ... after the crash occurred.  I had checked it previously in the week after a crash and it had both pre- and post-crash info so I will try again after another crash.

Nothing stands out to me in the /var/log/kern.log.  I do see:
[FONT="System"][COLOR="Blue"]PCI: BIOS BUG #81[49435000] found[/COLOR][/FONT]
which is something I always get when I boot.  Do other F572US users get that?

And one final note to add that probably is irrelevant to this topic ... after booting into Gnome, if I open a terminal window within ~2 minutes of starting, the following will show up in the window:
[FONT="System"][COLOR="Blue"]Message from syslogd@Compaq-Laptop at Sun Oct  7 07:17:18 2007 ...
Compaq-Laptop kernel: [  233.296000] Disabling IRQ #7[/COLOR][/FONT]
I have not tried to determine what that means or if it matters.

Thanks.

---

