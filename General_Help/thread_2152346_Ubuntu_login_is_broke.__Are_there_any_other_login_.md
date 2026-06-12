---
title: "Ubuntu login is broke.  Are there any other login screen options?"
date: 2013-06-07
forum: General Help
---

### Post by UserJB on 2013-06-07
When I try to login to my ubuntu laptop, it only gives me the choice of a single username.  It doesn't allow me to login as a different user.  I've been trying to get this resolved on the other forum with no success.  It seems like the Ubuntu login screen doesn't allow for this and nobody knows how to fix it.  I guess the designers of ubuntu assumed that nobody would ever try to login as a different user.

 I wonder if there's a different way to login to ubuntu?  Is there?  Is there one that lets you type in the username, then password (like on every other Operating System)?  If so, how can I enable that?  Thanks.

---

### Post by CatKiller on 2013-06-07
The LightDM login screen is perfectly fine with allowing you to select from multiple users, as was the GDM login screen before that. Perhaps you haven't added your other users appropriately? Whether you use text entry or the face browser was configurable by theme in GDM. I don't know whether the same is true with LightDM, but it's probably worth investigating.

---

### Post by VanillaMozilla on 2013-06-07
Look around the system settings.  You should find a tool to manage user accounts.

---

### Post by UserJB on 2013-06-07
I added user accounts with the 'adduser' command-line tool.  I specified a UID of 504 and a GID of 504.  That account is not listed when I try to log into ubuntu.  There is no provision on the login prompt to type in the username.  However, the account is fine otherwise: I can 'su' to it, it has a home directory, etc.  There's just no entry for logging itno it from the main ubuntu login screen.

If I instead create an account with UID and GID over 1000, then the account is listed in the login screen.

This is either a bug, or a dumb feature.

---

### Post by steeldriver on 2013-06-07
The cutoff UUID should be defined in the lightdm.conf file i.e.

```

$ cat /etc/lightdm/users.conf 
#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
[COLOR=#0000ff]**minimum-uid=500**[/COLOR]
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

---

### Post by UserJB on 2013-06-07
That worked.  Thanks!

---

