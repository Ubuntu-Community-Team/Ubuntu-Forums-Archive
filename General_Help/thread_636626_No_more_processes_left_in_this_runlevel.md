---
title: "No more processes left in this runlevel?"
date: 2007-12-10
forum: General Help
---

### Post by campee on 2007-12-10
I am running Ubuntu 6.06 Server as a virtual machine inside of VMWare Server. This machine has Zimbra mail server and Bind running on it, nothing else. The machine was up and running perfectly when the host computer lost power and turned off. Once the host computer was powered on I turned my Ubuntu VM on. I got Grub error 17 upon booting. I booted to a Ubuntu 7 Live CD and ran:

sudo fsck -y /dev/sda1

It found a ton of errors and it fixed them all, presumably. It found probably 100 issues with the file system. I rebooted and this time I didn't get a GRUB error. However, I get a message stating that no inittab file was found and I am asked to enter a run level to use, so I enter 3. Then I get 'no more processes left in this run level'. I'd like to recover the configuration of this virtual machine, what should I try do now? Also, I'd like to know if the recovery process that I tried earlier (fsck) was wise or not.. and if not, what should I have done instead? Thank you! :)

---

### Post by dcstar on 2007-12-10
> **campee said:**
> I am running Ubuntu 6.06 Server as a virtual machine inside of VMWare Server. This machine has Zimbra mail server and Bind running on it, nothing else. The machine was up and running perfectly when the host computer lost power and turned off. Once the host computer was powered on I turned my Ubuntu VM on. I got Grub error 17 upon booting. I booted to a Ubuntu 7 Live CD and ran:

sudo fsck -y /dev/sda1

It found a ton of errors and it fixed them all, presumably. It found probably 100 issues with the file system. I rebooted and this time I didn't get a GRUB error. However, I get a message stating that no inittab file was found and I am asked to enter a run level to use, so I enter 3. Then I get 'no more processes left in this run level'. I'd like to recover the configuration of this virtual machine, what should I try do now? Also, I'd like to know if the recovery process that I tried earlier (fsck) was wise or not.. and if not, what should I have done instead? Thank you! :)

Standard Ubuntu uses run level 2, I don't think the server version is different.

fsck was essential, but if you have file corruption then that's what can happen on a machine without UPS protection.

---

### Post by campee on 2007-12-10
Yeah, I know I should have a UPS.. this was just kind of a test set up, a temporary thing. At any rate, I'd like to learn how to recover from this sort of failure. I tried Run level 2 and got the same message. What should my next step be in trying to recover this box? Is there a "repair reinstallation" type of option with Ubuntu?

---

### Post by dcstar on 2007-12-10
> **campee said:**
> Yeah, I know I should have a UPS.. this was just kind of a test set up, a temporary thing. At any rate, I'd like to learn how to recover from this sort of failure. I tried Run level 2 and got the same message. What should my next step be in trying to recover this box? Is there a "repair reinstallation" type of option with Ubuntu?

I don't think so, the easiest thing may be to do another basic install on a new partition, and then copy files from the fresh install to your damaged one.

---

