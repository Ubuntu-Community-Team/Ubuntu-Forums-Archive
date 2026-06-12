---
title: "No auto mount on removable storage"
date: 2007-10-05
forum: General Help
---

### Post by ebike on 2007-10-05
Hi All,

I have a Dell laptop with Feisty installed. I cannot seem to get my removable drives mounted when I plug them in the USB port.

I have auto mounting set up in System->Preferences>Removable Drives

Dbus is running although when I boot my laptop I get a "HAL initialization error" so have to do a 
sudo /etc/init.d/dbus restart on initial startup, I don't know if that is relevant though.

The only way I can mount USB drives is to manually mount thenm as root.

Can anyone help out?

Thanks.

---

### Post by ryanVickers on 2007-10-05
Well, if your getting that, chances are that there was a problem initializing the hardware abstraction layer! ;)

I would look for a solution to this, and then see if fixing that solves the problem rather than just trying to find something wrong with "auto-mount".  That's like trying to find a solution to a GTK theme engine problem by searching "themes don't work" :)

I'll see what I can dig up :)

Edit: > I had this problem in Edgy, right after upgrade.  Followed suggestions in many threads, such as:
  1. Edit /etc/fstab file to "noauto" for NTFS volume
  2. Timed log-in for session
  3. Disabled volume manager in Start-up, and finally
  4. Deleted firefox from Start-up (my own idea)found that somewhere - especially, the "**disable automatic login**" seems to have fixed many a person's difficulties... :)

---

### Post by ebike on 2007-10-07
Thanks for that, I will try some of those suggestion for the "Hal Initialization" issue.

Regarding the auto-mount issue, I found I had an entry in /etc/fstab for mounting a /dev/sdc1
partition (for a card-reader I had). On removing that line, auto-mount works again.

Seems a bit strange that the device I was mounting was on /dev/sdb1, that it would conflict with that manual entry for /dev/sdc1 ??

Anyway, it's all good now.

---

