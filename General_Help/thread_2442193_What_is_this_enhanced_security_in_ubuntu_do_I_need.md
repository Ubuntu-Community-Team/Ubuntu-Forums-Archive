---
title: "What is this enhanced security in ubuntu do I need to enable it?"
date: 2020-04-30
forum: General Help
---

### Post by jebi on 2020-04-30
HI,

What is this enhanced security in ubuntu do I need to enable it?

I cant remember what this was called I think I read something about on omgubuntu, but I cant find it?

Instructions needed to install?

thx

---

### Post by TheFu on 2020-05-01
To enable enhanced security on any computer, do these things:
* disable blue tooth
* disable wifi
* unplug any network cable, be that ethernet, infiniband or usb

Those steps will drastically enhance security. There could be some convenience and usability issues, however.  ;)

Now, if you want something like SELinux, that isn't the native Ubuntu security tool and it is really only for experts.  SELinux is embedded in RHEL, Fedora, Scientific Linux, CentOS, so if that is your goal, perhaps changing to one of those distros would be a better idea.  SELinux will break things on Ubuntu. Often, on RHEL and CentOS, admins disable it to avoid the issues it brings to their servers.

Security is always a trade-off between convenience and security.

Another method to improve security for Ubuntu is to carefully read the sticky threads at the top of the Security sub-forum here. Lots and lots of good information.

---

