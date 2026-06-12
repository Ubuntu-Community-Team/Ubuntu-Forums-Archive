---
title: "Cannot Login - Desktop/xsession Error?"
date: 2017-09-05
forum: General Help
---

### Post by msanchez on 2017-09-05
Ubuntu 16.04 LTS on a Thinkpad W510. After entering creds, user list/login screen re-displays. I can only get to my desktop by dropping into a terminal (CTL + F2) and running ```
startx
```. Makes me think some kind of desktop authn problem. But I have done my due diligence and tried every solution or recommendation found, with caution, for the same issue. All to no avail; re-installed/configured nvidia drivers, fixed PATH var in /etc/environment, reconfigured lightdm, switched to gdm, and more. I'm including some screen shots of some things I think are relevant based on my previous research and attempts. Let me know if you need more.

Aside from the screen shots below, I can also tell you that when I drop into a terminal, it first echos that the commands ls, cat and something else are not found. So I have to run ```
source /etc/environment
``` before I start using the terminal.

[ATTACH=CONFIG]276617[/ATTACH][ATTACH=CONFIG]276618[/ATTACH][ATTACH=CONFIG]276619[/ATTACH]

TIA,

---

### Post by vasa1 on 2017-09-05
We prefer that terminal output is posted as text between code tags rather than as images. Thanks for obliging!

---

### Post by msanchez on 2017-09-05
"As you wish." What other data can I provide?

```
michael@michael-ThinkPad-W510:~$ tail -50 .xsession-errors/usr/sbin/lightdm-session: line 24: mktemp: command not found
/usr/sbin/lightdm-session: line 29: : No such file or directory
/usr/sbin/lightdm-session: line 33: cat: command not found
/usr/sbin/lightdm-session: line 34: truncate: command not found
/usr/sbin/lightdm-session: line 29: : No such file or directory
/usr/sbin/lightdm-session: line 33: cat: command not found
/usr/sbin/lightdm-session: line 34: truncate: command not found
/usr/sbin/lightdm-session: line 106: ls: command not found
/usr/sbin/lightdm-session: line 117: exec: gnome-session: not found
Xsession: X session started for michael at Mon Sep  4 22:16:26 PDT 2017
localuser:michael being added to access control list
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Unable to create /home/michael/.dbus/session-bus
Xsession: X session started for michael at Mon Sep  4 22:38:28 PDT 2017
localuser:michael being added to access control list
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Unable to create /home/michael/.dbus/session-bus
Xsession: X session started for michael at Tue Sep  5 14:12:57 PDT 2017
localuser:michael being added to access control list
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Unable to create /home/michael/.dbus/session-bus
michael@michael-ThinkPad-W510:~$
```

```
michael@michael-ThinkPad-W510:~$ tail -50 .xsession-errors.old /usr/sbin/lightdm-session: line 24: mktemp: command not found
/usr/sbin/lightdm-session: line 29: : No such file or directory
/usr/sbin/lightdm-session: line 33: cat: command not found
/usr/sbin/lightdm-session: line 34: truncate: command not found
/usr/sbin/lightdm-session: line 29: : No such file or directory
/usr/sbin/lightdm-session: line 33: cat: command not found
/usr/sbin/lightdm-session: line 34: truncate: command not found
/usr/sbin/lightdm-session: line 106: ls: command not found
/usr/sbin/lightdm-session: line 117: exec: gnome-session: not found
michael@michael-ThinkPad-W510:~$
```

```
michael@michael-ThinkPad-W510:~$ sudo lshw -C display[sudo] password for michael: 
  *-display               
       description: VGA compatible controller
       product: GT216GLM [Quadro FX 880M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:42 memory:cc000000-ccffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:2000(size=128) memory:cd000000-cd07ffff
michael@michael-ThinkPad-W510:~$ 
```

---

### Post by msanchez on 2017-09-24
The amount of responses has been overwhelming. Thank you. :confused: Since no solution was found I dropped into terminal, ran startx, and then created a startup disk on USB with Ubuntu17.04 and ran an upgrade to fix the OS but preserve my files.

---

