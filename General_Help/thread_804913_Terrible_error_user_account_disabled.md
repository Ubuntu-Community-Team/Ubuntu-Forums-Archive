---
title: "Terrible error: user account disabled"
date: 2008-05-23
forum: General Help
---

### Post by Jay I. on 2008-05-23
Hi! Just installed wine. After installation system rebooted (without even asking me) and when i tried to log in i was told - incorrect user name or password. Thanks god i've got another non-root account. So i logged in and tried to browse to /home/jay.However i found that my home directory was renamed to '/home/jay.disabled'.Both /etc/passwd and /etc/group seem to be ok. I tried to rename my home dir. back to /home/jay but that didn't help.Actually i had a problem with my account before - after i changed my user id and group id to 500 my account disappeared from the list displayed in System->Administration->Users and Groups. When i try to log in in recovery mode it tells me 'incorrect login' or something like this. I'm still a noob in working with shell so i wonder is there any way (preferably via command line) to recover user account under ubuntu??? I got absolutely stuck at this so i really need your help guys.

---

### Post by nick_h on 2008-05-23
It might be quicker to create a new user and copy the home directory across.

Accounts with a userid less than 1000 do not display in Users and Goups by default.  Is there any reason why you changed the userid to 500?

---

### Post by maybeway36 on 2008-05-23
You could edit /etc/passwd. Find the entry for your user and change the UID (first column?) from 500 to 1000. Also make sure the home directory (I think last column) matches.

---

### Post by bingoUV on 2008-05-23
wine generally does not trigger a reboot. I do not understand why your account might have been disabled but let us try :
1. Owner of your home directory : Is the account the owner of its home directory?
```

ls -l /home/<username>

```

2. Home directory as in /etc/passwd : See the second from right entry in /etc/passwd corresponding to your username. Is it /home/<username> ? It should be something like this
```

<username>:x:<uid>:<uid>::/home/<username>:/bin/bash

```

3. The account must be present in /etc/shadow. Open it as root, and see whether there is a line containing your username.

4. Now change the password
```

sudo passwd <username>

```


Hope one of these steps fixes your account.

---

### Post by mali2297 on 2008-05-23
Can you still do administrative tasks?

---

### Post by chrisccoulson on 2008-05-23
First of all, your user doesn't appear in the list when using the Users and Groups tool because your user ID of 500 is ***reserved for system and administrative users***. Normal users should have a user ID of >=1000 (same for group ID's too).

Nevertheless, I will try to help you fix your account. Because your other user cannot sudo, then you will need to boot to recovery mode. To do this, when GRUB loads (before the Ubuntu splash screen appears), press [ESC] (you are prompted briefly to press ESC anyway). You will then see the GRUB menu. Select the recovery mode option.

Once at a root shell in recovery mode, do the following:
```
passwd -S jay
```
You should see something similar to this (obviously with a different user name):
```
chr1s P 09/28/2007 0 99999 7 -1
```
If the second field ('P' in my example) is a 'L', you need to unlock your user account. To do this:
```
passwd -u jay
```
If the second field is 'NP', then you need to set a password:
```
passwd jay
```
...then enter your new password

Your user account should now be active. You also need to make sure that the home directory field in /etc/passwd matches the name of your actual home folder. To check the field in /etc/passwd:
```
cat /etc/passwd | grep jay
```
In my case, this looks like:
```
chr1s:x:1000:1000:Chris Coulson,,,,:/home/chr1s:/bin/bash
```
My home folder is /home/chr1s, so that is ok. If they don't match, then rename your home folder (you've already said that it has been renamed to '/home/jay.disabled').

Also make sure that the your user owns the home folder too. If you're unsure:
```
chown -R jay:jay /home/jay
```

You should be good to go then. But you really need to change your UID and GID to something sensible. To do this:
```
usermod -u <*UID*> jay
```
...where <*UID*> is a number greater than or equal to 1000, and not already used by anothe user on the system. Note, this still assumes you're in recovery mode. If you're not, then you'll need to use sudo. Changing UID will update ownership of your home folder automatically.

You also need to change the group ID:
```
groupmod -g <*GID*> jay
```
Generally, <*GID*> will be equal to your user ID (but make sure it doesn't equal other GID's on the system)

Once changing GID, you will need to update your user profile, as it will still contain the old group number:
```
usermod -g jay jay
```
...then re-correct group ownership on your home folder (as it will contain the old GID):
```
chown -R jay:jay /home/jay
```

Hope that helps!

---

### Post by Jay I. on 2008-05-23
Woooo-hooo! Changing password rules! Thank you guys! When so many variants are suggested it's hard not to solve a problem:) Now i'm only warried about what caused my password to change. System bug? or bug in some of root-priviledged apps. Is there any log file that may hold some helpful messages? What about my UID i changed it to be equal to my mandriva one. Actually i don't use mandriva any more so i'm gonna move all my docs to ubuntu and then change my UID to 1001.

---

