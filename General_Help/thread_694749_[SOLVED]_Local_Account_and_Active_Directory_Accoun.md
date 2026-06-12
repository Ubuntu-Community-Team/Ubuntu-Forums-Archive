---
title: "[SOLVED] Local Account and Active Directory Account the same"
date: 2008-02-12
forum: General Help
---

### Post by abuthemagician on 2008-02-12
Here is my Dilemma, I am using Gutsy BTW. 

When I set up Ubuntu I used my domain login for the first user added to the PC. Then I went through the steps and got it to authenticate with my 2003 Active Directory domain.

After realizing that i would need to use my domain login, i changed the Ubuntu user name to something else, and even changed the home directory.

Now when I log in i get all kinds of errors about files not belonging to me because the local account still uses those files. 

I am not really at a place where i could just reformat and reinstall and would love to be able to login as myself. Any help is appreciated.

---

### Post by taurus on 2008-02-12
When you changed your old $HOME to the new one, did you change the name of all the files in there?

Boot into recovery mode from GRUB menu and run

```
chown -R **newname**:**newname** /home/**newname**
```
Replacing the **newname** with your new login name.

Reboot and see if you get any error message about not the owner of your new $HOME.

```
shutdown -r now
```

---

### Post by abuthemagician on 2008-02-12
I just tried that and now i am stuck at:
Starting Kernel Log Daemon

---

### Post by taurus on 2008-02-12
Boot into recovery mode from the GRUB menu and post the outputs of these commands here.

```
ls -la /home
tail /etc/passwd
```

---

### Post by abuthemagician on 2008-02-12
i am using lynx to post this so see the attached files

---

### Post by abuthemagician on 2008-02-12
ok figured out that the ldap settings in nsswitch.conf were causing it to hang. Gotta get around that before i know if your original suggestion worked.

---

### Post by abuthemagician on 2008-02-12
Your suggestion solved my problem thanks!

---

