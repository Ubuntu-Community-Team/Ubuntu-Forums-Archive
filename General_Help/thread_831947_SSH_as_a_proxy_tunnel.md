---
title: "SSH as a proxy tunnel"
date: 2008-06-17
forum: General Help
---

### Post by jethro10 on 2008-06-17
Hi,
I've given up and am asking for help.

I previously had a Qnap NAS which is linux based and I could use Putty from my windows PC at work to connect to home, via ssh, then break out to the net.
I also have an Ubuntu PC at work and that worked fine also, with this command line :-
ssh -D 8080 user@host
So I set Firefox to use 127.0.0.1 port 8080 for all protocols ands its fine.

Replace Qnap with a homebuild Ubuntu server (actually just the normal desktop version!) and it now fails.
I can tunnel to it, run X programs on it from my Ubuntu PC at work etc.
But when I use firefox (both windows and linux) from work, it gives no error messages but gives a white screen as if there is no data for FF to display. When I stop the tunnel, FF gives a correct message that the proxy is not found.

The 'Server' can access the net if I run a VNC session to it, and is getting it's updates ok so it's not that.

Everything else, routers etc are unchanged and the Server is on the same IP address the Qnap NAS was. it's not mac address blocking or anything like that.

Any ideas?

Jeff

---

### Post by jethro10 on 2008-07-02
> **jethro10 said:**
> Hi,

So I set Firefox to use 127.0.0.1 port 8080 for all protocols ands its fine.


Jeff
And that was my error.
Had to be set for Socks only and it worked. Did I miss it earlier, or did Ubuntu do it differently compared to Qnap....

J

---

### Post by kevdog on 2008-07-02
wormser did a how-to on this in the tutorials and tips section.  I don't remember the settings but I believe only SOCKS5 had to be selected.

---

