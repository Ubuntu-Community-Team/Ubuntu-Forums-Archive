---
title: "Hiding User Directories in /home"
date: 2008-01-17
forum: General Help
---

### Post by Frogbarf on 2008-01-17
I've noticed that when the File Browser is pointed at the /home directory, it shows all the subdirectories. As these are named per user ids, this reveals all the user ids on the system.

How can I prevent this from happening? If I take my machine in for work on it, the shop has a userid set up for them "MTI" so they can boot it up, but I don't want them to be able to even see that I have an admin id and a couple of ordinary user ids on it.

The whole point of Ubuntu's insistence that one have an admin ID you use instead of root is so anyone trying to hack their way in has to guess not only a password, but also the relevant user id. Showing all the user ids when the file browser points to /home seems to defeat this security technique.

The solution clearly lies in setting permissions properly, but...:confused:

1. What directory should I set permissions on? /home or /home/userid?

2. What should I set the permissions to?

3. Will this cause bootup problems?

---

### Post by geirha on 2008-01-17
On directories, the **r**ead permission means that you are allowed to list its content.
The e**x**ecute permission means you are allowed to descend into it. So, remove the read permission, but keep the execute permission for the users that shouldn't be allowed to list the content of /home ```
sudo chmod o-r /home
```

However, /home isn't the only place you can see the usernames. /etc/passwd needs to be readable by all, and it also contains all usernames. I think you'll get better security by simply convincing the users to use a proper password, one with at least one uppercase letter, one lowercase letter and one digit, and a password of at least 8 characters. That's (26+26+10)^8 combinations.

Also, you can have [John the ripper](http://www.openwall.com/john/) run a few days. If that prog is unable to crack your users' passwords, then your system should be pretty safe from password cracking.

---

