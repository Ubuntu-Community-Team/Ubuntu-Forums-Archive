---
title: "Cannot remove /etc/resolv.conf"
date: 2007-04-21
forum: General Help
---

### Post by Boffin13 on 2007-04-21
Hello.

Something strange is going on with my pc :(

Here is what 
ls -l /etc/resolv.conf 
gives:


-r--r--r-- 1 root root 49 2007-04-17 04:16 /etc/resolv.conf


I'm trying to delete it or to change his permissions from root, but whatever I try it gives me: 
rm: cannot remove `resolv.conf`: Operation not permitted
or
chmod: changing permissions to `resolv.conf`: Operation not permitted.


How can it be that even root cannot do anything with this file? And how can I solve the problem?


Thnx

---

### Post by mickbuntu on 2007-04-21
I am not understanding your question correctly exactly. But think your trying to login as "root". Root in ubuntu is disabled, it has some password too.  If your trying to delete a file you will need to use sudo  filename after your password prompt.    Deleting resolv.conf, seems really risky to me.  As it is an important network file. If I am  correct you should not drop the privileges of that file to  users. Your  giving crackers a much easier time.  If they compromise your user account no barrier at all in its simplest form will exist in your defense.

> **Boffin13 said:**
> Hello.

Something strange is going on with my pc :(

Here is what 
ls -l /etc/resolv.conf 
gives:


-r--r--r-- 1 root root 49 2007-04-17 04:16 /etc/resolv.conf


I'm trying to delete it or to change his permissions from root, but whatever I try it gives me: 
rm: cannot remove `resolv.conf`: Operation not permitted
or
chmod: changing permissions to `resolv.conf`: Operation not permitted.


How can it be that even root cannot do anything with this file? And how can I solve the problem?


Thnx

---

### Post by Boffin13 on 2007-04-21
No. I logged in as usual user.
Then I run "sudo su", enter password and trying to do anything with resolv.conf

Actually, I don't need to delete it, but to edit it, however the problem is that I cannot do with it anything :(
Even when I run
sudo vim /etc/resolv.conf
or
sudo rm /etc/resolv.conf
I get "permission denied" on it :(

---

### Post by sdowney717 on 2007-04-21
you can activate a root login!
click on system-administration-login window
select the security tab
click on 'allow local system admin login'

THEN click system-administration-users and groups
click root
click preferences
set a new password

click ok

you can now login with root

---

### Post by mickbuntu on 2007-04-21
Unless you love  vim, their is an easier program to do your most basic editing.  

Try:

sudo nano  /etc/resolv.conf



> **Boffin13 said:**
> No. I logged in as usual user.
Then I run "sudo su", enter password and trying to do anything with resolv.conf

Actually, I don't need to delete it, but to edit it, however the problem is that I cannot do with it anything :(
Even when I run
sudo vim /etc/resolv.conf
or
sudo rm /etc/resolv.conf
I get "permission denied" on it :(

---

### Post by Boffin13 on 2007-04-21
Some kind of misunderstanding is going on here.


I have no problem to login as root or to run sudo in usual login session. But the problem is that even when I AM ROOT, I cannot do anything with this /etc/resolv.conf file :(

---

### Post by mickbuntu on 2007-04-21
Then I honestly do not know  going pass question to someone with more skills. :?   It seems if your on top of the chain it  should work.

> **Boffin13 said:**
> Some kind of misunderstanding is going on here.


I have no problem to login as root or to run sudo in usual login session. But the problem is that even when I AM ROOT, I cannot do anything with this /etc/resolv.conf file :(

---

### Post by zvacet on 2007-04-21
If you are under your administrator account(username and password you set during installation)
you are in admin group and this should work 
```
sudo gedit /etc/resolv.conf
```
  

You can also try alt+F2  or install nautilus scripts
[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

---

