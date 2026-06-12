---
title: "Getting prompted over &amp; over to do a restore test (even if successful)"
date: 2020-02-13
forum: General Help
---

### Post by fr33z0n3r on 2020-02-13
I use the builtin Ubuntu (18.04.4 up-to-date) backup feature.  It has started prompting me to do a restore test over and over.  It never stops prompting it seems.  After the first test completes (presumably successful) it just asks for the encryption password again - never ending.

I have no space issues (anywhere), no disk issues, and no errors are being shown.

Does anyone know how to fix this?

---

### Post by EuclideanCoffee on 2020-02-13
Appears that something is happening with the scheduling. I think running debug is your best bet since it appears deja-dup doesn't run logs.

[https://answers.launchpad.net/deja-dup/+question/125731](https://answers.launchpad.net/deja-dup/+question/125731)

The first comment answers how to turn out debugging.

Before you do this, you should probably stop deja-dup. I don't have it on my computer, but I'm assuming it's being run with a systemd configuration.

Try

[https://askubuntu.com/questions/1015568/prevent-deja-dup-daemon-from-starting-but-keep-deja-dup](https://askubuntu.com/questions/1015568/prevent-deja-dup-daemon-from-starting-but-keep-deja-dup)

Or these steps.

$ systemctl stop deja-dup

Or deja then hit the tab key until something appears.

---

### Post by fr33z0n3r on 2020-02-15
Thanks,  but that debug option doesn't seem to do anything useful.  I  stopped the prompting for testing the encrypted backup.  Then used  dconf-editor to re-enable it (I think).  In some time it should prompt  me to retest is the hope, and I'll update when that occurs.

---

