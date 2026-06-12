---
title: "Cannot unlock Shared Folders in Hardy"
date: 2008-06-11
forum: General Help
---

### Post by ed3120 on 2008-06-11
If I go to System -> Shared Folders and try to click unlock, I get the following message:

Could not authenticate
An unexpected error has occurred.

Is there any way to fix this, or is there a simple way to create a share via command line or editing a file?

---

### Post by iaculallad on 2008-06-11
Try to install the policy kit then try unlocking the Shared folder again:

```
sudo apt-get install policykit policykit-gnome
```

---

### Post by ed3120 on 2008-06-12
That fixed it...thanks!

---

### Post by dcparham on 2009-05-19
please pardon the latent interruption to your post, but i cannot view my Ubuntu box FROM windows network; advice from posts have not helped. also, [1]i cannot view Shared Folders unless i terminal: sudo shares-admin. then it does not allow unlocking[it is grayed out.] when i try your policy kit trick: , there is no change.  OR when i try to rightClick on folder>Sharing Options, i cannot Modify Share[grayed out.]

any ideas??

---

### Post by elykkyle on 2009-07-06
bump

---

### Post by michy99 on 2009-07-06
Instead of bumping an old thread, you will do better to start a new one.

---

