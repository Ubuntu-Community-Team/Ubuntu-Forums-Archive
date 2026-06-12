---
title: "what exactly is gksu doing when it echoes this?"
date: 2008-04-04
forum: General Help
---

### Post by ibuclaw on 2008-04-04
Examine this for a moment:
```

gksu a-program
No ask_pass set, using default!
xauth: /tmp/libgksu-RMVxfp/.Xauthority
STARTUP_ID: gksu/a-program/29178-0-fredbuntu_TIME11576185
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: a-program
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-RMVxfp/.Xauthority
xauth_env: /home/usernamer/.Xauthority
dir: /tmp/libgksu-RMVxfp

```

Can someone explain what it claims to be doing?

Cos at a first look, it seems to be exploiting a security hole to ask the user for a password.

If that is the case, couldn't someone just as easily create a piece of malware that consistently asks for a users password this way?
And if the user is dumb enough to enter his password, (granted that he is a sudo user) potentially infect his whole system?

Just wondering out of curiosity... And concern.

Regards
Iain

---

### Post by gsmanners on 2008-04-04
So, "sudo -p" is a security hole?

If I created some malware that exploited this "hole" and posted it on launchpad, I'm sure someone would notice.

---

### Post by ibuclaw on 2008-04-04
Ok, just adding in carriage returns to show what I see in the terminal.
> **tinivole said:**
> Examine this for a moment:
```

buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...

```


I suppose its the large number of S's and the "**brute force ended. Yeah we're in...** part.
I may be wrong. Or it may be bad use of using "echo" or "printf", but it had me thinking that its exploiting a buffer overflow within sudo...

Again, I was just puzzled by this bizarre printout in the console.

Regards
Iain

---

