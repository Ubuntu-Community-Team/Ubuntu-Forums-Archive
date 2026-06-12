---
title: "How to account for program restarts in a wrapper script?"
date: 2022-04-18
forum: General Help
---

### Post by &amp;KyT$0P# on 2022-04-18
I've run into several cases where it would be useful to run a program in a wrapper script that:
[LIST]
[*]does some initial setup,
[*]runs the program,
[*]does some cleanup after the program quits,
[*]exits with same exit code as the program did.
[/LIST]

Unfortunately this doesn't work well when the program being wrapped has the ability to restart itself.  When that happens, the wrapper script thinks the program has just quit and erroneously goes on to the cleanup.

How to make the wrapper script account for the program restarting?

I have been writing the wrapper scripts as bash scripts, but could use Python3 if it would make this problem better solvable.

Examples of programs that can do this type of self-restart include KeePassXC latest version (change theme to or from Classic) or Chromium flatpak (go to chrome://restart/).

---

### Post by TheFu on 2022-04-18
If bash is the wrapper, use the 'trap' function to capture all possible ways the binary code might be closes to do cleanup.  Years ago I saw a presentation by Michael Porter at a LUG. I don't recall the exact title, but something about *scripting with belts AND suspenders* to create bulletproof scripts.  He didn't allow the LUG to record it, unfortunately.  If anyone has a LUG (or other group where bash scripting is prevalent), I bet he'd be happy to present virtually.  The information is excellent, but the delivery is monotone.

I'm not seeing KeePassXC issues.  If it isn't running, I have an accel key-chord to launch it. That's simple enough, since I generally don't want it running if it isn't actively being used.  Too much critical information inside that DB and as much as a trust the team behind it, I'd rather not have any of that data in RAM to be slurped.  Sure, I get that it is supposed to be encrypted unless being used, but ... programs have bugs all the time.

[https://www.linuxjournal.com/content/bash-trap-command](https://www.linuxjournal.com/content/bash-trap-command) has an example cleanup() function called by a trap.
>     does some initial setup,
    runs the program,
    does some cleanup after the program quits,
    exits with same exit code as the program did.
Cleanup - use a trap
To pass the same exit code, save $? and return/exit with that.
Generally, a pid file is used to lookup whether a process is still running. Check the process table for the PID - if it doesn't exist, run the cleanup (which should remove the old PID file) and restart, creating a new PID.  I'd put a counter in to prevent thousands of restarts for a binary that just isn't working.

---

### Post by &amp;KyT$0P# on 2022-04-18
Thanks for the advice TheFu.  I changed it to run the cleanup on EXIT trap, so now I have something like this -
```
#!/bin/bash

exit_cleanup() {
  echo "After!"
  exit $x
}

echo "Before!"

trap exit_cleanup EXIT

flatpak run org.chromium.Chromium "$@"
x=$?
```

That does look more robust.  But still if I go to chrome://restart/ in that Chromium instance, the wrapper already prints "After!" and exits.

---

### Post by TheFu on 2022-04-18
I'd be inclined to just have an alias for running flatpak stuff, but if a browser is failing, I don't want it to automatically restart. I'd like to see the failure so I know to hunt down the logs and see what happened.

I'm not using any flatpaks, but with 22.04, I can see more use, assuming I can customize a few different profiles for each program. 

There are times when I want to run chromium where it is allowed to write to my HOME directory, but nowhere else.  There are other times when I want to run chromium and NOT allow it to read anywhere or write anywhere.  That's my default use for that browser.  

When doing online banking, I want the browser to appear 100% new each time with no prior settings and not allowed to save anything outside that environment ... but sometimes I need to download forms and statements, which I want to manually move from the protected area to a permanent area.  Firejail supports these modes - it is cumbersome, which is good. It shouldn't be easy to access files placed into an overlay file system.

I'm just spitballing here, but if a program is a daemon, systemd has an easy way to autostart it. That shouldn't be used for GUI programs.  Perhaps using the *daemontools* suite or the **daemon** (see daemon *package*) to handle the GUI program wrapped in validation that a GUI session is active would work?  IDK.

I'd be worried that an auto-restarting GUI (like firefox after an update) would kick off both the daemon restart task and the built-in FF restart task.  FF has protections against running multiple instances, but those projections generally don't work under the constraint systems as provided by snaps or firejail (and I'd expect flatpaks).

</spitballing>
;)

---

### Post by &amp;KyT$0P# on 2022-04-19
> **TheFu said:**
>  **daemon** (see daemon *package*) 

That helps, thanks!  With
```
daemon --foreground -- keepassxc "$@"
```
It works! :D
Works also with flatpak version of KeePassXC!

Trying this with Chromium, it just quits when I go to chrome://restart/ .  That's still an improvement, though ideally I would like restart to work properly.

> There are other times when I want to run chromium and NOT allow it to read anywhere or write anywhere. 

Actually that is exactly what I'm trying to achieve with writing a wrapper script for Chromium flatpak.  I can get most of the way there using flatseal, but there is still the [FONT=Courier New]~/.var/app/org.chromium.Chromium[/FONT] directory.

---

### Post by TheFu on 2022-04-19
Ah ... I have an 18.04 system around that has the latest chromium outside any snap/flatpak still. It runs fine in firejail.
```
#!/bin/bash

FJ_OPTS="--join-or-start=chromiumNormal --dns=172.22.22.80 \
         **--private **--rlimit-as=4096000000"
CH_OPTS=""

# limit RAM VSS to 4G
PID=$(/usr/bin/firejail $FJ_OPTS /usr/bin/chromium-browser $@ )
```

Note how I force a DNS to be used, regardless of what chromium (or any other attempted DNS takeover) may want.
Of course, using --dns has some caveats:
```
              Note: this feature is not supported on systemd-resolved setups.
```
Yet anther reason to disable/mask/purge systemd-resolved!

When 18.04 support ends, I'll have to solve the same issue you have. For now, I'll be lazy. ;)

---

### Post by &amp;KyT$0P# on 2022-04-25
bump

---

### Post by TheFu on 2022-04-25
> **halogen2 said:**
> bump

Chromium seems to be a special situation, since the dev team is abusing cgroups and namespaces for protections inside the Chromium processes. This often conflicts with outside tool efforts.

In post #5, you said "it works" .... so something isn't working?

---

### Post by &amp;KyT$0P# on 2022-04-25
> **TheFu said:**
> In post #5, you said "it works" .... so something isn't working?

The "It works!" was only referring to KeePassXC.  What still isn't quite working is wrapping Chromium -
> Trying [[FONT=Courier New]daemon --foreground[/FONT]] with Chromium, it just quits when I go to chrome://restart/ . That's still an improvement, though ideally I would like restart to work properly.

---

### Post by #&amp;thj^% on 2022-04-25
> **halogen2 said:**
> The "It works!" was only referring to KeePassXC.  What still isn't quite working is wrapping Chromium -
while using that script in Chromium show this:
```
journalctl --user >journal-user.txt
```

---

### Post by &amp;KyT$0P# on 2022-04-25
Here are all [FONT=Courier New]journalctl --user[/FONT] lines added after I ran the wrapper script, went to chrome://restart/ and Chromium just quit -
```
dbus-daemon[916]: [session uid=1000 pid=916] Activating via systemd: service name='org.freedesktop.Flatpak' unit='flatpak-session-helper.service' requested by ':1.46' (uid=1000 pid=1327 comm="flatpak run org.chromium.Chromium " label="unconfined")
systemd[899]: Starting flatpak session helper...
dbus-daemon[916]: [session uid=1000 pid=916] Successfully activated service 'org.freedesktop.Flatpak'
systemd[899]: Started flatpak session helper.
dbus-daemon[916]: [session uid=1000 pid=916] Activating via systemd: service name='org.freedesktop.portal.Documents' unit='xdg-document-portal.service' requested by ':1.46' (uid=1000 pid=1327 comm="flatpak run org.chromium.Chromium " label="unconfined")
systemd[899]: Starting flatpak document portal service...
dbus-daemon[916]: [session uid=1000 pid=916] Activating via systemd: service name='org.freedesktop.impl.portal.PermissionStore' unit='xdg-permission-store.service' requested by ':1.48' (uid=1000 pid=1339 comm="/usr/libexec/xdg-document-portal " label="unconfined")
systemd[899]: Starting sandboxed app permission store...
dbus-daemon[916]: [session uid=1000 pid=916] Successfully activated service 'org.freedesktop.impl.portal.PermissionStore'
systemd[899]: Started sandboxed app permission store.
dbus-daemon[916]: [session uid=1000 pid=916] Successfully activated service 'org.freedesktop.portal.Documents'
systemd[899]: Started flatpak document portal service.
systemd[899]: Started app-flatpak-org.chromium.Chromium-1327.scope.
dbus-daemon[916]: [session uid=1000 pid=916] Activating via systemd: service name='org.freedesktop.portal.Flatpak' unit='flatpak-portal.service' requested by ':1.50' (uid=1000 pid=1354 comm="xdg-dbus-proxy --args=42 " label="unconfined")
systemd[899]: Starting flatpak portal...
dbus-daemon[916]: [session uid=1000 pid=916] Successfully activated service 'org.freedesktop.portal.Flatpak'
systemd[899]: Started flatpak portal.
systemd[899]: Started app-flatpak-org.chromium.Chromium-1375.scope.
dbus-daemon[916]: [session uid=1000 pid=916] Activating via systemd: service name='org.freedesktop.portal.Desktop' unit='xdg-desktop-portal.service' requested by ':1.54' (uid=1000 pid=1354 comm="xdg-dbus-proxy --args=42 " label="unconfined")
systemd[899]: Starting Portal service...
dbus-daemon[916]: [session uid=1000 pid=916] Activating via systemd: service name='org.freedesktop.impl.portal.desktop.gtk' unit='xdg-desktop-portal-gtk.service' requested by ':1.55' (uid=1000 pid=1399 comm="/usr/libexec/xdg-desktop-portal " label="unconfined")
systemd[899]: Starting Portal service (GTK/GNOME implementation)...
dbus-daemon[916]: [session uid=1000 pid=916] Successfully activated service 'org.freedesktop.impl.portal.desktop.gtk'
systemd[899]: Started Portal service (GTK/GNOME implementation).
dbus-daemon[916]: [session uid=1000 pid=916] Successfully activated service 'org.freedesktop.portal.Desktop'
systemd[899]: Started Portal service.
systemd[899]: app-flatpak-org.chromium.Chromium-1327.scope: Consumed 2.260s CPU time.
```

---

### Post by #&amp;thj^% on 2022-04-26
I was hoping for something that would jump out at us.
I wonder though about " app-flatpak-org.chromium."version vs a .deb chromium?

---

### Post by &amp;KyT$0P# on 2022-04-26
> **1fallen said:**
> I wonder though about " app-flatpak-org.chromium."version vs a .deb chromium?

If this were specifically *only* about Chromium, sure I could just use a .deb and firejail and forget about involved wrapper scripts.  However Chromium is not the only program in question here, in fact it's not even the only Chromium based browser I have as flatpak and would like the wrapper script to work with.

---

### Post by #&amp;thj^% on 2022-04-26
well then, I guess that solidifies post #8
I too am curious why TheFu's post #6 works only on "keepassxc" very curious.

---

### Post by &amp;KyT$0P# on 2022-04-30
bump

---

### Post by &amp;KyT$0P# on 2022-05-04
bump

---

### Post by &amp;KyT$0P# on 2022-05-07
Hmm.  If I do
```
daemon --foreground -- sh -c 'flatpak run org.chromium.Chromium;sleep 10'
```
Then Chromium does restart, but gets spontaneously killed when the [FONT=Courier New]sleep 10[/FONT] finishes and [FONT=Courier New]sh[/FONT] exits.  And the cleanup code does not run until after this.

When Chromium is killed, it prints this in Terminal (timestamps removed) -
```
:FATAL:bus.cc(1225)] D-Bus connection was disconnected. Aborting.
:FATAL:bus.cc(1225)] D-Bus connection was disconnected. Aborting.
:FATAL:bus.cc(1225)] D-Bus connection was disconnected. Aborting.
:ERROR:scoped_ptrace_attach.cc(27)] ptrace: Operation not permitted (1)

```

---

### Post by #&amp;thj^% on 2022-05-07
This sounds like a "systemd-resolve" fail.
at least to me, can you test it without systemd-resolve enabled?
just stabbing in the dark.

---

### Post by &amp;KyT$0P# on 2022-05-07
> **1fallen said:**
> can you test it without systemd-resolve enabled?

That system uses dnsmasq instead of systemd-resolved.

---

### Post by &amp;KyT$0P# on 2022-05-07
This gets stranger and stranger.  I'm testing this stuff in a VM (VirtualBox 6.1.32, both host & guest are Xubuntu 22.04), and using [FONT=Courier New]daemon[/FONT] with Chromium is causing serious lag of some stuff on the *host*?? :shock:
Specifically, using the shared clipboard to copy some text from the guest into Firefox on the host reproducibly results in the lag, although the lagging is not limited to just that.

Anyway, for reasons unrelated to this I happened on [Python3 psutil [FONT=Courier New]Process.wait()[/FONT]]("https://psutil.readthedocs.io/en/latest/#psutil.Process.wait"), and to my surprise this seems to solve the restart problem -
```
#!/usr/bin/env python3

import os, psutil, subprocess, sys

print('Before!')

s=subprocess.run(['flatpak', 'run', 'org.chromium.Chromium']+sys.argv[1:])
waitProcess = None
for p in psutil.process_iter(['pid', 'cmdline']):
  c = p.cmdline()
  if len(c) > 0 and c[0] == 'bwrap' and os.path.basename(c[-1]) == 'chromium':
    waitProcess = p
    break
if waitProcess:
  r=waitProcess.wait()
else:
  r=s.returncode

print('After!')

print('exit', r)
sys.exit(r if type(r) is int else 0)

```
Not quite ideal, because I can't get exit code of a restarted Chromium.  But then again, some more careful testing of [FONT=Courier New]daemon[/FONT] indicates it too seems to eat the exit code, at least under some circumstances.  I'm thinking at this point, maybe I just shouldn't bother about the exit code, it's not hugely important in the cases I would like wrapper scripts.

Although I prefer the simplicity of the [FONT=Courier New]daemon[/FONT] based solution in the cases when it works.  So before I mark this solved, any ideas why using [FONT=Courier New]daemon[/FONT] inside a VM would cause such pervasive lagging?

---

### Post by &amp;KyT$0P# on 2022-05-12
> **halogen2 said:**
> before I mark this solved, any ideas why using [FONT=Courier New]daemon[/FONT] inside a VM would cause such pervasive lagging?

bump

---

### Post by &amp;KyT$0P# on 2022-05-16
bump

---

### Post by &amp;KyT$0P# on 2022-05-26
Seems the lag issue with use of [FONT=Courier New]daemon[/FONT] inside VM was fixed after some system updates, notably including VirtualBox version 6.1.34-150636.1~Ubuntu~jammy.  So I think I'm now good to use [FONT=Courier New]daemon[/FONT] where it solves this problem.  Thanks again to all who helped here. :KS

---

