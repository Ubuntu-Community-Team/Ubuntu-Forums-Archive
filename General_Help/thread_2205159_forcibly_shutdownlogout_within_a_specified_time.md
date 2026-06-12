---
title: "forcibly shutdown/logout within a specified time"
date: 2014-02-12
forum: General Help
---

### Post by evilweed on 2014-02-12
Hello!

Let me begin with saying that I am somewhat new to this forum, and if I missed a thread adressing this topic, or this is posted in the wrong forum please feel free to change it/point me in the right direction. However, I have looked, and havent found anything so far. Here goes...

How do you forcibly shutdown or logout a user within a specified time(for example within 2 hours/120minutes) in a way that the user cannot pause or cancel the process?

---

### Post by tgalati4 on 2014-02-12
How you do it depends on how your user is logged in.  What version of linux?

You can see your user's processes:

tgalati4@Mint14-Extensa ~ $ ps aux | grep tgalati4
tgalati4   869  0.0  0.0  22600  1312 pts/0    R+   07:14   0:00 ps aux
tgalati4   870  0.0  0.0  13584   936 pts/0    S+   07:14   0:00 grep --colour=auto tgalati4
tgalati4  1608  0.0  0.1 291312  2916 ?        Ssl  Jan28   0:02** x-session-manager**
tgalati4  1680  0.0  0.0  12572    32 ?        Ss   Jan28   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager

Then you can send the termination flag (signal 15) to that process after 2 hours and it should unceremoniously kick the user off.

Something like: (pseudo code--all errors are yours)

(In root shell)at now + 2 hours kill -15 1608

To get get the process id (PID) you would need to use a grep/gawk/sed script to pull out the PID for a specific user.

There is probably a cleaner way to do this, but I am not awake yet.

If you are managing a machine with several users, you could modify the login-script for users to use the *timeout* command.

```
man timeout
```

You would select an appropriate process (like their xsession process) and apply a 2-hour limit.  Again, killing processes this way would probably cause loss of work for that session.  A better method would be to simply send warnings (using *notify-send*) when a key process exceeds 2 hours of real time.

---

