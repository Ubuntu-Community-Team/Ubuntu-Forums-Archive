---
title: "Adding a Linux user to a Samba AD DC."
date: 2021-03-07
forum: General Help
---

### Post by rsteinmetz70112 on 2021-03-07
I have been attempting to understand the samba-ad-dc setup and I've set up a AD DC using sambatool.
I decided to add a local Linux user to the machines and used 
```
sudo useradd
```
Which ran as expected and created an entry for <username> in /etc/passwd, /etc/group and /etc/shadow.
The entry in /etc/shadow has a '!' where the password hash would normally be. I assume that indicates a Kerberos passwd.
I then decided I need to create a password for that user and used ```
$sudo  passwd <username>
Current Kerberos password:
Current Kerberos password:
passwd: Authentication token manipulation error

```
I want to add this user as a Linux only local user not as a Samba AD user.
My questions are:
[LIST=1]
[*]Can I simply edit /etc/shadow and remove the '!' so I can enter a password and have that control this local user?
[*]How can I set or reset the 'Current Kerberos passwd'? I don't recall setting one when I set up the samba-ad-dc using sambatool and if I did I don't know it.
[/LIST]

I found a reference to kpasswd but running that command results in:
```
sudo kpasswd 
kpasswd: Cannot find KDC for requested realm getting initial ticket
```

I tried to su to the username
```
# su <username>
$ passwd
Current Kerberos password:<cr>
Changing password for <username>
Current password:<cr>
passwd: Authentication token manipulation error
passwd: password unchanged
```

---

