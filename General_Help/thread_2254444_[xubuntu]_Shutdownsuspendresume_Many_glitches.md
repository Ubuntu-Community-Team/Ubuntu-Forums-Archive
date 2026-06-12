---
title: "[xubuntu] Shutdown/suspend/resume: Many glitches"
date: 2014-11-27
forum: General Help
---

### Post by EnglishElectricAndy on 2014-11-27
Affected machine: HP Pavilion g6 Notebook, AMD A8-4500M APU with Radeon graphics
                         Xubuntu 14.04.1 64-bit fresh install 

With Light Locker enabled:
Shutdown -
Expected complete power down of system, actually rotates back to my user login screen.
Suspend -
Expected screen shut-off with machine entering a low power 'standby' mode, actually shuts off screen and isolates the keyboard but machine remains fully powered. It is impossible to resume from this state, the only option being a hard power switch shutdown (which I don't like doing).
```
shutdown -h now

```
also shuts off the screen but leaves the machine fully powered, again in an un-resumable state. This command also requires 'sudo' privileges for some reason.

With Light Locker disabled:
Shutdown -
Expected complete power down of system, actually shuts off the screen but leaves the machine fully powered, again in an un-resumable state.
Suspend -
Expected screen shut-off with machine entering a low power 'standby' mode, actually generates an error - "GDBus.Error:org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

The command posted here [http://ubuntuforums.org/showthread.php?t=2220085](http://ubuntuforums.org/showthread.php?t=2220085) post #7 informs me that I have the latest version of the packages installed.

Searching for a fix or workaround has led me to many threads on several forums as well as Launchpad bug reports, but nothing I've found so far seems to match what I'm experiencing.

Well, there seems to be a fair number of issues surrounding Shutdown/Suspend/Resume affecting many different hardware setups, judging by the number of Launchpad and Bugzilla tabs I've had open.
None of those appear to match what I'm currently experiencing.

What I can establish is that I have three separate packages all having some means of regulating the machine/monitor settings for shutting down or suspending. These are Light Locker, Power Manager and Session & Startup. Somehow the duties of these packages overlap or conflict and I am at a loss to know where to look to resolve these, let alone file a bug with any degree of confidence that I would be reporting correctly.

What confuses me further is that I have an old Sony VAIO with an Intel Pentium T2390 chip and the same configuration of shutdown, suspend/resume settings works perfectly on that machine.

---

### Post by EnglishElectricAndy on 2014-11-28
In connection with this
[http://ubuntuforums.org/showthread.php?t=2254444](http://ubuntuforums.org/showthread.php?t=2254444)

The command caused the machine to power down in what I thought to be in a controlled, safe manner but did not reboot. Pressing the power button generated a normal boot (i.e no error or checking disk messages). After logging in an internal error notification briefly appeared and vanished so i have no idea what actually happened.

Anyone have any thoughts or suggestions?

---

### Post by Gottier on 2014-11-28
This isn't exclusive to Xubuntu. I have similar problems with Ubuntu 14.04. Occassionally I use suspend, then a couple of seconds later the login screen re-appears, but keyboard and mouse are locked. The only option is to do the hard power switch shutdown. At first I thought it was a problem with workspaces, because when workspaces were enabled the problem with happen much more frequently. I asked about this here in the forum with no response. In another forum thread I was reading a forum member suggested logging off before using suspend. I wish there was a way to debug this, but I have no idea what to do.

---

### Post by EnglishElectricAndy on 2014-11-28
[http://ubuntuforums.org/showthread.php?t=1543009&page=39&p=13176529#post13176529](http://ubuntuforums.org/showthread.php?t=1543009&page=39&p=13176529#post13176529)

Looks like it's back to Windows for this machine:(

---

### Post by jeffjohn2 on 2015-01-12
HP Pavilion Notebook running Ubuntu 12.04. ( I switched back to 12.04 as I could not get screen mirroring to TV with Trusty 14).  All works well except power control - no suspend function.  Main problem is at Power-Up.  Power button never loads by itself; however if I press 'esc' when offered, Boot works normally!  Does anyone know how to cure this annoyance, please??

---

