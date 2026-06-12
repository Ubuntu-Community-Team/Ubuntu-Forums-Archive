---
title: "changing init levels in upstart on edgy"
date: 2006-11-15
forum: General Help
---

### Post by xdevnull on 2006-11-15
I'm new to Ubuntu/Edgy, and I'm trying to understand the new init replacement, Upstart.  Specifically, in the past when I wanted to do some kind of maintenance, I could ctrl-alt Fnum, go to a command line, login as root and type- init 3 -to go to init stage 3 i.e. shutting down X, then type init 5 and restart it.  I also could go to init 1, single user mode, for some maintenance and go init 5 to get back to everything without a restart.  

Now I can login as root on another tty, and when I type init 3, nothing much seems to happen, and then if I type init 5, it seems to be thinking about something, but the command line doesn't reappear

```

user@host:~$ init 3
init 3
user@host:~$ init 5
init 5 
```

Init 6 seems to work in that it reboots the computer.  So - I'm wondering how to do this, since edgy doesn't use init anymore, and the old commands don't appear to work.  How does one get to init 3 and init 1, or their equivalents?

Thanks

---

### Post by po0f on 2006-11-15
xdevnull,

It's a bit of a PITA, but to get into single-user mode, reboot and pass "single" as a kernel parameter.  (Hit ESC when you see the GRUB startup message, highlight the relevant kernel and press "e" (for edit), highlight the kernel line and press "e", and add "single" to the end.)

---

### Post by xdevnull on 2006-11-17
Thanks for the info - but - 

[RANT]Holy Crap!!! Is that really the only way?!  Reboot?!  Really?!  I thought I was using linux...[/RANT]

Is this because of upstart, or has Ubuntu always been that way?

Also - I think the recovery mode boots into single user mode - at least that is option attached in grub vis:

 /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single

---

