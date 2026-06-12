---
title: "I need help with Users and Groups."
date: 2007-06-30
forum: General Help
---

### Post by alexv305 on 2007-06-30
I just re-installed my Ubuntu because I didn't want the 64 bit version. Now I made a mistake. I unchecked the box for "Administer Computer System" under users and groups for the only account I had on the computer. Then I restarted the computer and now I can't access the "Users and Groups" section of "System > Administration" and it also won't let me install all the updates because it says some require an administrator to install them. How do I correct this? Please help me, I need to add more users.

Thanks,
Alex V

---

### Post by mmmichael on 2007-06-30
Open a terminal (Applications>Accessories>Terminal) and type ```
gksudo users-admin
```. Then enter your password. This will open the users and groups window. Click on your user name and then on properties. Select the User Privileges tab and check Administer the System.

---

### Post by H.E. Pennypacker on 2007-06-30
When it asks you to enter the administrator's password, does your password work?  Enter your password (the password you entered when installing Ubuntu), and see what happens.

---

