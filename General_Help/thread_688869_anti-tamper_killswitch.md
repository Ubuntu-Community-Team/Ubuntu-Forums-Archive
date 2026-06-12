---
title: "anti-tamper killswitch?"
date: 2008-02-05
forum: General Help
---

### Post by leftorvo on 2008-02-05
Does anyone know of a program/software that exists that will detect physical tampering with a computer (for example if someone tried to unlock the screen after it had been locked and put in the wrong password) and execute some commands, like to shut the computer down?

I dont know what this would be called though, but it would be a good idea if someone hasn't done it already. it wouldnt even need to be fancy or complicated.

---

### Post by pointone on 2008-02-06
This can be done with the PAM module pam_exec.

```
man pam_exec
```

However, making it run after login failures requires some understanding of PAM.

For the most basic functionality, you could simply edit /etc/pam.d/common-auth and change it to the following:

```
auth    sufficient    pam_unix.so nullok_secure
auth    required      pam_exec.so shutdown -h now
```

This will cause the system to shutdown after ANY failed password attempt that uses PAM. For more control, you could instead have pam_exec run a custom script that, say for example, uses a counter method (so it only shuts down after 5 failed logins), or you could edit each application's PAM configuration separately. Add the pam_exec line to /etc/pam.d/gnome-screensaver, for instance, to only have it affect the locked screen.

See [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html) for more information.

---

### Post by euler_fan on 2008-02-06
If you just want to annoy someone you can always up the delay between login attempts to something silly. Simply shutting down will force them to reboot, which is equivalent, and at least in Gusty can be done under the Admin->Login Screen->Security. I want to say the default is one second. At 120 seconds it would start getting faster for an attacker to reboot rather than wait for the system to reset for another try.

But then if you botch your password once or twice (or four or five as I sometimes do) this gets really annoying really fast for, well, YOU.

On the other hand, if someone has physical access to your machine (and knows what they're doing), a kill-switch isn't going to do much good anyway.

---

### Post by leftorvo on 2008-02-07
thanks a lot to both of you, I really appreciate it - looks like some useful information that ill look in to (I didn't think anyone would even reply, let alone give me perfect answers) :)

EDIT: the pam method gave this error when testing it and putting in the wrong password:

```
shutdown failed: exit code 2
```

I'm googling now - its odd, any command there does that (like vlc).

---

