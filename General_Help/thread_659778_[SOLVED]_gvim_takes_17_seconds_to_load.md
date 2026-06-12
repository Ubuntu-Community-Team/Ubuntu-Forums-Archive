---
title: "[SOLVED] gvim takes 17 seconds to load"
date: 2008-01-06
forum: General Help
---

### Post by twice on 2008-01-06
About a week ago, a number of applications suddenly began taking a long time to start.  gvim has been affected the worst, and consistently waits almost exactly 17 seconds before the window appears.  vim  takes about 7 seconds in a gnome-terminal, but is instantaneous when run in an actual console.  gnome-terminal itself takes about 8 seconds to start, as does gedit.

top and gnome-system-monitor don't show a dent in cpu time or memory usage while this happens, and i haven't made any changes to my system recently that could be causing this.  I'm running Gutsy.

I'd really appreciate any help figuring this out.

---

### Post by webno on 2008-01-06
Try starting gvim from the terminal. You might see some messages being logged while the application is starting up.

If so. It might be helpfull to paste them in here.

---

### Post by twice on 2008-01-06
> **webno said:**
> Try starting gvim from the terminal. You might see some messages being logged while the application is starting up.

No, sadly, there's nothing on the terminal..  I've also checked all the logs I could think of, but I haven't found anything.

---

### Post by twice on 2008-01-08
Okay, there's a new symptom that I think might be related.  nautilus is slow to open as well, but it only seems to happen when opening my home partition (ext3, if it matters)..  All other partitions open instantly, including other partitions on the same physical drive (which is only a few months old).  Also, I've started getting "no space left on device" messages on my home partition, despite df showing a dozen gigs left.

Any ideas or suggestions?  Could a screwed-up filesystem be causing the delays?

---

### Post by twice on 2008-01-18
Running vim in gnome-terminal with the -X option -- "don't connect to the X server" -- completely removes the delay.

Also, oddly enough, running gvim with -X shaves off about 10 seconds, even though it doesn't appear to actually do anything to gvim's behavior or appearance.

---

### Post by proy on 2008-01-27
One of the reason why gnome applications can take too long is the host name. Please check the /etc/hosts file to see if 127.0.0.1 has both localhost and the hostname that you assigned for the system. Hope this helps.

---

### Post by twice on 2008-01-27
> **proy said:**
> One of the reason why gnome applications can take too long is the host name. Please check the /etc/hosts file to see if 127.0.0.1 has both localhost and the hostname that you assigned for the system. Hope this helps.

That did it!  Thank you!

---

