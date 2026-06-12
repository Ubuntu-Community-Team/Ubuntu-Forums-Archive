---
title: "How to automatically suspend while not logged in?"
date: 2018-03-02
forum: General Help
---

### Post by VanillaMozilla on 2018-03-02
I want to be able to suspend the system automatically when no one is logged in.

System settings > Power > "Suspend when inactive for 5 minutes" works only when someone is logged in.  On one computer there is only one user account, and it still doesn't auto suspend.  I even turned off or unplug the mouse to eliminate spurious movements as a possible cause.

I also have set 
System settings > Brightness & Lock > "Turn screen of when inactive for 3 minutes"; Lock ON; Lock screen after Screen turns off; Require my password when waking from suspend.

I tried adding the following lines to /etc/systemd/logind.conf and rebooting, without success:
IdleAction=suspend
IdleActionSec=300
(And yes, I remembered to remove the comment character '#'.)

I have Ubuntu 16.04 32bit and 64bit with Gnome Flashback.  It fails on both.  One computer is an older Dell with Intel Core 2 Duo; the other is a rather new Dell with Intel i5.

Does anyone know how to make this work?

---

### Post by #&amp;thj^% on 2018-03-02
Have Look here: [https://askubuntu.com/questions/529437/computer-not-suspending-when-inactive-in-the-main-log-in-prompt](https://askubuntu.com/questions/529437/computer-not-suspending-when-inactive-in-the-main-log-in-prompt)
Gnome Power manager has been depreciated and no longer works well, but powernap will.
Read carefully.
And from man powernap
```
powernap(8)                        powernap                        powernap(8)

NAME
       powernap  -  have  the  system  "take  a power nap"; this can be a user
       defined ACTION_METHOD in /etc/powernap/config among [best-effort,  sus&#8208;
       pend, hibernate, poweroff, powersave]

DESCRIPTION
       powernap will run when powernapd(8) has determined that an action needs
       to be taken according to its configured parameters. The  action  to  be
       taken, among [best-effort, suspend, hibernate, poweroff], is determined
       in /etc/powernap/config. By default, the action will be best-effort.

       When the ACTION_METHOD is best-effort,  and  if  the  file  /etc/power&#8208;
       nap/action  is  executable,  then  the powernap binary will run it when
       called. Otherwise, powernap will run one of:
        ** * pm-suspend**
         * pm-hibernate
         * poweroff depending on your hardware's capabilities,  as  determined
       by pm-is-supported(1).

       You may do one of:
1)  Write  your  own  custom at **/etc/powernap/**action and make it exe&#8208;
       cutable
         2) Replace /etc/powernap/action with an executable script or binary
         3) Symlink /etc/powernap/action to some other  executable  script  or
       binary

       [B]When  ACTION_METHOD is powersave, then powernap binary will execute pm-
       suspend.
[/B]
       When ACTION_METHOD is powersave, then powernap binary will execute  pm-
       hibernate.

       When  ACTION_METHOD  is  powersave,  then  powernap binary will execute
       poweroff.

       When ACTION_METHOD is powersave, then powernap binary will execute  pm-
       powersave  and  pass  an  argument  (true) to execute all the available
       scripts at /usr/lib/pm-utils/power.d/ and /etc/pm/power.d/. The  latter
       will contain scripts shipped with powernap.

       http://launchpad.net/powernap

FILES
       /etc/powernap/action, /proc/acpi/sleep

SEE ALSO
       powernapd(8), pm-is-supported(1), ethtool(8)

AUTHOR
       This  manpage  and  the  utility  was written by Dustin Kirkland <kirk&#8208;
       land@canonical.com> for Ubuntu systems (but may  be  used  by  others).
       Permission  is  granted to copy, distribute and/or modify this document
       under the terms of the GNU General Public License, Version 3  published
       by the Free Software Foundation.

       On  Debian systems, the complete text of the GNU General Public License
       can be found in /usr/share/common-licenses/GPL.

powernap                          2 Jul 2009                       powernap(8)
```
Cheers

---

### Post by VanillaMozilla on 2018-04-25
Thanks, but this looks scary.  There's a lot to configure, and it looks like the times have to be set just so in order to prevent disaster.  It looks like the default time to shutdown (ABSENT_SECONDS) is 30 seconds, which is absurd.  30 minutes would be about right.  I probably don't understand this.

And then in the final section of /etc/powernap/config it says "Note also that this plugin only reacts to the state of the drive and does not modify the behavior of the drive directly.  Therefore it only makes sense to monitor a drive that has already been configured to standby or sleep."  But I need this program--or plugin, or whatever it is -- to suspend the drive.

OK, so I Googled for "configure drive to sleep Ubuntu 16.04", and I discovered the Disks utility.  Simple.  Just turn it on and define the time.  But there's a problem:  "The problem is, when you suspend your system and resume this stops working."  I'm giving it a try, but I'm not optimistic.

The next recommendation is hdparm.  All I have to do is write an executable script (which I don't understand), and all will be well.  Maybe.  And then it doesn't suspend the whole system.  Just the drive(s).

It looks like I have to use at least two utilities in exactly the right combination, and every time I want to change the parameters it's a big production, that I might get wrong.  Am I misunderstanding this?

Is there just a nice little system setting that just works?  The Power setting used to work.

---

### Post by VanillaMozilla on 2018-04-26
OK, I just noticed the first line in the first reply, with the reference:  
[https://askubuntu.com/questions/529437/computer-not-suspending-when-inactive-in-the-main-log-in-prompt](https://askubuntu.com/questions/529437/computer-not-suspending-when-inactive-in-the-main-log-in-prompt)
I followed the directions, but powernap is not running, even after restarting.  I edited /etc/power/nap/config with the line ACTION_METHOD = 1
and I created file /etc/default/powernap, which has a single line
START=yes

Powernap is not running.  I think the directions are obsolete, but I have no idea how this system is put together, or how to fix it.

---

