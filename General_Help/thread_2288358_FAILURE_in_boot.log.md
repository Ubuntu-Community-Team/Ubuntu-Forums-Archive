---
title: "FAILURE in boot.log"
date: 2015-07-26
forum: General Help
---

### Post by lisa374 on 2015-07-26
The following is an excerpt from my prusual of various files; bolded text are the important parts.

#[SIZE=2]From the boot.log[/SIZE]
 [SIZE=2]**[FAILED] Failed to start /etc/rc.local Compatibility.**[/SIZE]
 [SIZE=2]See "systemctl status rc-local.service" for details.[/SIZE]
 
 
 [SIZE=2]#From the “systemctl status rc-local.service”[/SIZE]
 [SIZE=2]userhost:/etc$ systemctl status rc.local[/SIZE]
 &#9679; [SIZE=2]rc-local.service - /etc/rc.local Compatibility[/SIZE]
    [SIZE=2]Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)[/SIZE]
    [SIZE=2]Active: failed (Result: exit-code) since Sun 2015-07-26 11:56:17 EDT; 2h 32min ago[/SIZE]
   [SIZE=2]Process: 812 ExecStart=/etc/rc.local start (code=exited, status=127)[/SIZE]
 [SIZE=2]Jul 26 11:56:17 userhost systemd[1]: Starting /etc/rc.local Compatibility...[/SIZE]
 [SIZE=2]Jul 26 11:56:17 userhost rc.local[812]:** /etc/rc.local: 13: /etc/rc.local: /sbin/modprob: not found**[/SIZE]
 [SIZE=2]Jul 26 11:56:17 userhost systemd[1]: **rc-local.service: control process exited, code=exited status=127**[/SIZE]
 [SIZE=2]Jul 26 11:56:17 userhost systemd[1]: Failed to start /etc/rc.local Compatibility.[/SIZE]
 [SIZE=2]Jul 26 11:56:17 userhost systemd[1]: Unit rc-local.service entered failed state.[/SIZE]
 [SIZE=2]Jul 26 11:56:17 userhost systemd[1]: rc-local.service failed.[/SIZE]
 
 
 [SIZE=2]userhost:/sbin$ ls -al modprobe[/SIZE]
 [SIZE=2]**lrwxrwxrwx 1 root root 9 Jun 20 14:26 modprobe -> /bin/kmod**[/SIZE]
 
 
 [SIZE=2]userhost:/bin$ ls -al kmod[/SIZE]
 [SIZE=2]**-rwxr-xr-x 1 root root 158720 Apr  6 16:23 kmod**[/SIZE]
 
 
 [SIZE=2]I'm not sure what “/etc/rd.local: /sbin/modprob: not found” signifies since it clearly exists and the permissions seem to indicate “universal” access.

My OS: Ubuntu 3.19.0-23-generic #24-Ubuntu SMP Tue Jul 7 18:52:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux; with the latest update as of Jul 26.

Anyone know what's up
[/SIZE]

---

### Post by Habitual on 2015-07-27
The message is "/sbin/modprob:" not "/sbin/modprob**[COLOR=#ff0000]e[/COLOR]**:".
```
sudo grep -wn modprob /etc/rc.local
```

-w is whole word, so it greps only modprob and ignores modprobe
Looks like line 13.
-n is line number if found.

---

