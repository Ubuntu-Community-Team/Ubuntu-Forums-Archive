---
title: "Login as Root gaining Root privileges"
date: 2008-06-02
forum: General Help
---

### Post by Euphorion on 2008-06-02
How can I login as Root in order to carry out operations which require Root privileges such as installing dictionaries in OpenOffice using the Wizard.
   
  Ubuntu has after installation an account “Root” but it does not tell one what the password is. I have after the first installation of Ubuntu in “Users and Group” given Root a password and have created an account with Username=admin and all this did was to remove all administration authorizations, I could no longer add/remove software or unlock Users/Groups with the result that I reinstalled Ubuntu. In a thread in this forum a kind person told me why this happened and recommended I use the command “Adduser” and avoid Username=admin (gives one reason for thought doesn’t it!!).
   
  I have installed the required dictionaries in OpenOffice in a time consuming command line orgy in Terminal using sudo –i. But when on thinks that OpenOffice has a Wizard for this task and all it requires is that I log on as “root” but how, when the password is not revealed ? After my above experience with “Users and Groups” I am reluctant to try modifying my accounts now that Ubuntu is after 2 weeks work set up and installed the way I want it, the last thing I want is to reinstall the whole lot.
   
  Could someone please explain the philosophy behind the administration of Ubuntu and as to why “root” is sort of hidden and what I have to do in order to use wizards like the one above.

---

### Post by kesman on 2008-06-02
Can't you simply run the wizard with sudo in front of the command?
Also in terminal, you can use root's shell with
```

sudo su

```
and then you are root until you close the terminal.

---

### Post by Rocket2DMn on 2008-06-02
In Ubuntu, the root account is disabled by default to prevent people from just logging in as root and going about their business since this can be very dangerous.  That is why we use sudo - it gives you temporary superuser/root privileges which requires you to take that small extra step before performing adminstrative tasks that can potentially harm your system.  The root account CAN be enabled, but it is not suggested unless you really know what you are doing.  Using sudo should be good enough for anything you need to do, and if your system is damaged, you can run from a tty (full screen terminal) to fix the problem, or reboot into a root recovery terminal, the second option at the GRUB screen.

EDIT: see here - [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by Euphorion on 2008-06-02
Thank you for your kind reply, the problem here is that the Wizard is within OpenOffice (Files->Wizard->Insatal Dictionaries) and is written in the OpenOffice internal Macro Language it is not a script that I can start in a terminal.

From what has been said regarding Root Privilages during the short time of this post, I need a method in which I can get root privilages throughout the desktop for a temporary period of time in order to complete such tasks. That is, a sudo su that also applies for applications that are launched from the desktop or from within Programs such as OpenOffice.

---

### Post by aysiu on 2008-06-02
```
gksudo oowriter
``` should do it. I'm not on Ubuntu right now, so it could be ```
gksudo oowrite
```

As for why Ubuntu uses *sudo* instead of root, read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Rocket2DMn on 2008-06-02
You can try running Open Office with root privileges by opening a terminal and running
```
gksudo oowriter
```
This could prevent file ownership problems later if you create new files while using this root-owned instance of OO.org, but it should let you install what you need.  Then you can exit and start OO.org normally.

---

