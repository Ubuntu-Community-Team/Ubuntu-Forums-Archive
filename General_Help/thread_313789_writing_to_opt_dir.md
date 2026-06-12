---
title: "writing to /opt dir"
date: 2006-12-06
forum: General Help
---

### Post by Boonerball on 2006-12-06
I have installed xampp and have tried to change the httpd.conf file but it will not let me save as I do not have permissions.

Also the directory /opt/lamp/xampp/httd.docs has the sample index.html is in this dir and I wish to change it for a test web page but I do not have permissions to write to this dir.

How do I get permissions to do so. I am logged in as the only account I have and I assumed this was root.

Can I set permissions or log in as root permanetly?

Or is there another way?

---

### Post by taurus on 2006-12-06
Actually, the account that you log in with the username and password is not really root.  If you need to write something outside of your $HOME directory, you need to use the sudo command...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Boonerball on 2006-12-06
looked at the link but I am set up as admin already. Basically the link you kindly gave says in users make sure I am set up as admin.

Any other ideas.

I set this up in windows very easily but I have not and will not go back to Windows thats for internet if Linux has problems and that is it.

---

### Post by taurus on 2006-12-06
If you need to edit a file outside your $HOME directory, you need to use "sudo" if you use nano or "gksudo" if you want to use gedit...

Applications -> Accessories -> Terminal
```
gksudo gedit  /opt/lamp/xampp/httd.docs
```
And if you want to move stuff around, then run

```
gksudo nautilus
```

---

### Post by rpkehoe on 2006-12-06
you are not root, you are sudo enabled.  You can either use sudo or su to become root, but you will first need to use sudo to change the root password 'sudo passwd root' to do this.  It is easier to just use sudo.

---

### Post by Boonerball on 2006-12-06
Thankyou that has worked and you made it really simple to under stand.
many many thanks

---

