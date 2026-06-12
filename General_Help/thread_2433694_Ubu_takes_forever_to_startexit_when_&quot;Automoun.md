---
title: "Ubu takes forever to start/exit when &quot;Automount&quot; drives enabled."
date: 2019-12-23
forum: General Help
---

### Post by Mugsy323 on 2019-12-23
I'm using 64bit Ubuntu 19.10. I have all of my fixed drives set to auto-mount at startup.

Unfortunately, the first time I launch Ubu, the OS seems to have difficulty mounting my drives (takes too long to reach the desktop, long numeric values for drives instead of names, and programs fail to load.) Even shutting down/rebooting takes forever. The drive activity light stays constantly busy (boot drive is SSD).

I'm forced to hit the "Reset" button on the PC to reboot the computer, at which point Ubu loads quickly and with no problems.

This is incredibly annoying and happens the *first* time I launch Ubu *every* time. I have a dual boot PC and even if I load Windows first and try to reboot into Ubu, this still happens on the first attempt.

Does anyone know why Ubu does this and/or how to fix it? TIA

PS: Problem has been present for several versions now.

---

### Post by CelticWarrior on 2019-12-24
Are any of the drives NTFS and shared with Windows? If so consider testing again after disabling Fast Startup in Windows.

You can also use Disks to change how they're being mounted, namely to change the default identifier to LABEL so they appears with the partitions' names instead.

---

### Post by wildmanne39 on 2019-12-24
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by oldfred on 2019-12-24
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mugsy323 on 2019-12-25
> **CelticWarrior said:**
> Are any of the drives NTFS and shared with Windows? If so consider testing again after disabling Fast Startup in Windows.

You can also use Disks to change how they're being mounted, namely to change the default identifier to LABEL so they appears with the partitions' names instead.

Thanks for the reply.

"Fast Startup" already disabled in the BIOS. Yes, they are all NTFS drives.

What is "Disks"? I'm not finding any such app.

---

### Post by Mugsy323 on 2019-12-25
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks. I installed "boor-repair" using the second option at that link and ran it to perform a repair. It found no issues with any of the NTFS drives.

I'll let you know if the problem remains.

---

### Post by CelticWarrior on 2019-12-25
> **Mugsy323 said:**
> "Fast Startup" already disabled in the BIOS. Yes, they are all NTFS drives.

You're confusing it with **Fast Boot** which is a firmware feature. I mentioned **Fast Startup**, a Windows 8 (and newer) feature. This is a trick to give the impression that Windows boots fast but in reality it's some sort of hibernation. Knowing this it's easy to understand the obvious consequences when Ubuntu tries to mount at startup such partitions in an unsafe state and/or trying and filing to mount them RW to finally give up and, at best, mount them 'read only'.

This is very likely the root cause of the problem.

> What is "Disks"? I'm not finding any such app.

Well, "Disks" is Disks, I don't know it by any other name, and if you really have Ubuntu, not a flavor or derivative, then it's certainly installed by default, just search it by its name. It looks like this:

[IMG]https://www.securitybeacon.com/wp-content/uploads/2011/09/Screenshot-SanDisk-U3-Cruzer-Micro-SanDisk-U3-Cruzer-Micro-dev-sdc-%E2%80%94-Disk-Utility.png[/IMG]

---

### Post by Mugsy323 on 2019-12-29
Thanks. I found the "disks" app searching Ubuntu's "Activities".

So far, running "boor-repair" seems to have resolved the issue. Drives have been mounting correctly since I ran it.

Thx to all.

---

