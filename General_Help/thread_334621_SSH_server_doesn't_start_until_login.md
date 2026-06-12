---
title: "SSH server doesn't start until login"
date: 2007-01-09
forum: General Help
---

### Post by robrmd9 on 2007-01-09
Hello,

I can't SSH into my machine unless I am already physically logged in.  This makes me think the SSH server doesn't start until I log in.  I noticed this problem when I rebooted it remotely and couldn't log back in.

All I did to install it was apt-get install ssh, so my configuration should be default.  Can someone suggest a way I can get it to start automatically everytime the machine is booted, BEFORE a user physically logs in?

Thanks,
Rob

---

### Post by az on 2007-01-09
> **robrmd9 said:**
> Hello,

I can't SSH into my machine unless I am already physically logged in.  This makes me think the SSH server doesn't start until I log in.  I noticed this problem when I rebooted it remotely and couldn't log back in.

All I did to install it was apt-get install ssh, so my configuration should be default.  Can someone suggest a way I can get it to start automatically everytime the machine is booted, BEFORE a user physically logs in?

Thanks,
Rob

The ssh daemon should be running after you boot, and before you log in.  You should be able to log in remotely without someone logging in locally.  Something is not right.

What version of Ubuntu are you running?  What software are you running?

---

### Post by robrmd9 on 2007-01-09
I am running Ubuntu 6.10 - and yesterday I remotely rebooted the machine and couldn't get back in.  When I got home, it was at the Gnome login prompt.

Where could I look to make sure ssh should be starting up?

Thanks,
Rob

---

### Post by kebes on 2007-01-09
Yes the ssh daemon should be starting well before you physically log in. Is it possible that you installed something like firestarter, and that it is only applying firewall permissions after you log into a session?

Something else to try: while sitting at the gnome login screen, go Ctrl+Alt+F2 to get to a text terminal. Then log in there with your username and password. See if you can. Then go:
pgrep ssh -l

To see if any sshd process is running. If it is, try logging into it:
ssh 127.0.0.1

If that works, then try logging in as:
ssh localhost
(If the above works, so should this...)

Then if that works, try logging as if you were doing it remotely
ssh xxx.xxx.xxx.xxx

(where you use your external IP address or domain name...) This should give you an idea as to whether the problem you're seeing is the daemon not running, or you being blocked from logging in externally.


If you can, try (from a different machine) logging in before and after this text-login that I'm suggesting. Is it the same behavior? If you compile a list of cases where it does and doesn't work, it should make it clear at what stage during boot the daemon is finally running (and unblocked).


P.S.: I'm assuming you installed sshd the 'standard' way (with synaptic or aptitude). You didn't install manually, correct?

---

### Post by robrmd9 on 2007-01-09
Yes I installed with apt-get (found command at ubuntuguide.org), and will try your suggestions when I get home (at work). 

Thanks for your time,

Rob

---

