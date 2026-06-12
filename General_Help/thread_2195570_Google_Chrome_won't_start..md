---
title: "Google Chrome won't start."
date: 2013-12-25
forum: General Help
---

### Post by SlickStretch on 2013-12-25
I just installed google-chrome-stable on a fresh install of Lubuntu 13.10.  The install went fine with no errors.  When I try to start Chrome, I get a popup window that says "System Program Problem Detected." I click OK and get another window that says "Sorry, Ubuntu 13.10 has experienced an internal error." After that window, nothing.

---

### Post by monkeybrain20122 on 2013-12-25
Did you reboot and see if it works?

If it still does not work start chrome in the terminal and see if there is any error message, just type in the terminal
```
google-chrome
```

---

### Post by grier-devon on 2013-12-25
Google has been having a hard time keeping Chrome running smoothly on Ubuntu which includes Lubuntu. I would remove Chrome
```
sudo apt-get remove google-chrome-stable
```

The install again and let us know if that works.

---

### Post by jpascoe2 on 2014-11-12
Mine is also not starting in 14.

```
jason@XPredator:~$ google-chrome
The setuid sandbox is not running as root. Common causes:
  * An unprivileged process using ptrace on it, like a debugger.
  * A parent process set prctl(PR_SET_NO_NEW_PRIVS, ...)
Failed to move to new namespace: PID namespaces supported, Network namespace supported, but failed: errno = Operation not permitted
```

I reinstalled but havent tried to uninstall and reinstall yet. Will try that next.

---

### Post by jpascoe2 on 2014-11-12
Same error after uninstall and reinstall

---

### Post by oldos2er on 2014-11-12
Hi jpascoe2, please start a new thread for your problem since this one's nearly a year old and concerns a no-longer-supported version of Ubuntu.

---

