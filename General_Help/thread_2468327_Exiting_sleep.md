---
title: "Exiting sleep"
date: 2021-10-25
forum: General Help
---

### Post by Freiklite on 2021-10-25
Hi,
The notebook is on and the cover is folded in.
When I lift up the notebook cover the screen becomes black after a few seconds.
The power light is blinking: the computer is in the sleep state.
If I push and release the power button or press a key on the keyboard to bring the computer out of the sleep state nothing happens.
I have to shut down then turn on it.
Is it a matter of adjusting settings?
Any suggestions will be welcome.
Thank you in advance.


N.B.:
> $ uname -a
Linux zety-HP-Laptop-14s-fq0xxx 5.11.0-38-generic #42~20.04.1-Ubuntu SMP Tue Sep 28 20:41:07 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


dmesg file:> [https://paste.ubuntu.com/p/ZdKcHF54m7/](https://paste.ubuntu.com/p/ZdKcHF54m7/)

---

### Post by Freiklite on 2021-10-26
Hi,
More iinformation:> [ 1240.520207] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.523157] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.524613] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.525894] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.535023] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.536035] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.543620] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.543776] wlo1: deauthenticating from 34:27:92:eb:33:18 by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1240.545004] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.558205] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.570181] rtw_8821ce 0000:01:00.0: sta 34:27:92:eb:33:18 with macid 0 left
[ 1240.616183] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
[ 1240.644997] rtw_8821ce 0000:01:00.0: stop vif 00:e9:3a:e9:c8:c3 on port 0
zety@zety-HP-Laptop-14s-fq0xxx:~$ man kernel_lockdown.7
Aucune entrée de manuel pour kernel_lockdown.7

Bye.

---

### Post by Freiklite on 2021-10-26
Other information:
[https://manpages.ubuntu.com/manpages/jammy/en/man7/kernel_lockdown.7.html](https://manpages.ubuntu.com/manpages/jammy/en/man7/kernel_lockdown.7.html)

---

### Post by Freiklite on 2021-10-26
Hi,
On my notebook:
Boot options
Secure boot [enabled]

The  boot options *comment*:> When secure boot is enabled,
Bios performs cryptographic check during bootup, for the integrityof the software image.
It prevents unauthorized or maliciously modified software for running. 

End of the post.
Goodbye.

---

### Post by Holger_Gehrke on 2021-10-26
In short: if secure boot is enabled the kernel switches into a secure mode of operation. Among many other restrictions the use of an unencrypted swap file is forbidden. And since hibernation writes an image of the current state of the system to the swap file ...
The solution would be to have the swap file on an encrypted device / file system which has to be unlocked at boot time.

Holger

---

