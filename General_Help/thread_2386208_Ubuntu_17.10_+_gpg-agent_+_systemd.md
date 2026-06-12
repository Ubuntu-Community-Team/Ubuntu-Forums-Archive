---
title: "Ubuntu 17.10 + gpg-agent + systemd"
date: 2018-03-02
forum: General Help
---

### Post by mlohr on 2018-03-02
Hello,

i tried to use gpg-agent instead ssh-agent for SSH authorizations. Basically, it works, but i can not get gpg-agent started at login time (e.g. by systemd).

There's a file /etc/X11/Xsession.d/90gpg-agent which mentions, that systemd should do alle the stuff, but systemctl does not list any gpg-agent like service. So, how can i get it running?
(I also have "use-agent" in my gpg.conf and "enable-ssh-support" in gpg-agent.conf).

There is some kind of systemd script in /usr/lib/systemd/user/gpg-agent.service, but i can't enable it via systemctl enable, because of:
```

The unit files have no installation config (WantedBy, RequiredBy, Also, Alias
settings in the [Install] section, and DefaultInstance for template units).
This means they are not meant to be enabled using systemctl.
Possible reasons for having this kind of units are:
1) A unit may be statically enabled by being symlinked from another unit's
   .wants/ or .requires/ directory.
2) A unit's purpose may be to act as a helper for some other unit which has
   a requirement dependency on it.
3) A unit may be started when needed via activation (socket, path, timer,
   D-Bus, udev, scripted systemctl call, ...).
4) In case of template units, the unit is meant to be enabled with some
   instance name specified.

```

So, what am i doing wrong and what is the best way to get gpg-agent running?

Best regards and thanks in advance
Matthias

---

