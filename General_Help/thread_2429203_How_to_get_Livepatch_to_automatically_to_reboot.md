---
title: "How to get Livepatch to automatically to reboot"
date: 2019-10-15
forum: General Help
---

### Post by mfearby2 on 2019-10-15
How can I get Livepatch to automatically reboot? Everytime it installs a new kernel my wordpress blog won't connect to the database and I have to SSH in and reboot. I'd rather just have it reboot automatically. Thanks.

---

### Post by deadflowr on 2019-10-15
It would be counter to the point of livepatch if you set it to reboot.
If every time a livepatch is applied it breaks the system, don't run the livepatch.

Also, livepatch does not install new kernels, it applies small patches to the running kernel.

For issues please contact Ubuntu's support:
[https://ubuntu.com/livepatch#get-in-touch]("https://ubuntu.com/livepatch#get-in-touch")

---

### Post by mfearby2 on 2019-10-15
This is what's causing the need for a reboot:

ubuntu@ip-whatever:~$ cat /var/run/reboot-required.pkgs
linux-base

If linux-base is causing Mysql to shutdown and need a reboot, then why can't Livepatch be configured to just reboot? The alternative (not using Livepatch) is me forgetting to apply updates and the server becoming potentially vulnerable. I'd much rather an up-to-date system that might occasionally reboot and be unreachable for one minute once a week than have a much bigger problem on my hands down the track.

---

### Post by PaulW2U on 2019-10-15
> **mfearby2 said:**
> why can't Livepatch be configured to just reboot?
Because it was never designed to.

You're probably aware, but for the benefit of anyone else reading this thread, the following quote is taken from [https://wiki.ubuntu.com/Kernel/Livepatch](https://wiki.ubuntu.com/Kernel/Livepatch):
> There may be occasions when the traditional kernel upgrade and reboot might still be necessary. 
Just to clarify, are you also accepting conventional kernel updates as well as receiving patches via the Livepatch service? As [https://ubuntu.com/livepatch](https://ubuntu.com/livepatch) confirms, patches are applied without restarting your system so I would be surprised if the application of a patch left your server indicating that a restart was required.

---

### Post by mfearby2 on 2019-10-16
Well, if it's not Livepatch's fault, I guess my question therefore becomes: how can I configure Ubuntu to reboot automatically whenever it determines that one is required?

---

### Post by deadflowr on 2019-10-16
> **mfearby2 said:**
> Well, if it's not Livepatch's fault, I guess my question therefore becomes: how can I configure Ubuntu to reboot automatically whenever it determines that one is required?

You can uncomment a line in /etc/apt/apt.conf.d/50unattended-upgrades and set it to true
with regards to reboot automatically when required.
These
```
// Automatically reboot *WITHOUT CONFIRMATION* if
//  the file /var/run/reboot-required is found after the upgrade
**//Unattended-Upgrade::Automatic-Reboot "false";**
```
The line in bold would require the slashes at the front of the line removed and change false to true.
So it looks like this 
```
Unattended-Upgrade::Automatic-Reboot "true";
```
leave everything else alone.
If you require it to reboot after a set time, then uncomment the next part and set a time
```
// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
[B]//Unattended-Upgrade::Automatic-Reboot-Time "02:00";
```
[/B]
Otherwise, if left alone it will reboot at once.

---

### Post by mfearby2 on 2019-10-18
Thanks very much deadflowr. I'll go with the automatic reboot at 2:00 am.

Cheers!

---

