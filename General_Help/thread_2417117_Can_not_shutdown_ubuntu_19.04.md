---
title: "Can not shutdown ubuntu 19.04"
date: 2019-04-20
forum: General Help
---

### Post by williambiggs31 on 2019-04-20
I did a clean install of 19.04 on a AMD 6 core 24g ram  with a Rx 570 .  When I try to shut down I get the Ubuntu screen then it just locks up  and will not shut down . I have to hit the power button to shut the PC  down

---

### Post by QIII on 2019-04-20
Support request, not chat.

Moved to General Help.

---

### Post by jeanmarc-louviaux on 2019-04-21
Hi,
I had the same issue, i had to install "gnome-session".
Hope it help

---

### Post by jeanmarc-louviaux on 2019-04-22
Hmm.. i also had to :
Boot to grub > Advanced > Recovery > Root access
[B]sudo fsck -f /dev/nvme0n1p2
[/B]Still the shudown is slow, i wondering where the issue is :|

> 
avr 22 11:09:05 astrolabe gdm3[1102]: GLib: g_hash_table_foreach: assertion 'version == hash_table->version' failed
avr 22 11:09:05 astrolabe gnome-session-binary[1760]: CRITICAL: We failed, but the fail whale is dead. Sorry....
avr 22 11:07:46 astrolabe spice-vdagent[2070]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
avr 22 11:07:43 astrolabe nvidia-persistenced[1414]: Failed to unlink PID file: No such file or directory
avr 22 11:07:34 astrolabe systemd[1]: Failed to start Service for snap application canonical-livepatch.canonical-livepatchd.


---

### Post by jeanmarc-louviaux on 2019-04-25
well..well.. I've downgraded my BIOS and now the shutdown work properly \\:D/
I am using a [Gigabyte B360M DS3H (downgraded to F12)]("https://www.gigabyte.com/Motherboard/B360M-DS3H-rev-10#support-dl-bios")
Still got some odd errors but it work
> 
jeanmarc@astrolabe:~$ journalctl -xb -p err
-- Logs begin at Sun 2019-04-21 10:37:36 CEST, end at Thu 2019-04-25 19:44:53 CEST. --
avr 25 19:44:35 astrolabe kernel: Couldn't get size: 0x800000000000000e
avr 25 19:44:35 astrolabe kernel: MODSIGN: Couldn't get UEFI db list
avr 25 19:44:35 astrolabe kernel: Couldn't get size: 0x800000000000000e
avr 25 19:44:35 astrolabe kernel: Couldn't get size: 0x800000000000000e
avr 25 19:44:35 astrolabe kernel: PKCS#7 signature not signed with a trusted key
avr 25 19:44:36 astrolabe kernel: PKCS#7 signature not signed with a trusted key
avr 25 19:44:36 astrolabe kernel: PKCS#7 signature not signed with a trusted key
avr 25 19:44:36 astrolabe kernel: PKCS#7 signature not signed with a trusted key
avr 25 19:44:39 astrolabe systemd[1]: Failed to start Service for snap application canonical-livepatch.canonical-livepatchd.
-- Subject: L'unité (unit) snap.canonical-livepatch.canonical-livepatchd.service a échoué
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- L'unité (unit) snap.canonical-livepatch.canonical-livepatchd.service a échoué, avec le résultat failed.
avr 25 19:44:41 astrolabe spice-vdagent[1758]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0


---

### Post by gjtoth on 2019-07-27
In addition to a semi-slow boot-up, I'm having this problem.  Running Xubuntu 19.04  Anyone found a concrete solution?

---

### Post by habana on 2019-07-27
> well..well.. I've downgraded my BIOS and now the shutdown work properly
I am using a Gigabyte B360M DS3H (downgraded to F12)
Still got some odd errors but it work

I had this problem with a Gigabyte B360M HD3 motherboard with f12 BIOS. Upgrading to the latest f13 (released 27 June) fixed it. I note that the latest BIOS for your mobo is f15 (released 8 July); did you try that?

---

