---
title: "permissions"
date: 2008-06-01
forum: General Help
---

### Post by tripacer on 2008-06-01
I have the latest version loaded and am trying to set up file sharing. The system says I don't have permissions to create a share, I'm the only user and have admin permissions. How do I get permissions or log in as root, since the setup did not ask for a root password ?

---

### Post by drs305 on 2008-06-01
> **tripacer said:**
> I have the latest version loaded and am trying to set up file sharing. The system says I don't have permissions to create a share, I'm the only user and have admin permissions. How do I get permissions or log in as root, since the setup did not ask for a root password ?

To start the admin privileges you access root by preceeding the command with 'sudo'. It will then ask for your password, which you won't see as you are typing but it's there. Hit enter once you have typed it in.

---

### Post by mbeach on 2008-06-01
You should be able to right click on the folder, and select "Sharing Options".  Is that what you tried, or are you using another method?

For the root permissions, look up 'sudo'.
good reading:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tripacer on 2008-06-01
> **mbeach said:**
> You should be able to right click on the folder, and select "Sharing Options".  Is that what you tried, or are you using another method?

For the root permissions, look up 'sudo'.
good reading:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

 Problem is in the GUI it does not ask for a password, it just denies access ! I read the above link and in the GUI is basically says to input your password, BUT it does not ask for it !

---

### Post by mbeach on 2008-06-01
You might need to log out and back in again.  Looking at the posts toward the bottom of:
[https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus-share/+bug/212098](https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus-share/+bug/212098)
seems you are not the only one.

---

### Post by drs305 on 2008-06-01
> **tripacer said:**
> Problem is in the GUI it does not ask for a password, it just denies access ! I read the above link and in the GUI is basically says to input your password, BUT it does not ask for it !

If you open the app you are using from the command line, begin it with sudo. For instance, you can open a nautilus window with root powers by starting it in terminal with 
```
gksudo nautilus
```
Now anything you do in that application will be as root.

For text editing, it works the same way with gedit:
```
gksudo gedit
```

It is preferred to use 'gksudo' instead of 'sudo' when opening gui-based apps.

---

### Post by tripacer on 2008-06-01
> **mbeach said:**
> You might need to log out and back in again.  Looking at the posts toward the bottom of:
[https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus-share/+bug/212098](https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus-share/+bug/212098)
seems you are not the only one.

 That did it, logged out and back in and bingo !

 Thanks
 !

---

