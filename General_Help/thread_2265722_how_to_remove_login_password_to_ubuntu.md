---
title: "how to remove login password to ubuntu"
date: 2015-02-17
forum: General Help
---

### Post by emcquinn8 on 2015-02-17
hi

i would like to remove the requiment to enter a password at bootup to my ubuntu system (12.04 lts). How can i do this? I searched the forums already but couldn't find any information.

---

### Post by Otto-C on 2015-02-17
Suggest look at User Accounts and change your account to Automatic login.
hth
otto

---

### Post by steeldriver on 2015-02-17
Go to "System Settings" (the cog/wrench icon)

Select "User Accounts"

Click the "Unlock" button and enter your password when prompted

Move the "Automatic Login" switch from "Off" to "On"


Or you can edit the lightdm.conf file by hand and set the 'autologin-user=' value to your username

---

### Post by emcquinn8 on 2015-02-17
many thanks. But now i am being asked for login keyring

---

### Post by emcquinn8 on 2015-02-18
and the software updates are failing too

---

