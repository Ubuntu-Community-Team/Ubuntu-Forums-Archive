---
title: "Permissions problem as user"
date: 2007-05-17
forum: General Help
---

### Post by williemerwe on 2007-05-17
Hello,

I recently got cacti to work on Windows XP SP2.  One specific device that has to be monitored, gives an error and it was suggested that I try the cacti on Xubuntu.

I have everything I need - DualBoot Xubuntu on my Windows XP laptop to test.  Problem is that, with cacti, I need root privileges to all the /var folders and those I install.  When I use the dualboot, I'm logged into Xubuntu as user "ubuntu" which doesn't have the necessary privileges.  I tried to change users to root, but naturally there's a password...
Will it be possible to give me this password so that I can continue my tests?  I know cacti works with Ubuntu,but want to verify where my error is generated with that specific device.

Any assistance will be appreciated.

---

### Post by SeanHodges on 2007-05-17
Root is disabled in Ubuntu, you cannot log-in as root for security reasons. You have a couple of options:

- File a bug report on Launchpad, assuming you installed Cacti using the package manager. If you downloaded the program, consult its developers about your problem (filing a bug report or sending them an email should do it). Post a link to the bug report in this thread so people can find it easily.

- Run Cacti from the command-line, using the following command:

```
sudo cacti
```

Option 2 is the faster way to get going, but less secure, as you are running this Cacti program with root permissions. I recommend option 1 if possible, especially because it will help out other people who have the same problem in the future.

---

### Post by williemerwe on 2007-05-18
Thanks!
I'll try it and let you know what happens.

I installed all the requirements with "sudo apt-get install <application>".  Simple example - Apache installs /var/www/ where I'm supposed to extract the cacti to in order to use a URL //localhost/cacti.  I'm not able to change anything in the Linux folders, only the Home folder andso on.

Although a newby to Linux, I guess I'll try to find a spare machine and do a full Xubuntu install on that.

I'll let you know what happens where...

---

### Post by zvacet on 2007-05-18
You will not be able to run sudo without administrator privileges.Boot up in recovery mode and type (if ubuntu is your real username)

```
adduser ubuntu admin
```

This will put you in admin group and you will have superuser privileges.After that you can run sudo.

---

### Post by SeanHodges on 2007-05-18
> **williemerwe said:**
> Thanks!
I'll try it and let you know what happens.

I installed all the requirements with "sudo apt-get install <application>".  Simple example - Apache installs /var/www/ where I'm supposed to extract the cacti to in order to use a URL //localhost/cacti.  I'm not able to change anything in the Linux folders, only the Home folder andso on.

A few more points (I was in a rush before):

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo). This will give you a better understanding of what "sudo" is, and why you don't use the root user in Ubuntu.

If you have any problems installing or using Cacti, read and follow this howto: [https://help.ubuntu.com/community/Cacti?action=show&redirect=CactiHowTo](https://help.ubuntu.com/community/Cacti?action=show&redirect=CactiHowTo). The instructions are for an older version of Ubuntu, but I cant see anything that would be any different now. It will take you right from the installation, to logging into it. Theres also a FAQ further down if you hit any problems.

You can only write to files and directories inside your Home folder because being able to modify system files as a normal user is one of the reasons Windows is vulnerable to viruses. /var/www is an example of a directory that only an administrator should modify (by using the "sudo" program and typing their password to confirm they are allowed).

> Although a newby to Linux, I guess I'll try to find a spare machine and do a full Xubuntu install on that.

Let me know how you get on with that, and hope you have fun using Linux! Post another thread and let me know with a private message if you have any other unrelated problems.

---

