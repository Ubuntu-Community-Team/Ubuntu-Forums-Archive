---
title: "Is there way batch execute commands from windows machine"
date: 2013-02-14
forum: General Help
---

### Post by namoo on 2013-02-14
I've got bunch of Ubuntu machines.  I've got OpenSSH installed on of them.  My machine is windows 7 machine.
Periodically, I would like to reboot all my Ubuntu machines.
Right now, I'm logging into individual machines via putty and sending a reboot command.  This is painfully long process and it will get worse as I add machines.  Is there an easy way for me to do this?

My first choice would be to do this from a windows machine.  But if there is no way, I can even log into one of the Ubuntu machine and send the command from there.

---

### Post by papibe on 2013-02-14
Hi namoo.

> **namoo said:**
> Periodically, I would like to reboot all my Ubuntu machines.
I would start by rethinking this. It is not a common practice because is not necessary. You may need to reboot after a kernel or a video driver upgrade, but that covers almost all cases.

In rare cases, you would need to restart a service, but rarely reboot.

Anyway...

I see a couple of solutions:
[LIST]
[*]**Hack a simple solution**.

Start with something like this:
```
ssh remotehost /usr/bin/sudo /sbin/reboot
```
First automation would be to create passphraseless keys to avoid entering the login password (read [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") for that). Then you could avoid entering the sudo password by configuring sudoers (details [here]("https://help.ubuntu.com/community/Sudoers")).

Both measures involve a compromise in security.

You can do this both on a Linux client or on Windows using Putty.


[*]**Move into a more comprehensive remote administration solution**.

Take a look at [Landscape]("https://landscape.canonical.com/") or [Puppet]("http://en.wikipedia.org/wiki/Puppet_%28software%29").
[/LIST]
I would recommend taking a serious look at Puppet (in the repos btw)

Hope that helps. Let us know how it goes.
Regards.

---

