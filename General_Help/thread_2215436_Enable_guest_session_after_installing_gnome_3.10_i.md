---
title: "Enable guest session after installing gnome 3.10 in Ubuntu 13.10"
date: 2014-04-06
forum: General Help
---

### Post by CRIMPS on 2014-04-06
I had been having some desktop environment issues using Unity.  So, I uninstalled that and then installed Gnome 3.10.  Things are running smoothly.

My issue.  The login window no longer offers the choice for logging in as a guest, which is used by our babysitter.  I see the options on how to enable/disable when using lightdm, but I am not using lightdm, instead, using gdm.  I suspect the guest session is still enabled, but the guest and remote sessions simply are hidden.

I was looking through the /etc/gdm/*.conf files and the options, here, are a little different.  Before I completely destroy the settings in these configuration files, I thought I would pose the issue to the masses.  Google didn't readily supply a solution.

Thanks.

---

### Post by monkeybrain20122 on 2014-04-06
I don't know about gdm. But for some reasons if I log into the second DE (tested with gnome-flashback and lxde) and log back to Unity and THEN try to log into guest session it results in blackscreen. It appears to have something to do with graphic card and driver. In an Intel machine this always happens, in a Nvidia machine only happens with nouveau but not the proprietary driver But there is no issue logging in and out of guest session if have not logged into the guest session first. I don't remember whether I got blacksceen if I log in and out of guest session first and then switch desktop. I have since removed the second desktop so can't test now. This happens in 13.04 and 13.10.

A bug was filed somewhere and I had added an 'affect me too' but I don't remember where it is now.

---

### Post by CRIMPS on 2014-04-07
> **monkeybrain20122 said:**
> I don't know about gdm. But for some reasons if I log into the second DE (tested with gnome-flashback and lxde) and log back to Unity and THEN try to log into guest session it results in blackscreen. It appears to have something to do with graphic card and driver. In an Intel machine this always happens, in a Nvidia machine only happens with nouveau but not the proprietary driver But there is no issue logging in and out of guest session if have not logged into the guest session first. I don't remember whether I got blacksceen if I log in and out of guest session first and then switch desktop. I have since removed the second desktop so can't test now. This happens in 13.04 and 13.10.

A bug was filed somewhere and I had added an 'affect me too' but I don't remember where it is now.

i'm not having a "blackscreen" type problem.  I simply need to figure out how to enable the guest account.

---

### Post by OneLookup on 2014-08-08
Just create a new "standard" user. Call it "guest" and set it to login with or without a password.
No matter you use gdm or something else you will see your new added user when prompted to login.

Here is an example on how to add a user (See "Add User Account" section) : [http://thelinuxstartup.com/2014/01/30/managing-users-in-ubuntu-13-10/](http://thelinuxstartup.com/2014/01/30/managing-users-in-ubuntu-13-10/)

---

### Post by coffeecat on 2014-08-09
Ubuntu 13.10 is now past end of life and unsupported.

Thread closed.

---

