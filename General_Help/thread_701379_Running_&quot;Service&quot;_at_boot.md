---
title: "Running &quot;Service&quot; at boot?"
date: 2008-02-19
forum: General Help
---

### Post by Grax on 2008-02-19
Ubuntu 7.10 Server

I have a CSS server setup on the box and I'd like to have it run automatically when the server is booted.  I've played around with /etc/init.d, but I can't get it working properly.

What is the best way to get the CSS server running at boot, and how do I do that?

I had created a script in /etc/init.d and "installed" it to run at boot.  The script consists of:

cd /usr/local/HLDS/srcds;./run > /dev/null 2>&1

Which executes:

/usr/local/HLDS/srcds/srcds_run -console -game cstrike +maxplayers 24 +map fy_barn_ +mp_dynamicpricing 0

The problem I'm having...

1) The system never completes loading as the script never completes until the game server is shutdown.  When this does happen I see the the FTP server finally starts and a few other things

2) I can't connect to the server when executed this way, not sure why, but I can't

3) I can't shutdown the ubuntu server until I kill the process of the /etc/init.d script

Thanks in advance,

Andrew

---

### Post by Jussi Kukkonen on 2008-02-19
Grax, take a look at *start-stop-daemon*. All daemon init scripts use it, so you should have no problems finding examples in /etc/init.d/

EDIT: forgot to mention: read the man pages, especially about specifying the user to run as -- running CSS server as root is probably not healthy (and might even be a reason for some of the problems)

---

### Post by Grax on 2008-02-19
I figured it out...

I was missing an & at the end of the boot script, so:

cd /usr/local/HLDS/srcds;./run > /dev/null 2>&1 &

Andrew

---

### Post by Jussi Kukkonen on 2008-02-20
Andrew, that kind of works but there are several reasons to use start-stop-daemon, most importantly not running the service as root (using *--chuid*). Search "counter strike server exploit" and see why running things like that as root is not a good idea.

---

