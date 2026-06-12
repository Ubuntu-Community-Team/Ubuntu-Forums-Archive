---
title: "Can no longer get desktop environment after log in, just cursor"
date: 2014-11-30
forum: General Help
---

### Post by sremick on 2014-11-30
System: Xubuntu 14.10
Note: full-disk encryption enabled

History:

Somehow (still don't know how) the other day I ran out of inodes due to massive number of files in /tmp (while still having tons of free space). I managed to get /tmp cleaned up, so I'm in the final stages of cleaning up the fallout. As thing stand now the remaining issues are:

- Performance is much, much worse than right before running out of inodes, even though I'm back to plenty available. For example, disk thrashes for a very long time... several minutes... after entering in the volume password on boot, before prompting for the user/pass login. It never took anywhere near this long before. I have about 18% fragmentation now, not sure what it was before inodes were exhausted.
- Once I get to the user/password log in prompt in the GUI, once I try to log in all I get is a movable mouse cursor and a desktop. I wait for the disk to stop thrashing and everything settles and is calm, but the desktop environment never appears.

I can still CTRL-ALT-F1 and get a terminal.

What I've tried so far:

```
cd .cache
rm -rf sessions
```
Didn't help.

I've tried logging in with another account I had still created on this system, it's experiencing the same thing. So it's not profile-specific.

Tried to update things in case an update might straighten stuff out:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Nope, and now after I log in I don't even have my wallpaper, just black. I had been at least getting my wallpaper before. Cursor still movable and I can still CTRL-ALT-F1.

Hopefully someone can help me bring this computer back to life. I feel like I'm 99% there and there's just some stupid little thing mucking up log-in.

---

### Post by Bashing-om on 2014-12-03
sremick; Hey;

Maybe you changed authorization to your /home ?
Check:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
all should be owned and grouped to "you" .
However, I fail to see how this could possibly affect performance. Other things must also be at play here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by sremick on 2014-12-03
> **Bashing-om said:**
> sremick; Hey;

Maybe you changed authorization to your /home ?
Check:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
all should be owned and grouped to "you" .
However, I fail to see how this could possibly affect performance. Other things must also be at play here.[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]

Thanks for stepping in to help! I certainly didn't actively change anything, but who knows what things got screwed up when I ran out of inodes. To answer your questions:

-rw------- 1 scott scott 171 Nov 30 19:56 .Xauthority
-rw------- 1 scott scott 17788 Nov 25 00:08 .ICEauthority

and /home:
drwxr-xr-x 71 scott  scott  4096 Nov 30 19:53 scott

So everything looks fine. And at least this looks better now:

```
df -i
Filesystem                 Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/xubuntu-root 19005440 336721 18668719    2% /
```
That "2%" was at "100%" when all the issues started. I was able to trace it to /tmp but no idea what caused it (or what the files were, as I couldn't even get an ls to work). Took some creative deletion methods.

```
sudo fsck.ext4 -fn /dev/sda1
e2fsck 1.42.10 (18-May-2014)
Warning!  /dev/sda1 is mounted.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 312/124496 files (17.3% non-contiguous), 146253/248832 blocks
```
Quite fragmented (how to you defrag an encrypted volume anyway? e4defrag is not happy with it) but otherwise OK.

Here's all of /var/log/syslog starting from the point where I attempt to log into my desktop/profile:
```
Dec  3 20:54:10 OptiPlex-780 dbus[1383]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Dec  3 20:54:10 OptiPlex-780 dbus[1383]: [system] Successfully activated service 'org.freedesktop.systemd1'
Dec  3 20:54:15 OptiPlex-780 lvpnc[1939]: Session not found inject in user space and execve
Dec  3 20:54:15 OptiPlex-780 kernel: [ 8910.099258] lvpnc[1939]: segfault at 0 ip 000000000040af1c sp 00007fff46445630 error 6 in lvpnc[400000+10000]
Dec  3 20:54:18 OptiPlex-780 dbus[1383]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Dec  3 20:54:18 OptiPlex-780 dbus[1383]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Dec  3 20:54:18 OptiPlex-780 rtkit-daemon[4662]: Successfully called chroot.
Dec  3 20:54:18 OptiPlex-780 rtkit-daemon[4662]: Successfully dropped privileges.
Dec  3 20:54:18 OptiPlex-780 rtkit-daemon[4662]: Successfully limited resources.
Dec  3 20:54:18 OptiPlex-780 rtkit-daemon[4662]: Running.
Dec  3 20:54:18 OptiPlex-780 rtkit-daemon[4662]: Canary thread running.
Dec  3 20:54:18 OptiPlex-780 rtkit-daemon[4662]: Watchdog thread running.
Dec  3 20:54:22 OptiPlex-780 rtkit-daemon[4662]: Successfully made thread 4660 of process 4660 (n/a) owned by '1000' high priority at nice level -11.
Dec  3 20:54:22 OptiPlex-780 rtkit-daemon[4662]: Supervising 1 threads of 1 processes of 1 users.
Dec  3 20:54:23 OptiPlex-780 rtkit-daemon[4662]: Successfully made thread 4708 of process 4660 (n/a) owned by '1000' RT at priority 5.
Dec  3 20:54:23 OptiPlex-780 rtkit-daemon[4662]: Supervising 2 threads of 1 processes of 1 users.
Dec  3 20:54:23 OptiPlex-780 rtkit-daemon[4662]: Successfully made thread 4710 of process 4660 (n/a) owned by '1000' RT at priority 5.
Dec  3 20:54:23 OptiPlex-780 rtkit-daemon[4662]: Supervising 3 threads of 1 processes of 1 users.
Dec  3 20:54:23 OptiPlex-780 dbus[1383]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Dec  3 20:54:23 OptiPlex-780 blueman-mechanism: Starting blueman-mechanism 
Dec  3 20:54:23 OptiPlex-780 dbus[1383]: [system] Successfully activated service 'org.blueman.Mechanism'
Dec  3 20:54:23 OptiPlex-780 blueman-mechanism: loading RfKill 
Dec  3 20:54:23 OptiPlex-780 blueman-mechanism: loading Network 
Dec  3 20:54:23 OptiPlex-780 blueman-mechanism: loading Config 
Dec  3 20:54:23 OptiPlex-780 blueman-mechanism: loading Ppp 
Dec  3 20:54:28 OptiPlex-780 kernel: [ 8922.952289] usb 2-5.6: 3:1: cannot get freq at ep 0x82
Dec  3 20:54:33 OptiPlex-780 kernel: [ 8927.952265] usb 2-5.6: 3:1: cannot get freq at ep 0x82
Dec  3 20:54:38 OptiPlex-780 kernel: [ 8933.080236] usb 2-5.6: 3:1: cannot get freq at ep 0x82
Dec  3 20:54:43 OptiPlex-780 rtkit-daemon[4662]: Successfully made thread 4718 of process 4660 (n/a) owned by '1000' RT at priority 5.
Dec  3 20:54:43 OptiPlex-780 rtkit-daemon[4662]: Supervising 4 threads of 1 processes of 1 users.
Dec  3 20:54:43 OptiPlex-780 kernel: [ 8938.080211] usb 2-5.6: 3:1: cannot get freq at ep 0x82
Dec  3 20:54:43 OptiPlex-780 rtkit-daemon[4662]: Successfully made thread 4720 of process 4720 (n/a) owned by '1000' high priority at nice level -11.
Dec  3 20:54:43 OptiPlex-780 rtkit-daemon[4662]: Supervising 5 threads of 2 processes of 1 users.
Dec  3 20:54:43 OptiPlex-780 pulseaudio[4720]: [pulseaudio] pid.c: Daemon already running.
Dec  3 20:54:44 OptiPlex-780 rtkit-daemon[4662]: Successfully made thread 4722 of process 4722 (n/a) owned by '1000' high priority at nice level -11.
Dec  3 20:54:44 OptiPlex-780 rtkit-daemon[4662]: Supervising 6 threads of 3 processes of 1 users.
Dec  3 20:54:44 OptiPlex-780 pulseaudio[4722]: [pulseaudio] pid.c: Daemon already running.
Dec  3 20:54:53 OptiPlex-780 blueman-mechanism: Exiting 
```

/var/log/auth.log:
```
Dec  3 20:54:10 OptiPlex-780 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Dec  3 20:54:10 OptiPlex-780 lightdm: pam_unix(lightdm:session): session opened for user scott by (uid=0)
Dec  3 20:54:10 OptiPlex-780 kernel: [ 8905.131894] systemd-logind[1792]: New session c8 of user scott.
Dec  3 20:54:10 OptiPlex-780 kernel: [ 8905.131913] systemd-logind[1792]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Dec  3 20:54:10 OptiPlex-780 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Dec  3 20:54:11 OptiPlex-780 gnome-keyring-daemon[4368]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Dec  3 20:54:11 OptiPlex-780 gnome-keyring-daemon[4368]: message repeated 2 times: [ couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files]
Dec  3 20:54:14 OptiPlex-780 gnome-keyring-daemon[4368]: The SSH agent was already initialized
Dec  3 20:54:14 OptiPlex-780 gnome-keyring-daemon[4368]: The GPG agent was already initialized
Dec  3 20:54:14 OptiPlex-780 gnome-keyring-daemon[4368]: The Secret Service was already initialized
Dec  3 20:54:14 OptiPlex-780 gnome-keyring-daemon[4368]: The PKCS#11 component was already initialized
Dec  3 20:54:16 OptiPlex-780 polkitd(authority=local): Registered Authentication Agent for unix-session:c8 (system bus name :1.76 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec  3 20:56:01 OptiPlex-780 CRON[4737]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec  3 20:56:01 OptiPlex-780 CRON[4737]: pam_unix(cron:session): session closed for user root
```

/var/log/kern.log:
```
Dec  3 20:54:15 OptiPlex-780 kernel: [ 8910.099258] lvpnc[1939]: segfault at 0 ip 000000000040af1c sp 00007fff46445630 error 6 in lvpnc[400000+10000]
Dec  3 20:54:28 OptiPlex-780 kernel: [ 8922.952289] usb 2-5.6: 3:1: cannot get freq at ep 0x82
Dec  3 20:54:33 OptiPlex-780 kernel: [ 8927.952265] usb 2-5.6: 3:1: cannot get freq at ep 0x82
Dec  3 20:54:38 OptiPlex-780 kernel: [ 8933.080236] usb 2-5.6: 3:1: cannot get freq at ep 0x82
Dec  3 20:54:43 OptiPlex-780 kernel: [ 8938.080211] usb 2-5.6: 3:1: cannot get freq at ep 0x82
```

/var/log/apport.log:
```
ERROR: apport (pid 4598) Wed Dec  3 20:54:16 2014: called for pid 1939, signal 11, core limit 0
ERROR: apport (pid 4598) Wed Dec  3 20:54:16 2014: executable: /usr/bin/lvpnc (command line "/usr/bin/lvpnc")
ERROR: apport (pid 4598) Wed Dec  3 20:54:16 2014: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 4598) Wed Dec  3 20:54:16 2014: wrote report /var/crash/_usr_bin_lvpnc.0.crash
```


Let me know your thoughts. Thanks

---

### Post by Bashing-om on 2014-12-03
sremick; Yep;

Agreed, authorization to /home is good.

What is 'lvpnc' ? A quick look about and I find nothing on it ?

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sremick on 2014-12-03
> **Bashing-om said:**
> sremick; Yep;

Agreed, authorization to /home is good.

What is 'lvpnc' ? A quick look about and I find nothing on it ?
Looks like it's part of a VPN Autoconnect utility that was once installed. It never did really work, and could probably be removed, but I don't think that's the issue. It's been installed for a long time (and been broken).

[http://sourceforge.net/projects/vpnautoconnect/files/](http://sourceforge.net/projects/vpnautoconnect/files/)

I tried removing it and rebooting, then tried logging in. No change, so my guess was correct. 

It still takes several *minutes* (18mins I think? I'll time it next time) after entering in the volume decryption password ("cryptsetup: sda5_crypt set up successfully") to then get to the DE login prompt. During this time the HDD is active steadily (although not loudly) and I cannot ping the box. Right before the GUI login appears the HDD switches to audible thrashing then the login box appears a few moments after. syslog doesn't get written to until right before the login box so I wonder if it's something to do with the disk encryption. This issue is new since the inode episode, but the larger issue is not being able to log in. However the timing of both issues are tied to the same incident, so I'm confident they are related.

---

### Post by Bashing-om on 2014-12-04
sremick; Humm ...

I have no experience with encryption. I have no idea how that process to access the file system works. 
Let's await others to chime in here and see what is advised in this instance.

[INDENT][INDENT]things I have no need to know
[/INDENT][/INDENT]

---

