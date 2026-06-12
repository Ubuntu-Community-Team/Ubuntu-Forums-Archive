---
title: "/etc/securetty is MIA"
date: 2021-10-06
forum: General Help
---

### Post by psychohermit on 2021-10-06
Running ubuntu 20.04 LTS

From auth.log

```

Oct  3 05:09:02 Psycho gdm-password]: pam_unix(gdm-password:auth): Couldn't open /etc/securetty: No such file or directory
Oct  3 05:09:10 Psycho gdm-password]: pam_unix(gdm-password:auth): Couldn't open /etc/securetty: No such file or directory

```

i don't know what /etc/securetty is but it seems to be missing.

Thanks in advance.
--glenn

---

### Post by dain-bramage on 2021-10-07
You have to edit

```
[COLOR=#232629][FONT=ui-monospace]/etc/pam.d/common-auth[/FONT][/COLOR]
```

and remove

```
[COLOR=#232629][FONT=ui-monospace]nullok_secure[/FONT][/COLOR]
```

from the line

```
auth [success=1 default=ignore] pam_unix.so nullok_secure
```

---

### Post by TheFu on 2021-10-07
I think securetty is an extra option to prevent X11 security issues on remote terminals. It is intended to provide extra protections when root is used at a tty login - so never for a GUI. It appears to be part of a snap package now in core, core18 and core20 snaps.

The pam_securetty manpage says, 
> pam_securetty - Limit root login to special devices

Since root logins aren't part of Ubuntu, nobody should be logging in as root, so the specific list of securettys in /etc/securetty wouldn't be useful.

That's my best guess.

---

### Post by deadflowr on 2021-10-07
It's a known issue.
Or at least an issue which has been addressed in a report.
See: [https://bugs.launchpad.net/ubuntu/+source/pam/+bug/1860826]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/1860826")
which explains what's going on and how to fix if needed or wanted.

---

