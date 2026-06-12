---
title: "timeoutd errors"
date: 2008-05-01
forum: General Help
---

### Post by theparanoidone on 2008-05-01
Hi,

I need a way to timeout physical console terminal sessions, as well as ssh sessions.  So far, timeoutd seems to help

Here is my /etc/timeouts:
```

Al:pts*,tty*:*:*:60:0:0:0

```

However... if I log into the console... it *will* log me out; however, from that point forward... it will continue to kill the getty terminal indefinitely eventhough I am not logged in.

Syslog shows errors:
```

May  1 18:08:51 serviced1 timeoutd[4778]: User john exceeded idle limit (idle for 1 minutes, max=1). 
May  1 18:08:51 serviced1 timeoutd[4778]: chk_ssh(): PID 4864 does not exist. Something went wrong. Ignoring.
May  1 18:10:01 serviced1 timeoutd[4778]: User john exceeded idle limit (idle for 1 minutes, max=1). 
May  1 18:10:01 serviced1 timeoutd[4778]: chk_ssh(): PID 4864 does not exist. Something went wrong. Ignoring.

```

How do I make these errors go away?

---

### Post by theparanoidone on 2008-05-02
bump bump, any ideas?

---

### Post by theparanoidone on 2008-05-05
any ideas?

---

### Post by ecowan on 2010-01-27
I'm having the same problem on one of my systems, with the karmic koala release. Another one with jaunty works fine. Did you ever figure out a fix?
Thanks. - Erny

---

### Post by theparanoidone on 2010-01-27
This is what I have settled on:
```

Al:pts*,tty*:*:*:15:0:0:0

```


As a side note... I don't know where I read this... but the timeoutd package installed on Ubuntu Server 8.04 is slightly broken in the since that it will die occasionally.

we'll log in after a week or so... and notice that the timeoutd daemon is just not runnning

we have to restart it via /etc/init.d/timeoutd restart

I read somewhere that it's caused by some bunk code in the timeoutd package.  Think I remember reading it on launchpad and they said that they would not fix it in Ubuntu 8... but later releases of Ubuntu 9 and etc.

I think if you check, the latest version available on timeoutd on Ubuntu 8 is older than what the current codebase for timeoutd is. I suppose you could manually install a later version.. dpkg... etc.

Sorry I don't have more info on this.

Other than that it's a great simple lightweight tool.

---

