---
title: "how to add an new user from digitalocean sever"
date: 2014-08-14
forum: General Help
---

### Post by dellboy on 2014-08-14
hi ok i made an digitalocean sever to day i login to ssh and isntalled the ubuntu desktop with 

sudo apt-get update

then sudo-apt get ubuntu-desktop

i have the full ubuntu desktop but i only have an guest  account so my chanings are not being saved how do i get to make an new user so i can save changes ?

---

### Post by nerdtron on 2014-08-14
I don't get it why need a GUI on a server install?

You logged-in via ssh right?
Then create a user.
sudo adduser -m username

Then set the user password
sudo passwd username

Add this user to the sudo group to be able to use sudo privileges.
sudo usermod -a -G sudo username

Now you should be able to login via ssh using the new account.

---

### Post by dellboy on 2014-08-14
beacise i want to remote desktop into the computer so i can do somting on it ok i done that but when i login to the remote desktop that is not an user i can login as  ?

---

### Post by andrewsomething on 2014-08-14
Hi!

Like nerdtron mentioned, you just need to create a normal user. DigitalOcean droplets only have a root user by default. So on the command line, run:

```
sudo adduser -m username
sudo passwd username
sudo usermod -a -G sudo username
```

This will create a new user that you can login with instead of the guest account.

Let us know how it goes!

---

