---
title: "Error message in Saucy after logging back in: 'No session for pid xxxx', no network"
date: 2013-10-13
forum: General Help
---

### Post by syntaxerror74 on 2013-10-13
Hello there,

this issue must have occurred only recently. I can't seem to remember this behavior shortly after installing Saucy.
Interestingly enough, there are still no google-able threads that involve this message, so it is possible I'm the only one or one of few who gets this.

Sometimes it happens that the system runs out of physical memory (well, my older board doesn't support 8 GB) and you can get it back into a usable state by logging out and back in, because sometimes this is the only way to force zombie processes hooked deeply into the system to terminate.
However, this procedure, which worked perfectly on my previous Debian-based distro, seems to cause problems on Saucy (or maybe before that).

The following will happen:

- when X starts (NOTE: no compiz installation done yet), it will bring up an error message window on the top left saying "**No session for pid xxxx**' with xxxx being an arbitrary pid number.
Sure, click it away, and it can be ignored? 
NOPE. You wish!  Your network will be GONE after that, no internet, nada. Also, my custom connection settings (e. g. DSL connection 1) have disappeared from taskbar. The system doesn't know who I am anymore. ;)

Therefore, on condition that you ensure to leave your fingers off the 'Logout' button in LXDE/Openbox, your system will always work fine.
But malfunctioning networking after logout now forces me to **reboot** everytime, should I ever be required to log out.

Did anyone else experience this behavior?

---

### Post by syntaxerror74 on 2013-10-20
Anyone? 

(Now that Saucy is released, please move to appropriate support forum, thanks.)

---

### Post by cariboo on 2013-10-20
Moved by request.

---

### Post by Interruptor on 2013-11-11
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1249844](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1249844)

---

### Post by syntaxerror74 on 2013-11-13
Thank you!!

I hate to always play attention seeker by annoying others by constantly bumping my threads. That's why I'm even happier that you did discover my thread after all within these excessively busy forums! Thanks for the LP bug entry. I'm telling you that in all honesty: when I discovered the problem there were *ZERO* Google hits about that; for that reason I rather chose to wait a little more.

[edit] The above bug is a **duplicate**.

Here is the **active bug**: (please do no longer comment to #1249844 therefore)
[https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336)

---

