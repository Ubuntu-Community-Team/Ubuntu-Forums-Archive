---
title: "How do I log in as Root?"
date: 2007-02-05
forum: General Help
---

### Post by caffienda on 2007-02-05
I installed Edgy 6.10 from a torrent DVD.  While instllalling, it asked me for the user name and password.  It seems to have automatically set this to a "administrator" user setting.  

Is this the root account?  I noticed that there is also a root account, but I can't seem to log on as "root".  

The reason that I need to login as root, is that I am trying to add a serial number to VMWare Server.  I am getting this message:
"You do not have permission to enter a serial number. Please try again using the system administrator account."

How can I log in to fix this? What is my "real" root account?

---

### Post by Sef on 2007-02-05
Root is disabled by default because it improves security.  Use sudo in the terminal.  It allows temporary access to root.

Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo") for more information.

---

### Post by cmost on 2007-02-05
Logging into your system as root is not recommended!  If you must log in as root, then first do this in a terminal:

$sudo passwd
<enter a password for the root user>

Now, you should be able to drop into root by typing in any terminal:

$su

or

$su -

followed by the root password.

Good luck!

---

### Post by ardchoille42 on 2007-02-05
> **cmost said:**
> Logging into your system as root is not recommended!  If you must log in as root, then first do this in a terminal:

$sudo passwd
<ebter a oassword for the root user>




That effectively enables the root account and makes your system less secure. 

I have been using Ubuntu since Warty and have never needed to enable the root account. anything admin-related can be done via sudo.

---

### Post by etank on 2007-02-05
When I started using Ubuntu this was one of my biggest complaints. After a week or so it became a non-issue. Using sudo really is the way to go.

---

### Post by aysiu on 2007-02-05
Not only that, but if you really want to be "logged in" root, you don't have to create a password for it. Just do this: ```
sudo -s
```

---

