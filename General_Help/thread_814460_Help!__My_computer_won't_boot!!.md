---
title: "Help!  My computer won't boot!!"
date: 2008-05-31
forum: General Help
---

### Post by Culito on 2008-05-31
Running Gutsy.  Went to boot up just now and the boot flash comes up, all looks normal.  Screen goes blank before the login screen comes up.  It just flashes back and forth from a black screen to the "waiting" mouse icon.
Finally it gives up and I see what looks to be the end of the dmesg output.  The last line is:

*Running local boot scripts (/etc/rc.local)

And a lone, flashing cursor.  Crap!!!  Where can I go from here!  I hate using this crappy Windows laptop!!

---

### Post by TeoBigusGeekus on 2008-05-31
Boot up in recovery mode and type
```
dpkg-reconfigure -phigh xserver-xorg
```
If it's a graphics problem, reconfiguring your settings will probably solve it.

---

### Post by Culito on 2008-05-31
Thanks,
But that didn't seem to work.  Although it may be a a wacky nVidia hiccup.

The last thing I was doing was screwing around with the permissions on the /tmp folder.  Could this be the problem?

I'm tempted to download Hardy and just do a fresh install, but is there a way to do this from the cd without wiping all the stuff on my hard drive?!

---

### Post by TeoBigusGeekus on 2008-05-31
It depends...
Do you have a separate /home partition?
If not, boot up with the live cd, backup and then proceed with the installation.

---

### Post by hal8000 on 2008-05-31
> **Culito said:**
> Thanks,
But that didn't seem to work.  Although it may be a a wacky nVidia hiccup.

The last thing I was doing was screwing around with the permissions on the /tmp folder.  Could this be the problem?

I'm tempted to download Hardy and just do a fresh install, but is there a way to do this from the cd without wiping all the stuff on my hard drive?!

The /tmp folder is owned by root but inside /tmp you will have several directories owned by your user ID and group ID.

It is possibly that X will not start if these are wrong permissions.

---

### Post by Culito on 2008-06-01
So I was able to boot with the live cd and replace the old temp folder with the one from the cd.

Crisis averted.

I still can't update to 8.04, though.  Update manager won't let me.  Authentication error...

One thing after another.

---

