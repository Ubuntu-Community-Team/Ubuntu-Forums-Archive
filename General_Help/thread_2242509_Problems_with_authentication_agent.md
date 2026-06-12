---
title: "Problems with authentication agent"
date: 2014-09-02
forum: General Help
---

### Post by henrikwl on 2014-09-02
Hi guys

I'm on Ubuntu 14.04, running the xubuntu-desktop setup.

Software center keeps failing with permission errors, and I've managed to uncover that this is due to a component named polkit-gnome-authentication-agent-1 not running.

Every article I've read about this suggests to try and execute it from xterm after having logged in, but when I do this, I just get this error:

```
** (polkit-gnome-authentication-agent-1:24806): WARNING **: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Cannot determine user of subject
Cannot register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Cannot determine user of subject
```

The only reference to this error I've found had to do with problems starting the agent during login, but for me it fails even if I start it from the command line after having logged in.

Anybody have any ideas? I'd love to get this working.

---

### Post by grahammechanical on 2014-09-02
Do you have this problem with the software centre when using the Ubuntu Gnome Unity session. I ask because polkit-gnome-authentication-agent-1 is a Gnome component. What is the corresponding agent for the Xfce desktop?

I  have  found this thread

[http://ubuntuforums.org/showthread.php?t=2211822](http://ubuntuforums.org/showthread.php?t=2211822)

With this link relating to Lubuntu

[https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html)

Find out if you have polkit-desktop-privileges installed. I have it on my Utopic Unicorn Unity system.

Regards

---

### Post by henrikwl on 2014-09-03
I can't use the Gnome Unity session, as this is a headless VM on an ESX farm which I connect to through xrdp. I basically just installed the xubuntu-desktop meta package and it all got pulled in from that.

I also have the policykit-desktop-privilege package installed.

---

