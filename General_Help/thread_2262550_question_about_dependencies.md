---
title: "question about dependencies"
date: 2015-01-25
forum: General Help
---

### Post by nep-nori on 2015-01-25
so I'm looking at a specific package's details and among them there's rxvt-unicode as a dependency followed by "or x-terminal-emulator" which is a virtual package provided by, among others, xterm.

How do I specify that I want to install xterm and not rxvt or any other option? do I simply type xterm along with what I'm installing? I suspect that would just install both xterm and rxvt-unicode.

And yes, I'm still very much a noob after 2 years of switching full-time to Ubuntu... what can I say? GUIs are my life.

---

### Post by Holger_Gehrke on 2015-01-25
If any package that provides 'x-terminal-emulator' is installed, the dependency is satisfied and nothing new will be installed for the dependency. So if you do already have some terminal, all is good. If you don't (really ? Is there any way to set up Ubuntu with a GUI without pulling in some terminal emulator along the way ?), you should install the one you want before installing a program that depends on one.

---

### Post by oldos2er on 2015-01-25
You don't need to specify a dependency when running *sudo apt-get install ....* The fact that it's a dependency means the package manager takes care of its installation automatically so you don't have to. And I'm fairly certain xterm is installed by default on all Ubuntu flavors.

If you're unsure, try ```
sudo apt-get install -s foo
``` The -s flag means simulation, so the command will run normally only it won't actually do anything but allow you to see everything that would be installed.

---

### Post by Bashing-om on 2015-01-25
nep-nori; Hi .

How about just asking 'dpkg' what it knows ?
```

sysop@1404mini:~$ dpkg -l xterm
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
[color=green]ii[/color]  xterm          297-1ubuntu1 amd64        X terminal emulator
sysop@1404mini:~$

```
where 'ii' is Desired = installed, and status = installed

amongst all the other tools
[INDENT][INDENT][INDENT]that males 'buntu great
[/INDENT][/INDENT][/INDENT]

---

### Post by nep-nori on 2015-01-25
> **Holger_Gehrke said:**
> If you don't (really ? Is there any way to set up Ubuntu with a GUI without pulling in some terminal emulator along the way ?), you should install the one you want before installing a program that depends on one.

Thanks. Btw to shed some light on your doubts this is a for a hypothetical new DE I might build up from the netboot mini.iso.

Thread marked as solved.

---

