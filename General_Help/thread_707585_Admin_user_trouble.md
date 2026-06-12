---
title: "Admin user trouble"
date: 2008-02-25
forum: General Help
---

### Post by Geran on 2008-02-25
When the install of my new 7.10 Gutsy system finished, my starting admin user did not exist! I went into recovery mode and found that it really didn't exist anywhere, not in /etc/group, /etc/shadow or any of the rest. And now when I try to use root user, I can't seem to create it with adduser or useradd at all. Please help.

---

### Post by danwood76 on 2008-02-25
The root account is disabled in ubuntu by default.
it is there but as I say disabled, you can find how to enable it by searching these forums.

---

### Post by bodhi.zazen on 2008-02-25
:lolflag:

Ubuntu uses sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

To become root, use 

```
sudo -i
```

or 

```
gksu nautilus
```

Use gksu (or kedus if Kubuntu) for graphical apps.

---

### Post by sisco311 on 2008-02-25
in recovery mode:

create new (normal)user:

```
adduser username
```


add user to administrator group:
```
usermod -a -G admin username
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Geran on 2008-02-25
I don't mean the root user, I mean the starting user that you make up during the instillation.

---

### Post by Geran on 2008-02-25
Not quite working...

---

### Post by Geran on 2008-02-25
[QUOTE=sisco311;4403405]in recovery mode:

add user to administrator group:
```
usermod -a -G admin username
```

This returns "User [username] does not exist."

---

### Post by sisco311 on 2008-02-25
please post the output of:
```
cat /etc/passwd
```
and
```
ls -al /home
```

---

### Post by Iowan on 2008-02-25
You did  **adduser username** first?

---

### Post by Geran on 2008-02-26
No, I didn't, I need to adduser then usermod?

---

### Post by sisco311 on 2008-02-26
if you have a user replace username from the command with the users user name, else you need to create a new user.

example:
```
usermod -a -G admin geran
```

if you have a user but you don't know the users password you can change it:
```
passwd <username here(geran)>
```

---

