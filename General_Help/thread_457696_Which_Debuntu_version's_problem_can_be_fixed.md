---
title: "Which Debuntu version's problem can be fixed?"
date: 2007-05-28
forum: General Help
---

### Post by SubGothius on 2007-05-28
I have (more-or-less) successfully installed in succession (doing a nuke'n'pave between each install to cleanse my palate, of course ;) ) each of the following Debian and Ubuntu versions:[list][*]Debian 3.1 Sarge;
[*](X)Ubuntu 6.10 Edgy;
[*](X)Ubuntu 7.04 Feisty;
[*]Debian 4.0r0 Etch.[/list]However, each of these has its own, unique problem that, for me, renders the system unacceptable for full-time regular use (actually, I don't know what issue(s) Sarge might have had, as post-install updates ran me out of space on the too-small / partition I'd initially made, so I decided to apply lessons learned there towards trying to install Edgy instead of reinstalling Sarge).  If anyone can tell me how to fix any of the following problems, I will then wholeheartedly adopt that corresponding system (see links for relevant details, kernel boot messages, etc.):[list]
[*]Ubuntu 6.10 Edgy (2.6.17-series powerpc-smp kernel) [boots up with an all-black-on-black display signal, then after X starts all my F-key virtual console text display is distorted/jittery](http://ubuntuforums.org/showthread.php?t=423267) (looks like the horizontal scanlines are misaligned/malsynced? Also applies to shutdown kernel messages, too) -- this means all text-mode consoles are practically useless, so I am limited to using only X-based terminals (the Edgy installer also had this display problem, but I muddled thru the distorted display well enough to complete an install);
[*]Ubuntu 7.04 Feisty (2.6.20-series powerpc-smp kernel) boots up with perfect console text display and better hardware recognition, [except for one serious flaw: Feisty can only access one hard disk](http://ubuntuforums.org/showthread.php?t=440592) (a Wide SCSI Seagate drive adapted to my mobo's Fast SCSI-2 bus), out of 3 hard drives and 2 CD drives in my system, so CDs are useless, and I cannot access any other hard drives at all, let alone spread my system out among other partitions on those drives;
[*]Debian 4.0r0 Etch (2.6.18-series powerpc-smp kernel) also boots up with perfect console text display and good HW detection (including all drives), but [two problems conspire to preclude my full adoption](http://forums.debian.net/viewtopic.php?t=15464):[list]
[*]In a rootless install (no root user login configured), the original user created during installation should have Admin/sudo privileges across the installed system, but while 'sudo' commands do work fine in a CLI shell, the user cannot authenticate as an Admin when attempting to launch/perform Admin tasks within GNOME (e.g. all Desktop > Administration menu items prompt for an Admin PW but will not accept the user's PW as an Admin) -- as installed, the user does appear listed in /etc/sudoers but is not part of the sudo group in /etc/group, tho' adding the user to the sudo group in /etc/group does not fix the Admin authentication problem in GNOME;
[*]Hair-trigger keeeybbbbboardd-rreeepppeaat issues are *maddening*!  Every time I think I've fixed it with some tweak to the keyboard repeat/delay variables in GNOME prefs, or in my xorg.conf, or just running a shell command (IIRC, something like 'kbdrate -r 10.0 -d 500'), something makes it start going crazy again.  The F-key virtual consoles are the worst -- due to this problem, I can't even log in there at all, except for brief periods of calm after a temporary fix (and I'm never sure what seems to briefly fix it, if it's anything I do at all).[/list][/list]So there you have'em.  If anyone could help me just get *any* of these systems past any of their teething problems, I would be a grateful and happy Linux nerd n00b! \\:D/

---

