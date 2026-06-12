---
title: "dell laptop, random freezing only while screen off or lid closed"
date: 2018-09-30
forum: General Help
---

### Post by 9-david-1 on 2018-09-30
I have a Dell 7373, with a Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz. I'm running a fairly stock version of xubuntu 18.04, kernel 4.15.0-33-generic. (It's the latest kernel I got from an apt upgrade)

Programs I regularly run: virtualbox, google-chrome, thunderbird, visual-studio-code, slack, nginx.


For a couple of months now, once every day or so my computer will lock up. (I've only had this computer for a couple of months, so it's essentially been happening since day one.) It **only** happens if the screen is off (either powersave or lid closed). Sometimes it might happen after only 20 or 30 minutes of screen-off, other times it will go for hours, other times it won't freeze. No pattern I have been able to find. Also, I don't have any sort of sleep or hibernation enabled. Just the screen timeout (or as I said if I close the lid, which I've set to only turn off the screen).

It has literally **never** crashed/frozen when the screen was active (I use this machine for my programming work, which means I'm on it doing intensive compiles, database stuff, etc for literally hours at a time)

What it's actually doing: when I open the lid (if it was closed) and try moving the cursor or typing, the screen just doesn't come on, and it doesn't respond in any way. Can't SSH in. The only thing that works is press-and-hold power button until a forced power-off.

Here's what I've tried thus far:


[LIST]
[*]memtest - ran for about 30 mins with no errors (I wasn't expecting to find anything here: it literally NEVER freezes if the screen is on. With a hardware problem I would expect some freezes when the screen is on too)
[*]check md5 of install ISO (it's good - 1b0bcbad9853cf7a4cade6324e6622f7)
[*]after freeze try switching to text console (ctrl+alt+fN)
[*]after freeze try opening SSH terminal from another computer
[*]before freeze open SSH terminal connection and start journalctl -f
connection broken when freeze occurs, no useful info in journalctl
[*]install linux-crashdump, check /var/crash after freeze
this one surprised me. i know it was working because i had one entry in this folder (_opt_google_chrome_chrome.1000.crash, 9/23/18), but nothing after a freeze.
[*]checking for cron job (or anacron) that coincides with timing of crashes (nothing)
[/LIST]

In hopes of at least narrowing down a time frame when it's happening, I set up a bash script to add an "awake" log entry every minute (so that I could see when they stopped. I've had two freezes this weekend while running my script. Here's about a 20 minute window of journalctl before each one. 

Does anyone know of anything else I might be able to look for or try?

```
Sep 29 13:41:13 user-Inspiron-7373 user[1948]: awake
Sep 29 13:41:35 user-Inspiron-7373 gnome-keyring-daemon[1354]: asked to register item /org/freedesktop/secrets/collec
Sep 29 13:41:35 user-Inspiron-7373 gnome-keyring-daemon[1354]: asked to register item /org/freedesktop/secrets/collec
Sep 29 13:41:42 user-Inspiron-7373 systemd-resolved[683]: Server returned error NXDOMAIN, mitigating potential DNS vi
Sep 29 13:41:42 user-Inspiron-7373 systemd-resolved[683]: Server returned error NXDOMAIN, mitigating potential DNS vi
Sep 29 13:41:42 user-Inspiron-7373 systemd-resolved[683]: Server returned error NXDOMAIN, mitigating potential DNS vi
Sep 29 13:41:48 user-Inspiron-7373 dbus-daemon[1374]: [session uid=1000 pid=1374] Activating service name='org.gnome.
Sep 29 13:41:48 user-Inspiron-7373 dbus-daemon[1374]: [session uid=1000 pid=1374] Successfully activated service 'org
Sep 29 13:42:13 user-Inspiron-7373 user[2388]: awake
Sep 29 13:43:13 user-Inspiron-7373 user[2444]: awake
Sep 29 13:44:13 user-Inspiron-7373 user[2483]: awake
Sep 29 13:45:13 user-Inspiron-7373 user[2633]: awake
Sep 29 13:45:36 user-Inspiron-7373 snapd[841]: storehelpers.go:398: cannot refresh: snap has no updates available: "c
Sep 29 13:45:36 user-Inspiron-7373 snapd[841]: autorefresh.go:387: auto-refresh: all snaps are up-to-date
Sep 29 13:46:13 user-Inspiron-7373 user[2662]: awake
Sep 29 13:47:13 user-Inspiron-7373 user[2723]: awake
Sep 29 13:48:13 user-Inspiron-7373 user[2974]: awake
Sep 29 13:49:13 user-Inspiron-7373 user[3033]: awake
Sep 29 13:49:13 user-Inspiron-7373 kernel: acpi INT3400:00: Unsupported event [0x86]
Sep 29 13:49:19 user-Inspiron-7373 systemd-logind[756]: Lid closed.
Sep 29 13:49:24 user-Inspiron-7373 kernel: dell_wmi: Unknown key with type 0x0000 and code 0xe070 pressed
Sep 29 13:49:45 user-Inspiron-7373 kernel: dell_wmi: Unknown key with type 0x0000 and code 0xe070 pressed
Sep 29 13:49:54 user-Inspiron-7373 systemd-logind[756]: Lid opened.
Sep 29 13:49:54 user-Inspiron-7373 kernel: acpi INT3400:00: Unsupported event [0x86]
Sep 29 13:50:13 user-Inspiron-7373 user[3054]: awake
Sep 29 13:50:34 user-Inspiron-7373 systemd[1]: Starting Cleanup of Temporary Directories...
Sep 29 13:50:34 user-Inspiron-7373 systemd[1]: Started Cleanup of Temporary Directories.
Sep 29 13:51:13 user-Inspiron-7373 user[3069]: awake
Sep 29 13:51:45 user-Inspiron-7373 pkexec[3083]: pam_unix(polkit-1:session): session opened for user root by (uid=100
Sep 29 13:51:45 user-Inspiron-7373 pkexec[3083]: user: Executing command [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/
Sep 29 13:52:13 user-Inspiron-7373 user[3090]: awake
Sep 29 13:53:13 user-Inspiron-7373 user[3094]: awake
Sep 29 13:54:13 user-Inspiron-7373 user[3102]: awake
Sep 29 13:55:13 user-Inspiron-7373 user[3118]: awake
Sep 29 13:56:13 user-Inspiron-7373 user[3127]: awake
Sep 29 13:57:13 user-Inspiron-7373 user[3150]: awake
Sep 29 13:57:50 user-Inspiron-7373 systemd-resolved[683]: Using degraded feature set (UDP) for DNS server 192.168.22.
Sep 29 13:58:13 user-Inspiron-7373 user[3157]: awake
Sep 29 13:59:13 user-Inspiron-7373 user[3169]: awake
Sep 29 14:00:13 user-Inspiron-7373 user[3180]: awake
Sep 29 14:00:41 user-Inspiron-7373 systemd[1]: Started Run anacron jobs.
Sep 29 14:00:41 user-Inspiron-7373 anacron[3189]: Anacron 2.3 started on 2018-09-29
Sep 29 14:00:41 user-Inspiron-7373 anacron[3189]: Normal exit (0 jobs run)
Sep 29 14:01:13 user-Inspiron-7373 user[3196]: awake
-- Reboot --
Sep 29 14:14:38 user-Inspiron-7373 kernel: Linux version 4.15.0-34-generic (buildd@lgw01-amd64-047) (gcc version 7.3.
Sep 29 14:14:38 user-Inspiron-7373 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-34-generic root=UUID=5276f0f

```

```
Sep 30 14:07:39 user-Inspiron-7373 user[28465]: awake
Sep 30 14:08:39 user-Inspiron-7373 user[28480]: awake
Sep 30 14:09:01 user-Inspiron-7373 CRON[28482]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 30 14:09:01 user-Inspiron-7373 CRON[28483]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/syst
Sep 30 14:09:01 user-Inspiron-7373 CRON[28482]: pam_unix(cron:session): session closed for user root
Sep 30 14:09:05 user-Inspiron-7373 systemd[1]: Starting Clean php session files...
Sep 30 14:09:05 user-Inspiron-7373 systemd[1]: Started Clean php session files.
Sep 30 14:09:39 user-Inspiron-7373 user[28534]: awake
Sep 30 14:10:39 user-Inspiron-7373 user[28548]: awake
Sep 30 14:11:39 user-Inspiron-7373 user[28552]: awake
Sep 30 14:12:39 user-Inspiron-7373 user[28566]: awake
Sep 30 14:13:39 user-Inspiron-7373 user[28574]: awake
Sep 30 14:14:39 user-Inspiron-7373 user[28586]: awake
Sep 30 14:15:39 user-Inspiron-7373 user[28592]: awake
Sep 30 14:16:39 user-Inspiron-7373 user[28604]: awake
Sep 30 14:17:01 user-Inspiron-7373 CRON[28609]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 30 14:17:01 user-Inspiron-7373 CRON[28610]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 30 14:17:01 user-Inspiron-7373 CRON[28609]: pam_unix(cron:session): session closed for user root
Sep 30 14:17:39 user-Inspiron-7373 user[28617]: awake
Sep 30 14:17:53 user-Inspiron-7373 pkexec[28619]: pam_unix(polkit-1:session): session opened for user root by (uid=10
Sep 30 14:17:53 user-Inspiron-7373 pkexec[28619]: user: Executing command [USER=root] [TTY=unknown] [CWD=/] [COMMAND=
Sep 30 14:18:39 user-Inspiron-7373 user[28634]: awake
Sep 30 14:19:39 user-Inspiron-7373 user[28638]: awake
Sep 30 14:19:54 user-Inspiron-7373 pkexec[28642]: pam_unix(polkit-1:session): session opened for user root by (uid=10
Sep 30 14:19:54 user-Inspiron-7373 pkexec[28642]: user: Executing command [USER=root] [TTY=unknown] [CWD=/] [COMMAND=
Sep 30 14:20:39 user-Inspiron-7373 user[28662]: awake
Sep 30 14:21:39 user-Inspiron-7373 user[28668]: awake
Sep 30 14:22:39 user-Inspiron-7373 user[28683]: awake
Sep 30 14:23:39 user-Inspiron-7373 user[28693]: awake
Sep 30 14:24:39 user-Inspiron-7373 user[28700]: awake
Sep 30 14:25:39 user-Inspiron-7373 user[28706]: awake
Sep 30 14:26:39 user-Inspiron-7373 user[28719]: awake
Sep 30 14:27:39 user-Inspiron-7373 user[28729]: awake
Sep 30 14:28:39 user-Inspiron-7373 user[28740]: awake
Sep 30 14:29:39 user-Inspiron-7373 user[28748]: awake
-- Reboot --
Sep 30 15:33:30 user-Inspiron-7373 kernel: Linux version 4.15.0-34-generic (buildd@lgw01-amd64-047) (gcc version 7.3.
Sep 30 15:33:30 user-Inspiron-7373 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-34-generic root=UUID=5276f0f


```

---

### Post by 9-david-1 on 2018-10-04
[COLOR=#242729][FONT=Arial]I believe I found a solution to my problem; at least I haven't had a freeze in several days after doing the following:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It occurred to me that since it seems to be related to screen on/off state, that made a video driver seem a likely place to start. In this [article]("https://hobo.house/2018/05/18/fix-for-intel-i915-gpu-freeze-on-recent-linux-kernels/"), the author describes a slightly different kind of freeze, but most importantly gives some information on the various video drivers and how to switch them. I was running the xorg-x11-drv-intel driver, and I used his instructions to switch to the i915 driver:[/FONT][/COLOR]

```
cat > /etc/X11/xorg.conf.d/10-intel.conf <<EOF
Section "Device"
Identifier "Intel Graphics"
Driver "intel"
EndSection
EOF
```
[COLOR=#242729][FONT=Arial]
I also upgraded my kernel to 4.18.11-041811-generic from the [ubuntu kernel site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18.11/"), since the article I referenced mentioned his freezes with the <4.17 kernel.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]While I haven't had any freezes in several days, I can't say definitively that this "solved" the problem since the freezes have been quite unpredictable. But so far so good.[/FONT][/COLOR]

---

