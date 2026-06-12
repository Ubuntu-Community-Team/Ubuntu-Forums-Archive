---
title: "possible boot problems"
date: 2022-07-13
forum: General Help
---

### Post by jgw on 2022-07-13
Today I turned on my computer and then, for the heck of it, thought I would take a loolk at logs and see what logs thought.  I know about the couchpotato thing below is the result.  I think most of it seems ok to me but there is something about not comminicating with TPM chip, I have no idea what an TPM chip is.  Anyway, I thought I would p;ost this and see if I'm really fine. 

```
10:29:17 AM (otato.py): couchpotato.service: Failed at step USER spawning /var/lib/CouchPotatoServer/CouchPotato.py: No such process
10:25:33 AM pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
10:25:31 AM (otato.py): couchpotato.service: Failed at step USER spawning /var/lib/CouchPotatoServer/CouchPotato.py: No such process
10:25:20 AM systemd-resolve: Failed to send hostname reply: Invalid argument
10:25:18 AM (otato.py): couchpotato.service: Failed at step USER spawning /var/lib/CouchPotatoServer/CouchPotato.py: No such process
10:25:14 AM systemd-resolve: Failed to send hostname reply: Invalid argument
10:25:14 AM (otato.py): couchpotato.service: Failed at step USER spawning /var/lib/CouchPotatoServer/CouchPotato.py: No such process
10:24:55 AM kernel: ima: Error Communicating to TPM chip
10:24:55 AM kernel: ipmi:dmi: Base address is zero, assuming no IPMI interface
10:24:55 AM kernel: x86/cpu: VMX (outside TXT) disabled by BIOS
```

Thank you..............

---

### Post by yancek on 2022-07-14
The TPM (Trusted Platform Module) is explained at the link below.  You should find the ootion to enable/disable it under the Security tab in your BIOS firmware.

[https://trustedcomputinggroup.org/resource/trusted-platform-module-tpm-summary/](https://trustedcomputinggroup.org/resource/trusted-platform-module-tpm-summary/)

---

### Post by VMC on 2022-07-14
> **jgw said:**
> ...there is something about not comminicating with TPM chip, I have no idea what an TPM chip is.  Anyway, I thought I would p;ost this and see if I'm really fine. 

```
...
10:24:55 AM kernel: ipmi:dmi: Base address is zero, assuming no IPMI interface
..
```

Thank you..............

A user with same issue and easy fix:
[https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot](https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot)

---

### Post by jgw on 2022-07-14
Thank you for the reply!

---

