---
title: "Upstart job causes lightdm to restart"
date: 2013-02-04
forum: General Help
---

### Post by ppslim on 2013-02-04
I have setup an upstart job to control a ssh session to a remote host. It provides a report forwarded port back to my machine only.

Before I get any "that isn't a viable VPN", I'm aware and is not the purpose of this and is actually short term wrap-around for other issues.

The upstart job is set to fire on "local-filesystems and network-device-up" automatically, but I currently have a .override file in place and it is manually started. This is due to a secondary problem that is most probably the same problem that I am trying to raise here (I will come back to that at a later time).

"sudo start autossh" works fine and the session/tunnel comes up.

The upstart job is as follows, using autossh from the following page.

[http://www.harding.motd.ca/autossh/](http://www.harding.motd.ca/autossh/)

```
# tunnel - ssh tunnel backup proxy
#
# Provides for remote access

description     "ssh tunnel"

start on (local-filesystems and network-device-up)
stop on (runlevel [!2345] or stopping lightdm)

# expect fork
respawn
respawn limit 10 5
umask 022

exec su tunuser -c "autossh -M 0 -N -F /home/tunuser/.ssh/tconfig -p 8922 -i /home/tunuser/.ssh/TU_id_dsa tunserver@host.name"
```

The setup of the problem is that I have started the job fine, and encounter it as a go to reboot or shutdown (kernel update is the primary example).

On clicking Power, Shutdown, Reboot, lightdm appears to exit, as does X (though I can't be certain of X, it's simply that my display goes out, before returning as follows).

Then X/lightdm restarts and takes me back to the login prompt.

Work around

If I manually stop the job before I reboot (both before I reboot, or if I log back in following the problem to stop it before retrying), the reboot is perfectly fine.

This is 100% reproducible and have not had a successful reboot with the job running to date.

My problem is I am unsure how to debug why lightdm is restarting if the autossh job is still running. Can somebody start with some pointers on this?

Can anybody suggest an event to trigger the stop on to reliably do this?

As a side note (as hinted above), I have the override on the job in place, as without it I am having the following symptoms (Which may be related to my main issue).

When  the system boots and the autossh job starts automatically, lightdm will let me login, but within 3 seconds will take me right back to the login prompt. A second login works.

Final point, I can confirm that home directories are not encrypted, so it's not a file accessibility issue prior to my login.

---

