---
title: "Enabling swap within encrypted /home directory"
date: 2012-12-29
forum: General Help
---

### Post by heml0ck on 2012-12-29
Hello guys,

So everytime I did the setup for a swap partition on a LiveCD and rebooted twice(one to the native install to see if its working and 2nd one to confirm); that partition switched to "unknown" in gparted after the second reboot. I found* [SwapFAQ]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F") *and *[EnableHibernateWithEncryptedSetup]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F")* and followed both which were incredibly helpful; but while I was doing the second one the passphrase I entered wasn't recognized so I had to start over.

Now I've finished both successfully but in the last step when I ran ```
sudo update-initramfs -u -k all
``` I got a warning like this:
> cryptsetup: WARNING: found more than one resume device candidate:
                                 (the UUID for the swap I entered in my first try)
                                 cryptswap1So my question is how do I remove that first UUID to prevent any possible conflict? I haven't done a reboot since following the howtos so hopefully there won't be a problem after I'm done. Thanks in advance for any help!

---

### Post by heml0ck on 2012-12-29
bump.. someone should know something, surely?

---

### Post by oldfred on 2012-12-29
Please bump only once per 24 hours.

Post fstab or make sure you have only one swap entry. When you encrypt /home, swap is also encrypted and when a partition is encrypted gparted and other tools do not see the partition. 
cat /etc/fstab


Fstab should only have the one entry for the cryptswap. You can add # like other comments, to convert to comment before deleting to make sure you are editing out the entry you do want to remove.

---

