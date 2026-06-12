---
title: "How to make standard user an admin user?"
date: 2012-12-15
forum: General Help
---

### Post by joemartin on 2012-12-15
How do I make an existing standard user an admin user?  Thank you.

---

### Post by chadk5utc on 2012-12-15
> **joemartin said:**
> How do I make an existing standard user an admin user?  Thank you.

Typically the first user setup is the "Admin" you can add more is this Desktop or server?
Choose System -> Administration -> Users and Groups.

Select Add to add your new user. When you have completed the wizard, choose your new user and click on account type and change from Desktop user to Administrator.

---

### Post by joemartin on 2012-12-15
Desktop


You have to create new user?  Can't change existing to admin?

---

### Post by steeldriver on 2012-12-15
It depends what version and flavor of Ubuntu you are using. Basically you add the user to the appropriate super-user group: up to and including Ubuntu 11.10 that was 'admin'; from 12.04 on it is 'sudo'. You can use the appropriate GUI users + groups tool or from a terminal either

```
sudo gpasswd --add <*username*> sudo
```or

```
sudo adduser <*username*> sudo
```or

```
sudo usermod -aG sudo <*username*>
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zombifier25 on 2012-12-15
> **joemartin said:**
> Desktop


You have to create new user?  Can't change existing to admin?

It's only an example. There's no need to. But generally, if you want to change a standard user to an admin user, there should be another admin user to authorize the process.

---

