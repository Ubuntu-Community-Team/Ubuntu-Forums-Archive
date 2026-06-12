---
title: "Restoring backintime archive from external drive?"
date: 2014-08-31
forum: General Help
---

### Post by myacct on 2014-08-31
Hello,

I have a password encrypted backintime archive saved to an external drive.  My hard drive crashed and I need to restore my data.  However, backintime doesn't seem to offer a clear way to do this.  As far as I can tell I can only setup a new archive, not restore from an existing one.  

Any help will be greatly appreciated.

---

### Post by whitesmith on 2014-08-31
It's the nearly invisible icon to the right of the plus sign. See my screenshot. Cheers!

---

### Post by Germar on 2014-09-03
I think the problem is not to find the button but BackInTime is not configured at all, is it?

You can either configure BackInTime manually to use 'Mode local encrypted' with the correct path and your old password. Or you can mount the encrypted snapshots with encfs and restore the old config. Run these commands:

```

mkdir /tmp/bit_restore
encfs /path/to/your/old/snapshots /tmp/bit_restore
#enter your password
cp /tmp/bit_restore/backintime/HOST/USER/PROFILE_ID/last_snapshot/config ~/.config/backintime/

```

If your snapshot list is still empty after this (with both methods) you need to deactivate 'Auto Host/User/Profile ID' in Settings and change 'Host' and 'User' to match your old machines name and user.

Regards,
Germar, BIT-Dev-Team

---

### Post by myacct on 2014-09-05
Thank you for your help! I was able to mount the directory.  I had been concerned that in manually setting backintime to point to the original directory that I might overwrite it or make it otherwise unrestorable.

---

