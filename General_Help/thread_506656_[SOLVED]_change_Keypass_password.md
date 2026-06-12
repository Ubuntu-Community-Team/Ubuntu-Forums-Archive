---
title: "[SOLVED] change Keypass password"
date: 2007-07-22
forum: General Help
---

### Post by MacDuff on 2007-07-22
When I was asked to enter a WEP key the first time, a keypass window opened and I was asked to enter a password.  I was in a hurry and entered something that I will not remember.

How can the master keypass password be changed?  If it cannot be changed, can a file be deleted and built again with a proper password?  If so what is the file and where is it located?

Thanks

---

### Post by lisati on 2007-07-22
Have you checked System->Administration->Keyring manager??

---

### Post by zanglang on 2007-07-22
No, for now GNOME doesn't support changing the master password. You can delete the keyring and reconfigure it from scratch though. Do:
> rm .gnome2/keyrings/default.keyring
And try to reconnect to your network again, it should ask for a new keyring password.

---

### Post by MacDuff on 2007-07-22
Thanks Zanglang.    The first thing I did was to check the keyring manager.  But it seems to default to a display that shows only passwords that have been set up.  I could not see the default password which led to my post.

When I got your reply, I thought "I must have missed something." and went back to the keyring manager.  After checking the menus, I realized that I had to press [F-9] to see ALL the keyrings.   I had looked at the [View] menu before and thought that the window was already showing all the passwords.  Pressing [F-9] displays the default password in another pane.   It seems a little obscure but...... thanks for helping me past that one.  

So much to learn..... so little time.

Mac

---

### Post by zanglang on 2007-07-22
Afaik changing the master password is only available if you have GNOME's Seahorse 2.19, which is still a testing version. It might've been a mistake or intentional omission at GNOME's part to hide the feature for security purposes perhaps. ;)

---

