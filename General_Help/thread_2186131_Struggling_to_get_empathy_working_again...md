---
title: "Struggling to get empathy working again.."
date: 2013-11-05
forum: General Help
---

### Post by Baldrick_NZ on 2013-11-05
When I first set 13.10 up, I got both gtalk and fb chat working fine through empathy. I decided I needed a break for a while so deleted my accounts from empathy. But now, I can't seem to activate either accounts in empathy (or Friends) any more. My username and passwords are the same as before, and are entered correctly.

No matter what I do, I keep getting the same message "Disconnected - Authentication Failed"

I've tried purging and re-installing Empathy and gnome online accounts, but to no avail. Even purging the keyring.

There must be some files somewhere that require amending/deleting. But where?

Any help would be very much appreciated!

Using Ubuntu Gnome 13.10.

---

### Post by Baldrick_NZ on 2013-11-06
yippee!

The answer lies here...
```

Tested on Ubuntu 13.04 (but the package is available also for 12.10 so it should work).

sudo apt-get update
sudo apt-get install mcp-account-manager-goa
sudo apt-get remove --purge mcp-account-manager-uoa
sudo reboot

After the reboot empathy will use the Gnome Online Accounts instead of the Ubuntu one.

```

From here... [http://askubuntu.com/questions/224702/empathy-with-gnome-online-accounts-goa](http://askubuntu.com/questions/224702/empathy-with-gnome-online-accounts-goa)

Seems as if the culprit was some unity-based plugins which somehow got installed on my Unity-free Ubuntu Gnome system.

Stoked!:P

---

