---
title: "Different accounts not sharing time or flash"
date: 2008-02-05
forum: General Help
---

### Post by patrickaupperle on 2008-02-05
I've got flash and the correct time on my account, but the other account I created has neither. I try to change the time and it asks for a password. I put in the password for that account and it gives an error message involving sudo. If I put in administrator password than it says password is incorrect.

Any ideas?:confused::confused:

---

### Post by PaulFr on 2008-02-05
1. The time is set at a system level (and similarly the timezone), so I do not understand how the second user does not have the correct time. I also think Flash is installed at a system level, but am not sure.

2. I presume you are trying to change the time using sudo. By default, users who are members of the **admin** group are allowed to **sudo** - see the /etc/sudoers file for more details (or **man sudo**). So, if you want the second account to sudo, I would suggest add this user to the admin group by logging in as the first user, and ```
sudo usermod -G admin user2
```where you replace user2 by the name of your second user account. You can check whether it worked by ```
grep admin /etc/group
```.

---

### Post by patrickaupperle on 2008-02-05
Sorry for the misunderstanding but I was not using sudo. I right clicked on the time and clicked adjust. I dont know about the time and flash being at system level, but I do know that the times on the two accounts are different I'll get a screen of the error.

---

### Post by patrickaupperle on 2008-02-05
here it is
According to my account it was 9:49  at the time of the screenshot

---

### Post by patrickaupperle on 2008-02-05
Ok I fixed the time. There was a problem in the prefrences. Flash is still a problem though.

---

### Post by dhysk on 2008-02-05
get the .tar file for flash.  unpack the file and try to install it to /usr/lib/mozilla/plugins/

or just take the libflashplayer.so file thats in the .tar and copy it into that directory.

---

### Post by patrickaupperle on 2008-02-06
Ok, I just got a flash update from update manager now it works on all accounts.

---

