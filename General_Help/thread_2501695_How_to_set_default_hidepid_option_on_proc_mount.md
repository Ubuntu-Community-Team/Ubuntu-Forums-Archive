---
title: "How to set default hidepid option on /proc mount"
date: 2024-10-17
forum: General Help
---

### Post by Kevin_Rahe on 2024-10-17
In my Ubuntu 22.04 virtual private server (VPS), /proc gets mounted with hidepid=2 by default. That setting is incompatible with one of my applications, which needs hidepid=0. Does anyone know how to get /proc to mount with hidepid=0 by default? Adding an entry for /proc to /etc/fstab doesn't do it.

---

### Post by 1fallen on 2024-10-17
> **Kevin_Rahe said:**
> Adding an entry for /proc to /etc/fstab doesn't do it.

I just need some clarity here, so this did not work?
fstab:
```
proc /proc proc defaults,hidepid= 0 0
```
It should have....
EDIT:
```
[FONT=monospace][COLOR=#000000]sudo mount -o remount,rw,hidepid=0 /proc[/COLOR]



```
[/FONT]

---

### Post by Kevin_Rahe on 2024-10-17
If I add the following to /etc/fstab:
```
proc /proc proc defaults,hidepid=0 0 0
```
and then do (as root):
```
mount -o remount /proc
```
and then run the mount command with no parameters, the output will include the following:
```
proc on /proc type proc (rw,relatime)
```
But then if I wait a couple minutes and run the mount command again, I will get:
```
proc on /proc type proc (rw,relatime,hidepid=2)
```
which is also the same thing I get initially after a restart of the VPS, regardless of what is in /etc/fstab.

---

### Post by Kevin_Rahe on 2024-10-18
I'm strongly suspecting that the hypervisor is sticking its finger in the pie and trying to enforce a policy of hidepid=2. I just ran across [this article]("https://access.redhat.com/solutions/6704531") that raises multiple issues with using the hidepid=2 setting. While the article is regarding Red Hat Linux, the issues would likely apply to any Linux distro.

---

### Post by 1fallen on 2024-10-18
At first I suspected a bug in the kernel, but that link now shows>>>"hidepid=1 or hidepid=2 are not compatible with how *systemd* manages the system."
> Previous issue leads to the second problem. If hidepid= option is used then some system services like (*PolicyKit* or *D-Bus*)  are not able to query information about the clients which are  connecting to them. This is because all these services run as  non-privileged (i.e. euid != 0) and hence don't see needed information in /proc/[pid] directory of the client, unless the client runs under the same *uid* which is never the case (at least for *PolicyKit* and *D-Bus*).
 Last problem, that we would like to highlight is potential information leak and false sense of security that hidepid= provides. Information (PID numbers, command line arguments, UID and GID) about system services are tracked by *systemd*. By default this information is available to everyone to read via *systemd*'s D-Bus interface. When hidepid= option is used *systemd* doesn't take it into consideration and still exposes all this information at the API level.



EDIT You may want to read this over: [URL="https://github.com/Kicksecure/security-misc"]https://github.com/Kicksecure/security-misc

[/URL]```
[FONT=monospace][COLOR=#000000] mount | grep ^proc [/COLOR]
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime,hidepid=invisible)



```
```
[/FONT][FONT=monospace][COLOR=#000000]loginctl show-session $XDG_SESSION_ID --property=Active [/COLOR]
Active=yes

```


[/FONT]

---

### Post by Kevin_Rahe on 2024-10-21
The information on that page about the proc-hidepid.service sounded interesting, but I find no such service defined on my server.

---

