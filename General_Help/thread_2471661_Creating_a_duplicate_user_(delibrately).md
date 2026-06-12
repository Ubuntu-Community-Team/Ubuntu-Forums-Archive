---
title: "Creating a duplicate user (delibrately)"
date: 2022-02-05
forum: General Help
---

### Post by xyzulu on 2022-02-05
I'm well experienced with Ubuntu/Linux.. but never had to deliberately configure this particular setup.
Background: I'm working on this setup: [https://developers.cloudflare.com/cloudflare-one/identity/users/short-lived-certificates#3-ensure-unix-usernames-match-user-sso-identities](https://developers.cloudflare.com/cloudflare-one/identity/users/short-lived-certificates#3-ensure-unix-usernames-match-user-sso-identities)

Suggestions for doing this "nicely" on Ubuntu?
> You can create a user entry with duplicate uid, gid, and home directory to link an identity to an existing user with a different username. You will need to create a password for it separately and add it to the same groups to replicate permissions.

---

### Post by HermanAB on 2022-02-06
That sounds like bad idea to me…

If you want to experiment without messing up your regular host, you should at least make a different user account or preferably a virtual machine.  

In a VM, you can play all you like and once messed up, simply delete it and start over.

---

### Post by roshanmathewphilip on 2022-02-06
It'll be easier to just change your current username.
[https://www.configserverfirewall.com/ubuntu-linux/change-username/](https://www.configserverfirewall.com/ubuntu-linux/change-username/)

---

### Post by xyzulu on 2022-02-06
> **roshanmathewphilip said:**
> It'll be easier to just change your current username.
[https://www.configserverfirewall.com/ubuntu-linux/change-username/](https://www.configserverfirewall.com/ubuntu-linux/change-username/)

That won't work for my use case ;)

---

### Post by xyzulu on 2022-02-06
> **HermanAB said:**
> That sounds like bad idea to me…

If you want to experiment without messing up your regular host, you should at least make a different user account or preferably a virtual machine.  

In a VM, you can play all you like and once messed up, simply delete it and start over.

I've done just this..
After adding a new user and then editing /etc/passwd and editing the uid and gid of "alias" user (making sure they are listed AFTER) "real" user with the same values appears to work with no ill effects.

---

