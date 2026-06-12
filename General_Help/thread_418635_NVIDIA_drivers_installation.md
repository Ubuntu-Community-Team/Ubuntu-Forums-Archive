---
title: "NVIDIA drivers installation"
date: 2007-04-22
forum: General Help
---

### Post by afterburner on 2007-04-22
Hi, I couldn't get my wireless to work, but I needed to install the NVIDIA drivers, so I downloaded the file on another computer from the NVIDIA site, and tried to run in in terminal by double clicking...I then got a message saying that I need to be in root to perform this particular operation, so I logged back in with root, but his time it said that I cant run the package in X...Now, I have no idea of how to run in NOT in X...Can anyone help me with this one?

The site said to type sh "name of package"...but this does not work

By the way this is for Ubuntu 7.04

Thanks

---

### Post by Crakie on 2007-04-22
Get yourself a copy of [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), it will do the job for you. Read the instructions well and be aware that the release might be a bit buggy, Feisty being so new and all (you'll need the unstable version).

---

### Post by dreadlord_chris on 2007-04-22
> **afterburner said:**
> Hi, I couldn't get my wireless to work, but I needed to install the NVIDIA drivers, so I downloaded the file on another computer from the NVIDIA site, and tried to run in in terminal by double clicking...I then got a message saying that I need to be in root to perform this particular operation, so I logged back in with root, but his time it said that I cant run the package in X...Now, I have no idea of how to run in NOT in X...Can anyone help me with this one?

The site said to type sh "name of package"...but this does not work

By the way this is for Ubuntu 7.04

Thanks

Boot into your regular user account. When the Desktop loads press **Control-Alt-F1**
This will bring up a console log in screen - enter you username & password here (same one to log into your Desktop (yes, you will be logged in twice)). Now enter (assuming you are using GNOME, if KDE change *gdm* to *kdm*:
```

sudo /etc/init.d/gdm stop

```
This will stop X so you can install the drivers. Now, do you remember where you downloaded that package too? Change to that directory.
```
sudo sh ./packagename

```
If everything goes ok to get back to your Desktop:
```

sudo /etc/init.d/gdm start

```
Remember to change the *gdm* to *kdm* if you are using KDE

---

