---
title: "Please Help, i cannot create a user without it getting deleted...."
date: 2007-05-27
forum: General Help
---

### Post by Aesir09 on 2007-05-27
 i honestly cannot create one, please help. when i boot my live cd it just doesn't work then when i go to check, the user profile i have created isn't even there...

---

### Post by H.E. Pennypacker on 2007-05-27
Because Live CDs run using RAM, when you restart your computer, everything you had done before is gone.  For that reason, don't bother saving anything, because it will be gone the next time you run the CD.

As far as creating users, why are you creating a new user account while running the Live CD?  If you are trying to create multiple users, first install Ubuntu on your hard drive, and then create multiple user accounts.

---

### Post by Lucifiel on 2007-05-27
If you want to install Ubuntu, remember these for guidelines:

1 partition set as linux-swap . It should be double the size of your RAM.

1 partition set as ext3. This will be your root folder: "/" and should be around 6 gb to 8 gb huge.

1 partition set as ext3. This will be your home folder. "/home" and should be around 9 gb or more.

---

