---
title: "Wake on lan setup on Ubuntu without &quot;magic packet&quot;"
date: 2013-07-06
forum: General Help
---

### Post by Garen15 on 2013-07-06
Hi Everyone, this forum has provided me with very valuable information as always
but now i am stuck and can't seem to find what i need anywhere

i have a Ubuntu server 12, it's setup as a SAMBA server, it stores data files and images
so far so good, i need the server to sleep when it's not being used
when no users are accessing any files for about an hour, i need it to sleep/suspend to save power

my problem is that all the instructions about wake on lan require the use of the "magic Packet"
i need the server to come back from sleep after a user tries to access a file on the SAMBA server

is that possible? i do that on Windows servers all the time, so i hope i can do the same here

---

### Post by Cheesehead on 2013-07-06
Can the system resume based on *any* network activity instead of a magic packet? Yes, if the BIOS supports that. Look through your BIOS WOL settings.

Another alternative, instead of suspending the entire system, is to spin down your disks using hdparm and a trigger criteria (and/or cron job). First disk I/O will spin them back up. Obviously, you'll want to move most disk-instensive activity like logging and frequently-used files to RAM - spinning down saves a lot of energy and heat...but repeatedly spinning up and down will prematurely wear them out.

---

### Post by Garen15 on 2013-07-06
thank you for your reply, i think the first problem is that it's not going into sleep/suspend mode, i have set the timeout to one hour, but it never does work.
for this system i have downloaded the Ubuntu desktop, just to make things a bit easier to setup
i used the "Power" application to set the "suspend when inactive for" to 1 hour

will there be any reason for it not to sleep?

for now i ran the command [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]"sudo pm-suspend" to force it to suspend and it did not come back on when i tried to RDP in or try to access the SAMBA server[/FONT]

---

### Post by Cheesehead on 2013-07-06
If you suspend it, does it resume if you use a normal way (power button, for example)?
If you suspend it, can you use a magic packet to resume (wake-on-LAN)?

There are lots of possible reasons for a desktop system to not-sleep. For example, a running desktop application has the ability to inhibit suspend. Or your BIOS may not support it. Or the screensaver settings may conflict.

---

### Post by Garen15 on 2013-07-06
suspending and then pressing the power button works
suspending and then sending the magic packet does not work

the machine definitely supports suspend and wake on lan, i have an identical machine running windows server just to test it
and that one goes to sleep and comes back on when accessed.

is there a way to find out what application or process is causing the system not to suspend?

---

### Post by Cheesehead on 2013-07-07
> **Garen15 said:**
> suspending and then pressing the power button works
suspending and then sending the magic packet does not work

From your description, seems like the system is suspending just fine.
Resuming seems like the issue.

Have you been through [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) ?
It's basic, starting with BIOS, then working up through ethtool and NIC settings...but basic and methodical seems appropriate here.

---

### Post by Garen15 on 2013-07-07
yes i had gone through that article before, with no luck

there are two problems, it does not go into sleep mode on it's own (After the timeout of 1 hour)
and it does not come back on with or without the magic packet when i force a suspend.

---

### Post by Cheesehead on 2013-07-08
For suspend, sometimes gnome-screensaver gets triggered instead of gnome-power-manager. If that's the problem, and if you plan to remove ubuntu-desktop after configuration is complete, then it's a self-resolving problem.

For resume, your used ethtool to verify that your NIC really does support WOL?

---

### Post by Garen15 on 2013-07-09
i might actually keep the Gnome interface, i sometimes need it
when i get confident enough running only the text based, then i might get rid of it

is there a way to disable the screen saver and see if that's the cause?

the network card info in ethtools shows
support wake on lan:g
wake-on:g

---

