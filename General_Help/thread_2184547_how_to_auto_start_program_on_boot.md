---
title: "how to auto start program on boot?"
date: 2013-10-29
forum: General Help
---

### Post by kdomrose2 on 2013-10-29
I am running 12.04 lts
I have 2 programs that need to run on boot.
Program is direwolf and xastir. This is a clean install of Ubuntu and all updates applied.
I have tried putting them in startup application. All that does is open the script in gedit.
I can  click on the startup script, or type it in a terminal and they run fine.
Both programs need to run from a terminal.

I have also tried creating a .desktop file. Same result.
Have tried putting them in the autostart folder.same result.
Also tried setting up a crontab job.same result.

No matter which method I use they will run manually, but not on boot.

The direwolf program needs to be started with root, or sudo also.

I have been googling for a week now and I am out of ideas.

Any input is welcome.

---

### Post by TheFu on 2013-10-29
The quick answer is to modify the /etc/rc.local file. Everything run from there runs as root. NEVER run a GUI program from there.

The better answer is to create a startup/shutdown script modeled after any other one inside /etc/init.d/, then use update-rc.d to have it start and stop under the appropriate runlevels as needed.

I have NO idea at all about those specific programs, so this advice may not be good or needed. ;)

---

### Post by kdomrose2 on 2013-10-29
Thanks.... I will try that when I get home tonight. I seem to Remember trying rc.local in the beginning without much luck.  I will revisit it as I have working scripts now..

---

### Post by kdomrose2 on 2013-11-03
well I tried every permutation I could think of in /etc/rc.local with no luck whatsoever. If I open a terminal and run rc.local it works fine. Just will not run on bootup.
Then tried /etc/init.d  Same results.
No matter what I tried would not work.

Even tried upstart. That fails also.

I ended up cheating. ;)

Since this machine had one function only and there is NO sensitive info on it at all I configured sudo to not need a password.
I know, I know.. Not supposed to do that.

I then created a couple of shell scripts that basically looked like this

```

#!/bin/bash

sleep 20

sudo gnome-terminal -x /usr/local/bin/direwolf

exit 0

```

I then put the script to startup using startup applications..
This solves my problem for this machine. I am still curious as to why none of the other methods would work for me.

---

### Post by TheFu on 2013-11-03
Scripts running as root from rc.local or /etc/init.d/ do not have any -environment- ... no $PATH and minimal other settings.  You must specify the complete environment that you wish for them to use. Normally, we completely spell out the full-path-to-any-program and set environment variables like LD_LIBRARY_PATH and JAVA_HOME as required for each script.  So, putting this:
```
/usr/local/bin/direwolf &
```

at the bottom of the /etc/rc.local script, before any exit, should work.  That is, unless there are some weird dependencies, libraries, config/settings, or hardware things involved. Each of those could be a _fly-in-the-ointment_.

By running the command from your user-id after login, you may set a basic environment up that gets transferred via sudo.  The bash manpage tries to explain the difference between a console shell and a non-console shell.  Some of the differences c an be very frustrating until we understand  the _why_.  Hardware can behave differently for a real login  - like audio stuff wont work. This is to prevent someone remotely logging in and playing music, or other audio clips when someone else is on  the _head_.

You are correct in your understanding of using sudo in scripts. It is generally considered bad form.  By not having a password, you have opened the entire system to being trivially hacked.  It is possible to accidentally download a .desktop file that takes over your system. Nice.

I would strongly encourage you to rectify the issue sooner than later. Ask for help, if you get stuck.

---

### Post by kdomrose2 on 2013-11-04
Thanks..I will keep pecking away at it.

The direwolf program is an audio type program. It is basically turning the soundcard into a X.25 modem.

Would that be part of my frustrations?

---

### Post by kdomrose2 on 2013-11-04
well..

I tried entering

```
/usr/local/bin/direwolf &
```

into the /etc/rc.local file right above the exit 0

Same result. Does not startup.

Very frustrating.

---

### Post by kdomrose2 on 2013-11-04
If I drop to a terminal and enter /etc/rc.local it does nothing.

If I do sudo /etc/rc.local the program direwolf starts up fine.

The commands in the rc.local seem to be correct. I can't seem to get it to actually run when the system starts up.

---

### Post by TheFu on 2013-11-05
rc.local is called through the old style /etc/init.d/ scripts on every system I have ever seen from 1993 on, but I have NOT seen anything newer than 12.04 LTS. There should be a script in that directory, with the same name that starts/stops it. Check the status and enable it, if necessary using **update-rc.d**.

Permissions and ownership of /etc/rc.local should be **root.root 755 **. If this is not clear, a little tutorial on unix file permissions would be a good idea today.

Remember how I said that startup scripts do not have ANY environment?  Are there specific environment variables needed by direwolf? If so, you need to set those. I could suspect that the LD_LIBRARY_PATH (or the system default) would need to modified, however, I do not if that is required for that program or not. There may be other settings too.  This sort of stuff should be explained in the README or INSTALL file that came with the program.

---

### Post by christopher-lees on 2013-11-05
The instructions for using Direwolf on the Raspberry Pi will also work on a normal Linux distribution. It has a suggestion of using the Crontab to automatically start Direwolf and ensure it keeps running.

[http://home.comcast.net/~wb2osz/Version%200.8/Raspberry-Pi-APRS.pdf](http://home.comcast.net/~wb2osz/Version%200.8/Raspberry-Pi-APRS.pdf)

---

### Post by kdomrose2 on 2013-11-07
Christopher 
I am familiar with that link. I have tried using crontab already with  same results. 
My suspicion is I do not have proper environment variables setup. Something I will need to research.

I will get this resolved eventually. When I do I will post back here with findings.

---

