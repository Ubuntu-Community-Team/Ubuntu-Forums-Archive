---
title: "rbash login fail"
date: 2022-07-01
forum: General Help
---

### Post by vbgf3 on 2022-07-01
Hi,

I used chsh to change shell to /bin/rbash and I can't login. So I did both apt-get update and apt-get upgrade. Still no luck. Help. Using Ubuntu 21.

---

### Post by vbgf3 on 2022-07-01
I found some 'fails' in syslog, they haopened during the time I tried to log in


gsd-color[17869]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/xrandr_LG_Display_gdm_127


gdm-launch-environment]: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' fai
led


/usr/libexec/gdm-wayland-session[23497]: -/bin/rbash: line 1: /usr/bin/gnome-session: restr
icted: cannot specify `/' in command names
Jul  1 12:44:13 zzz-HP-ProBook-440-G7 gdm3: Gdm: GdmDisplay: Session never registered, failing


/usr/libexec/gdm-wayland-session[23469]: -/bin/rbash: line 1: /usr/bin/gnome-session: restr
icted: cannot specify `/' in command names
Jul  1 12:44:05 zzz-HP-ProBook-440-G7 gdm3: Gdm: GdmDisplay: Session never registered, failing


/usr/libexec/gdm-wayland-session[23022]: dbus-daemon[23022]: [session uid=127 pid=23022] Ac
tivated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1


gnome-session-binary[23024]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL ||
 *error == NULL' failed


gnome-session[23024]: gnome-session-binary[23024]: GLib-GIO-CRITICAL: g_bus_get_sync: asser
tion 'error == NULL || *error == NULL' failed

Hope this helps.

---

### Post by TheFu on 2022-07-01
"Ubuntu 21" is ambiguous.  21.04 support ended in January.  21.10 support ends next month (this month?).

Basically, it isn't worth trying to figure out this issue on unsupported versions.  Move to 22.04 and try again.
Be certain that rbash exists and is listed as in /etc/shells as a valid shell.

I'm not saying this is not a bug.  Very few people will use a restricted shell, so it isn't well-tested, if at all.

If you use a supported LTS release (22.04) or the alpha release for 22.10 that is being developed now and test it, find an issue, then submit a bug, there is a much higher chance to be fixed.  That's especially true for the 22.10&#945;.

I did test on a 20.04 system. Here's the commands:
```
rtf@regulus:~$ chsh -s  /bin/rbash
Password:
rtf@regulus:~$ logout

tf@regulus:~$ su - rjp
Password:
rtf@regulus:~$ ps
    PID TTY          TIME CMD
1893542 pts/0    00:00:00 rbash
1893555 pts/0    00:00:00 ps
```

I logged in a rtf, changed the shell to rbash, logged out, then logged in again, forcing all the init files to be used.  It all worked. The commands an prompt show where the different usernames are used.

For fun, I tried a GUI session too.  A few setting files were unreadable and a loop of GUI errors were displayed.  Turns out the specific files were owned by root, since that username was my backup root-login username.  After changing all the file ownership from root to rtf in the ~rft/ area, logins work fine, but a bunch of other GUI things don't  work, as would be expected inside a restricted shell.  Restricted shells are meant to be used for highly restricted environments, not general GUI use.

---

### Post by vbgf3 on 2022-07-01
Hi TheFu,

Thanks for the reply. I am using Ubuntu 22.04 LTS, minimal install.

I am trying to prepare a surfing account, where I only download browsers, and surf. It is not in sudoers, and nothing administrative is done using it. I want it to be protected against hackers, and the riskyest thing i do on it is surf. I come from Windows 11 21H2, and have been successfully attacked while using hardened services and Sandboxie and NoVrusThanks OSArmor. I believe it was a javascript based attack entrypoint and the attacker gained root. I believe persistence was gained by modifying a saved program installer which was part of my backups, because I experienced an instantaneous attack after I completed a new install and went online. I am taking a Linux detour and trying to relearn some Unix things I learnt in the past with OpenBSD some 15 years ago.

I am using Chrome. Currently I am using setpriv and bwrap together with Chrome. I plan on layering an apparmor profile to Chrome. But the internal working of Linux are new to me so this may take a while. I also plan on configuring the system to least privilege so that this surfing account can't do nothing useful 

System is minimally hardened by removing avahi-daemon and cups, which are two listening services i see. 

Anyways, I plan on using rbash to somewhat contain the attacker. Won't stop all attacks, but it is a defence layer. I somehow managed to login to Gnome before while rbash was the shell, but now it doesn't work anymore with this install.

I tried using CTRL ALT F3 to use a plain terminal as you did,  Changed the shell to rbash, and the login was successful. But login fails when I try Gnome.

---

### Post by TheFu on 2022-07-01
If you use chromium, under a different username, and chromium is installed as a snap package, you'll have some protections.

If you use chromium, without a snap package, you can setup firejail in "private" mode that doesn't allow anything from the browser to touch any storage on the system at all and only a pristine, new, account view is provided to the browser each time it is started in this way.

Or you can run chromium inside a full linux container that you build whenever it is needed.  Some other long-time posters in these forums have links for setting up a GUI program to run under a linux container on Ubuntu.

Or you can create a minimal LXD container with just the broswer you like and run stuff there.

Or you can create a minimal virtual machine with no other purpose than using the browser.

Regardless, I'd never install chrome - the browser created by the largest internet tracking and advertising company in the world. That just seems like a terrible thing to do for privacy or security.

Of course, you can also setup a chromebook virtual machine. Without the chromebook/chromebox hardware and TMP, it won't be as secure as a real chromebook, but is will be light and probably more secure than 99% of other OSes we'd setup inside a VM.  Neverware used to make a versions of ChromiumOS for this purpose, but I haven't looked recently.

Regardless, restricted shells really aren't the way to run a DE or GUI program unless you control EVERYTHING that is needs access into. That isn't hard, but lots of accounting and allowing access to specific libraries will be necessary because of the nature of GUIs and browsers.

$ more ~/bin/firepchrome 
```
#!/bin/bash 

# limit RAM VSS to 4G
FJ_OPTS="--join-or-start=chromiumNormal --dns=172.22.22.80 \
         --private --rlimit-as=4096000000"
CH_OPTS=""

PID=$(/usr/bin/firejail $FJ_OPTS /usr/bin/chromium-browser $@ )

```
is my chromium script to run it in side a private firejail. I force an internal DNS server, so the broswers don't invalidate my DNS for their own preferences. I'm not grandma and don't need someone forcing me to use a specific DNS.

You can play with firejail using bash to see what is restricted and what isn't.  Try:
```
$ firejail --private bash
```
See what can and cannot be seen and accomplished in that shell to get an idea. I think you'll be convinced.  Alas, firejail and snaps conflict with each other, so only 1 can be used at a time.

---

