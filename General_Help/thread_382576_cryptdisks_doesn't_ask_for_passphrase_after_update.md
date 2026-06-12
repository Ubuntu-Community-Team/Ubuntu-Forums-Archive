---
title: "cryptdisks doesn't ask for passphrase after update"
date: 2007-03-12
forum: General Help
---

### Post by vmalep on 2007-03-12
Hi,

I am running edgy. This afternoon (12/03/2007), I did an upgrade of the system (this is done more or less every two days) and cryptsetup was updated. During the upgrade, I remember having seen a message like "missing arguments in /etc/crypttab. I rebooted a bit later and I could not mount anymore the encrypted partition.

The block file in /dev/mapper was not created and when restarting /etc/init.d/cryptdisks, I was not asked for the passphrase.

I eventually had a look in /lib/cryptsetup/cryptdisks.function and found out that the script was stopping at the line 392, function do_start because of the "Make sure that all fields are present" test (even though no error message were displayed in the terminal when starting cryptdisks). I commented the line ("continue" of the elif) and now, it works.

Is that a bug? Does anyone faced the same problem?

Best regards,
Pierre

---

