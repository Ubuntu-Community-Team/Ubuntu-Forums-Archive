---
title: "Display info prior to login prompt"
date: 2007-12-21
forum: General Help
---

### Post by btrichardson on 2007-12-21
Hello all,

As part of my company's Common Operating Environment, I'm required to display an info screen when someone logs into my machine.  I'm currently using Zenity to display the info screen, and I have placed the Zenity script in /etc/gdm/PostLogin/Default.  However, this causes the info screen to show up after a user has logged into the machine rather than before.  I'd like the info screen to pop up such that a user has to click ok before the login prompt will appear.  Is this possible?  Thanks! -- BTR

---

### Post by wormser on 2007-12-22
The /etc/issue.net file is the login banner that users will see when they make a networked i.e. telnet, SSH connection to your machine. You will find it in the /etc directory, along with a similar file called issue, which is the login banner that gets displayed to local users.  You probably want to make them both display your warning message.

/etc/issue.net
/etc/issue 

```
sudo gedit /etc/issue.net
```

---

