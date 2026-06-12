---
title: "How to run TorGuard with root privileges on startup/login?"
date: 2017-05-17
forum: General Help
---

### Post by SpectrumDT on 2017-05-17
Hi! 

I am using the [TorGuard](https://torguard.net/) VPN client. I would like TorGuard to start automatically on login. I have a Bash script that runs on login and starts various things, so I put a command in there to start TorGuard. 

The problem is that TorGuard pops up and asks for my root password. I would like TorGuard to start silently without my having to input root password. What is a nice way to do this?

When I search, most people seem to recommend using **/etc/rc.local**. I have tried to add a line saying "**torguard**" to my **/etc/rc.local**. That had no effect. 

I am running Kubuntu 14.04. 

Can anyone advise me? Thanks in advance! :)

---

### Post by TheFu on 2017-05-17
I don't know anything abuot TorGuard.

GUI programs cannot be run before login, which is why /etc/rc.local doesn't work, if it is a GUI.
Also, inside a script, it is very important to provide the full path to the program and any configuration settings it requires. This is a safety/security thing.  Never trust the PATH.

One option is to allow the exact, specific, program to run without requiring authentication. There are ways to modify the settings in the sudoers file to allow that.  I would be that a how-to on sudo would have that information.  [https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password) was found by google.  Be certain that you limit the command, options to the command and the exact user allowed as much as possible.  It is dangerous to allow anyone to run most commands. There are often options that let a user do much more than expected, which can lead to a complete take-over of the system.

---

### Post by SpectrumDT on 2017-05-18
> **TheFu said:**
> I don't know anything abuot TorGuard.

GUI programs cannot be run before login, which is why /etc/rc.local doesn't work, if it is a GUI.
Also, inside a script, it is very important to provide the full path to the program and any configuration settings it requires. This is a safety/security thing.  Never trust the PATH.

One option is to allow the exact, specific, program to run without requiring authentication. There are ways to modify the settings in the sudoers file to allow that.  I would be that a how-to on sudo would have that information.  [https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password) was found by google.  Be certain that you limit the command, options to the command and the exact user allowed as much as possible.  It is dangerous to allow anyone to run most commands. There are often options that let a user do much more than expected, which can lead to a complete take-over of the system.
You were right. Thanks! 

I had some trouble getting the **sudoers** setup to work, but I found help for that in this thread: [https://ubuntuforums.org/showthread.php?t=2327757](https://ubuntuforums.org/showthread.php?t=2327757)

---

### Post by TheFu on 2017-05-18
That solution is VERY VERY dangerous.  You should only allow the single command you need to work without prompting for a password.  Allowing all commands is EXTREMELY dangerous for a networked Linux system.

---

### Post by SpectrumDT on 2017-05-19
> **TheFu said:**
> That solution is VERY VERY dangerous.  You should only allow the single command you need to work without prompting for a password.  Allowing all commands is EXTREMELY dangerous for a networked Linux system.
I didn't copy the other guy's text verbatim. My **sudoers** contains this: 

```
Defaults        verifypw = any
...
spectrum ALL = (ALL:ALL) NOPASSWD: /usr/bin/torguard
```
Does this look OK? If not, what would you recommend?

---

### Post by TheFu on 2017-05-19
I'm not an expert on sudoers, but that seems pretty open. My best guess is:

```
spectrumdt spectrum-hostname = (root) NOPASSWD: /usr/bin/torguard 
```

and I'd leave the %sudo line alone for all the other management needs on the box where you really need to be prompted for a password.  On my home systems (those that don't move), I have a sudo timeout set longer than the default for a slightly nicer experience. 15 min isn't long enough when I'm bringing up a new server always.

I didn't test my version, so it may not be correct. The sudoers manpage has examples for the specific version of sudo on your machine. Best to use that over webpages, IMHO.

---

### Post by SpectrumDT on 2017-05-20
> **TheFu said:**
> I'm not an expert on sudoers, but that seems pretty open. My best guess is:

```
spectrumdt spectrum-hostname = (root) NOPASSWD: /usr/bin/torguard 
```

and I'd leave the %sudo line alone for all the other management needs on the box where you really need to be prompted for a password.  On my home systems (those that don't move), I have a sudo timeout set longer than the default for a slightly nicer experience. 15 min isn't long enough when I'm bringing up a new server always.

I didn't test my version, so it may not be correct. The sudoers manpage has examples for the specific version of sudo on your machine. Best to use that over webpages, IMHO.
Thanks for the advice. I tightened it to this, which seems to also work:

```
spectrum spectrum-P55-USB3 = (root) NOPASSWD: /usr/bin/torguard
```

---

