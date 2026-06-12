---
title: "Trying to run scripts at shutdown"
date: 2013-08-30
forum: General Help
---

### Post by Zukaro on 2013-08-30
I'm trying to run a script at shutdown which will shutdown a bunch of computers using SSH.  I've already set up the RSA key so I don't need to use a password, and changed the permissions on /sbin/poweroff so a password isn't required to call it.  The script works, however, I'm unable to run it at shutdown.  What I want to be able to do is press the power button on the machine and have it automatically shutdown all the other machines.

I've been looking around and I've been told a bunch of things, none of which seem to work.  I've tried changing the ACPI scripts to call my script instead (which in turn calls /sbin/poweroff), I've tried disabling the power menu (the one which comes up asking you to confirm shutdown when you press the power button).  I'm not sure what else to do.  I tried following this [post]("http://ubuntuforums.org/showthread.php?t=185261") but have been unable to get it working so far.

What I need to happen is for the script to be the only thing that's called (and then for the script to call anything else it needs, such as the poweroff command).  However, during a shutdown it does seem to be trying to use the script as I see the error "Host Key Verification Failed" during shutdown (unless I call shutdown via the script I wrote, in which case everything works fine but it seems to call itself a second time as I see errors about how each machine is unreachable after they've shutdown).

I'm using Ubuntu 12.10 (32-bit).

---

### Post by Zukaro on 2013-08-30
I figured out the issue.  I had set everything up to work with the user, not with root (the ssh keys).  I added all the ssh keys to root and now everything is working.

---

### Post by Lars Noodén on 2013-08-30
Another way of doing that, without risking remote root access, is to add the remote user to sudo and allow use of /sbin/shutdown without a password.  That's the kind of granularity that sudo is designed for.  You can also embed the shutdown command inside the key itself on the remote server.

---

