---
title: "I don't have file permissions!"
date: 2007-06-14
forum: General Help
---

### Post by InternationalRescue on 2007-06-14
howdy, i am trying to retreive my files, as i cannot access the only account on my system. when i navigate to the files using the live cd it says i dont have access permission to view or copy the files to removable storage. is there any way of changing this?

---

### Post by jasonlfunk on 2007-06-14
If it is Ubuntu that you cannot log in to so you are forced to use a live CD you can reset your password by using single user mode.

In your GRUB menu, select one of the items that has Recovery Mode.
When you get a prompt type ```
passwd username
``` and reset the password.
Type ```
 shutdown -r now
``` to reboot and login.

If it is Windows that you cannot log in to, it may be a problem with reading NTFS. I don't know for sure though.

---

### Post by InternationalRescue on 2007-06-14
thanks for your suggestion, i should have been more specific though. i can log onto my ubuntu account, but the screen goes white from thereon. perhaps if there was a way of creating a new user account then i would be able to access the files from there...

---

### Post by jasonlfunk on 2007-06-14
A few things to try:

Once you get to your login screen, in the lower left corner click options and then try changing the Session to something different. It sounds like your X11 settings are messed up somehow. You should be able to log in to Fail Safe terminal. Once there you can create a new user with the adduser command. Though if it is your X11 settings that are messed up, adding another user probably won't help. When you get into the Failsafe terminal, you might then be able to copy your files as well.

---

