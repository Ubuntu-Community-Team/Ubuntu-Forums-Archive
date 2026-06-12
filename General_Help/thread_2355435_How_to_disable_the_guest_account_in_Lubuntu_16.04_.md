---
title: "How to disable the guest account in Lubuntu 16.04 LTS"
date: 2017-03-12
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-12
I would like to know how to safely disable the guest account in Lubuntu 16.04 LTS, just like in Ubuntu.

---

### Post by &amp;KyT$0P# on 2017-03-12
Try running this in Terminal -
```
sudo bash -c "echo '[SeatDefaults]
allow-guest=false' > /etc/lightdm/lightdm.conf.d/noguest.conf"
```
Then reboot.

Does it work?

---

### Post by John_Patrick_Mason on 2017-03-12
It worked! Now, how do I re-enable it if I have guests over?

---

### Post by &amp;KyT$0P# on 2017-03-12
> **John_Patrick_Mason said:**
> Now, how do I re-enable it if I have guests over?
Delete [FONT=Courier New]/etc/lightdm/lightdm.conf.d/noguest.conf[/FONT] and then reboot.

---

### Post by John_Patrick_Mason on 2017-03-12
Also, before I log in now, where it shows each users' names, it gives me the option of logging in using the "other" account. What is this account supposed to do? Is it similar to the guest account?

---

### Post by &amp;KyT$0P# on 2017-03-12
You didn't have that option before?

"Other" is not an account.  Click it, you will see it just offers the option to manually enter a username and password.

---

### Post by John_Patrick_Mason on 2017-03-12
[QUOTE=halogen2] You didn't have that option before?[/QUOTE]  To tell you the truth I haven't used this computer in a while, but if it's like you say then I'm not worried about it. Thanks again.

---

### Post by &amp;KyT$0P# on 2017-03-12
You're welcome. :KS

---

