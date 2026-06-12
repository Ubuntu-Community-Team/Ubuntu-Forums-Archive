---
title: "I locked myself out of administration, please help me!"
date: 2007-06-19
forum: General Help
---

### Post by Edgeworth on 2007-06-19
I need to modify users on a non-admin account. I know my root password if it is needed.
Thank you in advance for any help you can give me.:D

---

### Post by dreadlord_chris on 2007-06-19
> **Edgeworth said:**
> I need to modify users on a non-admin account. I know my root password if it is needed.
Thank you in advance for any help you can give me.:D

Are you in an account that doesn't have access to **sudo**? Have you tried **su**? Not sure, you might be locked out of that too. If neither of those work - boot into Recovery Mode and do it from there.

---

### Post by Edgeworth on 2007-06-19
Sudo fails, su gets me into root. What do I do now?

---

### Post by firstlife on 2007-06-19
Easy. Open up a terminal, and run

echo $PATH

This should give you a list of folders. Look for /sbin and /usr/sbin. If they are in there then you can just use 

su

Otherwise you need to use

su -

notice the trailing '-'. That means use root's path. System programs are usually found in /sbin or /usr/sbin, so if it's not in your path, you have to use the full path of the app, ie /usr/sbin/adduser instead of adduser.

Anyways, that will help you find all the possible apps you can use, though I recommend running a graphical from the terminal.  And just use the man pages for more info (man adduser).  

If you need more specific help, ask more specific questions. Modifying users is  a broad subject. ;)

---

### Post by Edgeworth on 2007-06-19
I just need to somehow wind up with an administrator account that can be accessed with gnome. I cannot find any app in /sbin and /usr/sbin to do this by either creating or modifying an account so that it has administrating capacities. 
                     As always, thank you in advance for your time, patience and help, as well as thank you to Dreadlord and Firstlife for getting me this far, and for putting up with how new I am at this.

---

### Post by dreadlord_chris on 2007-06-19
> **Edgeworth said:**
> Sudo fails, su gets me into root. What do I do now?

```

usermod -a -G admin NAME

```
Replace NAME with your login name. This will add you to the admin group.

---

### Post by Edgeworth on 2007-06-20
Thank you, that worked perfectly! :D

---

