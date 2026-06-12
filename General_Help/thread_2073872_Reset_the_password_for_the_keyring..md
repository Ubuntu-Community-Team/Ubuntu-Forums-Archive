---
title: "Reset the password for the keyring."
date: 2012-10-20
forum: General Help
---

### Post by seubert on 2012-10-20
Accidentally entered a password for keychain, now suffer - every time you connect to an Internet request pops up the password. And how do the reverse operation - reset the password - do not know. In Ubuntu everything is done simply through the program from the "Keys and encryption", all the zest of the matter is that I have and there is lubuntu point "and Encryption Keys" no. Folder ~ / .gnome2/keyrings also discovered. Established a seahorse, but he does not see the existing keys What to do?

---

### Post by efflandt on 2012-10-20
You are not alone.  I have a tablet PC that can boot either Ubuntu or Lubuntu from SD card with a common /home partition.  And when configuring wireless at work, Lubuntu kept disconnecting wireless and at first I thought that it was asking for the wireless key again, but maybe it asked for the keyring password.  After I noticed that, it would not accept my system password to authenticate the network setting changes and just kept connecting and disconnecting wireless asking for authentication.

At home WiFi connects and remains connected for Lubuntu or Ubuntu, but I configured that sometime ago to connect automatically for anyone.

---

### Post by netipot on 2012-10-25
I also have keychain problem. However I have the password & even when I delete the message my connection works.

---

### Post by Abhinav Kumar on 2012-10-27
may be you have changed the password for your login in to the system.
If thats the case, enter your earlier system login password in login keyring.:)

---

### Post by vasa1 on 2012-10-27
> **efflandt said:**
> You are not alone. ...
Any idea if there's a bug we could "me too"?

---

### Post by vasa1 on 2012-10-29
Got this in the mail:
>  Hi,

If you have a problem to mount internal partitions, or if it asks for a password for network configuration, please try to install policykit-desktop-privileges, reboot, and try again.

Regards,
Julien Lavergne

Source: [https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html)

WFM! I hope this is relevant to the topic.

---

### Post by mark-wheadon on 2013-09-04
I have Lubuntu 13.04 installed and this problem. I haven't solved it, but I now know how to change the key ring password (to match my user password):

1) sudo apt-get install seahorse
2) Open a terminal and type seahorse, or find 'Passwords and Keys' in Preferences menu.
3) Click on the View menu and then click on 'By keyring', this shows a left side bar.
4) In the left side bar, under Passwords, right click on 'default' and choose 'Change Password'.
5) Enter the old password, then the new one twice (as prompted).
6) Reboot to ensure it all works wonderfully well.

---

