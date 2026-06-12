---
title: "security issue"
date: 2016-08-30
forum: General Help
---

### Post by rybena on 2016-08-30
Hi
I am wondering about security with Ubuntu if I am able to reset my password if I forget it from a command line by holding shift down on reboot and heading to root promt. Doesn't this make it really insecure and that anyone can reset my password? Or is there something I am missing? Should I be putting a password on root?

---

### Post by Jimysbil on 2016-08-30
Root should always have a password.Every distribution is asking for a root password when it is getting installed.
If you know how to change your password from an other boot device either some exploit or a kernel vulnerability you could say it is not perfectly safe.But you have to ask yourself, what OS is perfectly safe??
The only better way to be safe from a password change without your permission is to encrypt your hard disk you have your OS installed.

---

### Post by yancek on 2016-08-30
Anyone with physical access to a computer can do this.  You don't seriously think this can't be done with other operating systems, windows for example.  If you want data secured, use encryption.    An obviously, don't give physical access to your computer to untrusted persons or leave it running unattended, particularly in public places.    Passwords, no matter how complicated, cannot prevent someone from accessing your data.  If you leave your computer unattended or allow an untrusted person access, they don't need any particular skills but a simple screw driver to remove the hard drive and they've got everything and all the time in the world to access it.

[http://www.pcworld.com/article/2988539/windows/if-you-forget-your-windows-admin-password-try-this.html](http://www.pcworld.com/article/2988539/windows/if-you-forget-your-windows-admin-password-try-this.html)

---

### Post by deadflowr on 2016-08-30
If someone other than yourself will have access to your PC, then you are better off setting up Full Disk Encryption.

You can, though, disable the recovery mode settings in the boot menu.
edit the the file (as root/sudo) /etc/default/grub, and remove the comment(remove the # symbol) for the line GRUB_DISABLE_RECOVERY="true"
then reload grub with sudo update-grub

Bonus points to adding a machine password to select boot devices, and set the hard drive as the boot device.
In this way if someone wanted to boot a livecd, they would need the password to change the boot device.
Of course, in the end this too can be reverted by anyone willing to open the machine's case and reset the cmos/bios, usually takes the removal of the cmos battery to do that.
(or if they have the time, flip around a jumper or two...)

Which of course leads back to use Full Disk Encryption, which will force the user to know the encrypted disk passphrase to actually ever make any changes.

---

### Post by QIII on 2016-08-30
> **Jimysbil said:**
> Root should always have a password.Every distribution is asking for a root password when it is getting installed.
If you know how to change your password from an other boot device either some exploit or a kernel vulnerability you could say it is not perfectly safe.But you have to ask yourself, what OS is perfectly safe??
The only better way to be safe from a password change without your permission is to encrypt your hard disk you have your OS installed.


Not quite true for Ubuntu.  By default, Ubuntu's root account is disabled due to having no password.  The account installing Ubuntu is automatically placed in sudoers and is an administrator who can use sudo to temporarily elevate their priviledge.

---

### Post by coffeecat on 2016-08-30
> **Jimysbil said:**
> Root should always have a password.Every distribution is asking for a root password when it is getting installed.

Er... No and no. In all the years I've run Ubuntu, I've never set a root password. There is no "should" about it. And not every distribution asks you to set a root password - Ubuntu being the obvious example of a distro that does not ask you to set a root password. 

I hope you are not confusing the root account with the administrative account which can access root privileges. More here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Jimysbil on 2016-08-31
> **coffeecat said:**
> Er... No and no. In all the years I've run Ubuntu, I've never set a root password. There is no "should" about it. And not every distribution asks you to set a root password - Ubuntu being the obvious example of a distro that does not ask you to set a root password. 

I hope you are not confusing the root account with the administrative account which can access root privileges. More here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

My mistake.All I had in my mind was the password every user has to give in order to get root privileges (with sudo).Yes, ubuntu,mint and other distributions do not ask a password for the user root but a password for the user we create in case we have to get root privileges.

---

