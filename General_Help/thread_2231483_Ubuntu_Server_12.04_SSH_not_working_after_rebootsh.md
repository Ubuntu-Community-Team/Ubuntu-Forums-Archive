---
title: "Ubuntu Server 12.04 SSH not working after reboot/shutdown"
date: 2014-06-25
forum: General Help
---

### Post by Vindows Wista on 2014-06-25
Hi all,

I have an issue where ssh stops working after a reboot/shutdown. After the system restarts I try to ssh back in only to get "ssh: connect to host 192.168.*.*** port 22: No route to host". I have to manually shut the system down using the power button and when it restarts again the ssh works fine. I usually reboot with "sudo reboot" but I always need to shut the server down using the power button. This happens when I use "sudo shutdown" as well. I'll power on the server but then I would have to poweroff using the power button and restart again. Any ideas?

Regards,

---

### Post by ubudog on 2014-06-25
Hi,

Sounds like a firewall issue.  Is port 22 closed?

---

### Post by Lars Noodén on 2014-06-26
Having to press the power button to get the system properly shutdown suggests that the problem is with the shutdown process.   Does that apply to the reboot process too?  Specifically which command with which parameters are you using?

---

### Post by Vindows Wista on 2014-06-29
> **Lars Noodén said:**
> Having to press the power button to get the system properly shutdown suggests that the problem is with the shutdown process.   Does that apply to the reboot process too?  Specifically which command with which parameters are you using?

Yes this applies to rebooting as well. I use "sudo reboot" mainly.

---

### Post by Vindows Wista on 2014-06-29
> **ubudog said:**
> Hi,

Sounds like a firewall issue.  Is port 22 closed?

I just checked to be sure and the port is open.

---

### Post by Lars Noodén on 2014-06-30
> **Vindows Wista said:**
> Yes this applies to rebooting as well. I use "sudo reboot" mainly.

That suggests it is a hardware problem and that you need different options to shutdown or reboot.  Try using [shutdown -r](http://manpages.ubuntu.com/manpages/trusty/en/man8/shutdown.8.html) instead of "reboot" and try different options like -h, -H, or -P  When you find the combination that works for your hardware, then you'll have to pass them as boot parameters:

[http://askubuntu.com/questions/7114/why-cant-i-restart-shutdown](http://askubuntu.com/questions/7114/why-cant-i-restart-shutdown)

---

### Post by Vindows Wista on 2014-07-02
> **Lars Noodén said:**
> That suggests it is a hardware problem and that you need different options to shutdown or reboot.  Try using [shutdown -r]("http://manpages.ubuntu.com/manpages/trusty/en/man8/shutdown.8.html") instead of "reboot" and try different options like -h, -H, or -P  When you find the combination that works for your hardware, then you'll have to pass them as boot parameters:

[http://askubuntu.com/questions/7114/why-cant-i-restart-shutdown](http://askubuntu.com/questions/7114/why-cant-i-restart-shutdown)

I appreciate the help but that didn't work. I tried everything under the sun but somehow I'm stuck. That wasn't the same problem either.

---

