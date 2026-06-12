---
title: "unusual files in /tmp"
date: 2020-12-31
forum: General Help
---

### Post by Frank P on 2020-12-31
recently, I think it's since upgrading 16.04lts server to 18.04 these files are showing up in /tmp. They are all empty except the 2nd which contains my php error log. Any idea of what's been changed to cause this?
Thanks
Frank
```

total 104
drwxrwxrwt 24 root   root   4096 Dec 31 17:46 .
drwxr-xr-x 20 root   root   4096 Dec 12 20:53 ..
-rw-rw-r--  1 laozi  laozi     0 Dec 31 17:46 chk.txt
-rw-------  1 laozi  laozi     0 Dec 31 15:37 config-err-pU03zh
drwxrwxrwt  2 root   root   4096 Dec 31 15:35 .font-unix
drwxrwxrwt  2 root   root   4096 Dec 31 15:37 .ICE-unix
drwx------  2 laozi  laozi  4096 Dec 31 15:38 mc-laozi
drwx------  2 root   root   4096 Dec 31 15:39 mc-root
drwx------  2 laozi  laozi  4096 Dec 31 15:37 ssh-NX6O4l7h8UGw
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-apache2.service-T2PdRh
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-bolt.service-eQblwj
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-colord.service-nnnSgh
drwx------  3 root   root   4096 Dec 31 15:38 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-fwupd.service-rcAdug
drwx------  3 root   root   4096 Dec 31 15:37 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-geoclue.service-SfhQWi
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-ModemManager.service-nw7Gyh
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-switcheroo-control.service-FBUMwj
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-systemd-logind.service-goZiDg
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-systemd-resolved.service-ibu9Vh
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-systemd-timesyncd.service-F88foj
drwx------  3 root   root   4096 Dec 31 15:35 systemd-private-d9d2d1d4283e4ac8ac0547bb3c256c5e-upower.service-FCjZCi
drwxrwxrwt  2 root   root   4096 Dec 31 15:35 .Test-unix
drwx------  2 fpolan fpolan 4096 Dec 31 17:31 tracker-extract-files.1000
drwx------  2 laozi  laozi  4096 Dec 31 15:37 tracker-extract-files.1001
drwx------  2 gdm    gdm    4096 Dec 31 15:35 tracker-extract-files.125
-r--r--r--  1 gdm    gdm      11 Dec 31 15:35 .X1024-lock
-r--r--r--  1 gdm    gdm      11 Dec 31 15:35 .X1025-lock
drwxrwxrwt  2 root   root   4096 Dec 31 15:37 .X11-unix
drwxrwxrwt  2 root   root   4096 Dec 31 15:35 .XIM-unix



```

---

### Post by TheFu on 2020-12-31
systemd stuff.

---

### Post by Frank P on 2021-01-01
okay, next question
How do I find out why they're there and is the some way to control location, permissions, etc. They have broken my php custom exception handler ; it used to write to /tmp, now it ends up inside one of those files./ Its a nuisance to have to use sudo to access them and they're a little long to write

---

### Post by TheFu on 2021-01-01
Systemd is the MCP (Tron reference), so you'll want to change your "php custom exception handler" in some way.

---

### Post by Frank P on 2021-01-01
okay
Thanks

---

### Post by TheFu on 2021-01-01
Why are you writing filenames? Use tab-completion and select/paste in your terminals.

As for the permissions, your program should manage those for whatever you need.  I don't understand any of this really.

Logs don't belong in /tmp/. They belong in /var/log/ and a logrotate setup should be included so logs don't get too large and are removed as needed. /etc/logrotate.d/ has lots of examples.

When we need a temporary file in /tmp, make it /tmp/{app-name}-{random}.tmp or something like that. Test that the file doesn't already exist before using it. If it does, create a new temporary file and use that.  Be certain to remove these files when they aren't needed any more.  The user and group and permissions should be set once the file is created.  Probably something like process-owner, shared-group, 640 would be reasonable. Add your userid into the shared-group so you have read-access.  Be cause /tmp/ has the sticky bit set (that's the chmod +t ), only the userid that created the file there can remove it.  Since Linux systems can remain running for months, you'll want not to be lazy on keeping the temporary files clean and deleted when not used anymore. Catch any signals, like the kill signal in your programs, so cleanup is performed.

Or just use syslog. There must be libraries for php for syslog integration, since there are for every other language. No need to reinvent the log-wheel.

---

### Post by Frank P on 2021-01-01
a lot to comment on , but here goes:

---

### Post by Frank P on 2021-01-01
oops, pushed the wrong button a minute ago. here's the message

a lot to comment on , but here goes:

file names: I'm talking about those extremely long file names created by systemd. I don't think tab completion would help much. Anyway know I know what those files are, I can ignore them.
permissions: again talking about those systemd files in /tmp; all owned by root.
logs: program error & exception logs belong where the programmer wants them to be; definitely not in system logs. I've moved them out of /tmp so problem is gone. As far as the rest of the comments go, I know how to handle file checks & user permissions for the files I want to use. I don't want/need to mess with the systemd output in /tmp
Thanks
Frank

---

### Post by TheFu on 2021-01-01
I agree with most above.

For ```
cd systemd-private-361112f78e7b4fa789be385fd5db0ea5-colord.service-ybrgsj/
``` for the colord.service.
I typed:
```
cd sy{tab}co{tab}{enter}
```
Pretty efficient.
BTW, I have no idea what colord is for and I think systemd is a solution to a problem I've never had.

In a script/program, I'd use globbing with wildcard patterns.  systemd-private-*-colord.service-* and check that only 1 match returned.

There are plans to make linux system log files more restrictive for security reasons.

---

### Post by Frank P on 2021-01-01
okay, that tab stuff is pretty impressive.
As for actually accessing those systemd files, now I know I don't need them I feel a lot better. The file names I use are a lot shorter :-) 

Thanks
Frank

---

### Post by TheFu on 2021-01-01
Between systemd and snaps, we have a bunch of weird stuff showing up outside places they belong these days.  Don't get me started about 'df' output.

---

### Post by Frank P on 2021-01-01
I really miss 16.04 LTS :-)
I'll mark this solved
Thanks for your help
Frank

---

