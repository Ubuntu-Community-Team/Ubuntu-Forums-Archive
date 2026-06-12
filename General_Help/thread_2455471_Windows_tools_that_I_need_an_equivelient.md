---
title: "Windows tools that I need an equivelient"
date: 2020-12-20
forum: General Help
---

### Post by kingpenguin on 2020-12-20
Hello Everyone,

I normally work on windows and I have a few tools that I use almost all of the time so help me better understand what is going on. I am looking for an equivalent for all of these tools.
[LIST=1]
[*]procmon (I know there is a procmon clone being created by Microsoft but I would rather something in the software store. I have also tried out htop strace but I am not 100% sure this is what I am looking for as I was playing around with an application and almost no events were recorded except the web browser woke up)
[*]Process explorer with a process tree to understand what processes called each other.
[*]tcpview (I know there is wireshark but this seems overkill just to see what connections have been made. I am not needing to see all of the traffic just connection attempts in a easy readable format)
[/LIST]

---

### Post by dragonfly41 on 2020-12-20
I recommend adding this GUI tool .. [Stacer]("https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,%2Drepository%20ppa%3Aoguzhaninan%2Fstacer")

There are dashboards for all three of your scenarios .. and more.

Then I would look at zenmap.   ```
sudo -H zenmap
``` .. scan localhost

There are many others of course.

---

### Post by TheFu on 2020-12-20
> **kingpenguin said:**
> Hello Everyone,

I normally work on windows and I have a few tools that I use almost all of the time so help me better understand what is going on. I am looking for an equivalent for all of these tools.
[LIST=1]
[*]procmon (I know there is a procmon clone being created by Microsoft but I would rather something in the software store. I have also tried out htop strace but I am not 100% sure this is what I am looking for as I was playing around with an application and almost no events were recorded except the web browser woke up)
[*]Process explorer with a process tree to understand what processes called each other.
[*]tcpview (I know there is wireshark but this seems overkill just to see what connections have been made. I am not needing to see all of the traffic just connection attempts in a easy readable format)
[/LIST]

I have no clue what procman does. Doesn't exist on Windows here.  Looks like top with a little extra data.  That extra data is easily access using the pseudo-file system data under /proc/ for anyone who's userid has access and understands what they seek.

# Want a process tree?
**pstree**  There are lots of these things. I think systemd will generate one with startup dependencies too.

```

# Open ports with listeners, not localhost
ss -lnt|egrep -v 127
netstat -tunl|grep LISTEN|grep -v 127
netstat -tulpn |grep LISTEN|grep -v 127
```
we filter out '127' to avoid connections on the same system. On Unix, talking over a socket between processes on the same system is as easy as talking between systems.

There are all sorts of ways to make text into a graph, if you like.  graphviz can be used.  iostat, netstat, vmstat and sar all have tools which accept their output for visualization, if that is desired.  Recall, most Linux servers don't have any GUI, so most admins don't want GUI tools.  When I'm troubleshooting server issues, I begin with the performance data for the last 6 months from that system.  Patterns often are seen from that data and I can drill down from there into the process. This is normal server setup stuff. Proactive alarming and monitoring are part of it.

If I just want to see which resources a current process is using beyond what top/htop netstat, vmstate and iostat provide, then I'll get into the /proc/ to see the environment, arguments, etc.  If needed, I can dump the process RAM to a file for analysis. That's when having a C programming background helps.

Or did I miss understanding the questions?

For later lurkers, Unix isn't Windows.    [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) Linux is not Windows
Pretty much any system tool needed was created 30+ yrs ago and has been forgotten.

---

