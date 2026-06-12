---
title: "Unknown Password"
date: 2007-09-01
forum: General Help
---

### Post by dgoldb1 on 2007-09-01
Today I decided I would change my password. So I went to Users and groups, selected my user account and added a number to the end of the current password, I did not re-type the entire password, just added to it.  Now I am unable to log in using the new and old password.  I think because I did not re-type the entire password, something got fowled up.

Any ideas?

Thanks.

---

### Post by merlinus on 2007-09-01
You cannot retrieve your password but you can reset it.

At the grub menu choose recovery mode. This will log you into a terminal as root.

to find out your username, if you do not remember that either:

```

ls /home

```

to set a new password:

```

passwd your_username

```

then reboot via

```

reboot

```

-merlin

---

### Post by X-626 on 2007-09-01
The "password" that shows up in the "Users and Groups" password field is not your real password.  I don't know much about what it is or why it does that.  Your password is encrypted one-way (meaning it shouldn't be able to be decrypted).  To change your password, you should have went to System->Preferences->About Me and clicked "Change Password".  Just follow the instructions merlinus posted and you should be able to change it.

---

