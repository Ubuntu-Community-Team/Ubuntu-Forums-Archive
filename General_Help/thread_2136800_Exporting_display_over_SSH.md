---
title: "Exporting display over SSH"
date: 2013-04-18
forum: General Help
---

### Post by YourSurrogateGod on 2013-04-18
Hi all,

I'm having a hell of a time trying to get this to work.  In my virtual Azure environment, I have CentOS 6.3 set up.  I would like to export an instance of firefox because I'm testing something on localhost.

I ran this command on remote (CentOS 6.3):
```
ssh -X someusername@somehostname.net -p 54444
```

And on local (a Mac):
```
xhost +
```

On remote:
```
xclock
```

... and nothing.  I was expecting a small clock to show up.  What am I messing up?

---

### Post by matt_symes on 2013-04-18
Hi

This is from the man page for ssh.

> -X      Enables X11 forwarding.  This can also be specified on a per-host basis in a configuration file.
                                                                                                                                      
             X11 forwarding should be enabled with caution.  Users with the ability to bypass file permissions on the remote host
             (for the user's X authorization database) can access the local X11 display through the forwarded connection.  An
             attacker may then be able to perform activities such as keystroke monitoring.
                                                                                                                                      
             For this reason, X11 forwarding is subjected to X11 SECURITY extension restrictions by default.  Please refer to the
             ssh -Y option and the ForwardX11Trusted directive in ssh_config(5) for more information.

-Y      Enables trusted X11 forwarding.  Trusted X11 forwardings are not subjected to the X11 SECURITY extension controls.

Maybe that's the problem.

Kind regards

---

### Post by YourSurrogateGod on 2013-04-18
> **matt_symes said:**
> Hi

This is from the man page for ssh.



Maybe that's the problem.

Kind regards

I have to disagree.  I'm behind a router and that could be the main problem, imo.  Not sure how to get around this issue.

---

### Post by matt_symes on 2013-04-18
Hi

I may not be the best to help you then as i always ssh into the CLI and i have never used x11 forwarding.

Still, this is a free bump for your trouble.

Kind regards

---

### Post by markbl on 2013-04-18
OP, you are not clear what your server is here. Ubuntu I presume? Anyhow, you must ensure X11Forwarding is set to Yes on your server (in /etc/ssh/sshd_config). The "xhost +" is not required btw.

---

### Post by tgalati4 on 2013-04-18
I always use:

ssh -2 -Y username@computername

---

