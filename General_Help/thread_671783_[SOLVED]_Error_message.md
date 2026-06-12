---
title: "[SOLVED] Error message"
date: 2008-01-18
forum: General Help
---

### Post by kens8 on 2008-01-18
I'm getting this error message when starting a few programs:

```
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 476 error_code 11 request_code 148 minor_code 5)
```

A couple of the programs I'm getting this with are VLC and Python (when starting Icepodder).

I have an Athlon 64 3000, 1 gb RAM, 80 and 120 gig hard drives.  Resources shouldn't be a problem for these programs.  I never had a problem until today.  Any ideas?

---

### Post by zvacet on 2008-01-19
```
df -h
```

Post it here.

---

### Post by dabang on 2008-01-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See what "xserver-xorg-core" package you have installed. If it's 1.3.0.0.dfsg-12ubuntu8.1, than this is causing the trouble. Just update to latest version. (should be ...ubuntu8.3).

---

### Post by kens8 on 2008-01-19
It was the x-server.  I guess the update last week screwed with java and python.  Anyway, they released another update this morning and it fixed the problem.

---

