---
title: "Can i separate right as on Android?"
date: 2021-08-07
forum: General Help
---

### Post by jondonald on 2021-08-07
Is it possible to setup an OS as android: user can use it without any passwords, install apps, etc. But they have no rights to supersu.

My parents use android and they have no problem. But Linux asks the password for each action. I'm not sure give a user rights of root or let them work under root is correct decision. But to give them root password is the same mistake.

Maybe i can give them rights to work, but only in their user account?

---

### Post by yancek on 2021-08-07
Ubuntu should not ask for a password for each action.  I use it daily and can go for many days, even weeks without a request for a passwor.  Exception is login password which I use. The password is generally needed only when there is some modification to system files.  Your example above of installing software is one.  You can give different users sudo privilege for this action by using the visudo command to edit /etc/sudoers.  An example entry is shown at the bottom of the page at the link below.  If you want to give privilege to the apt command from the terminal, the path is:   /usr/bin/apt

[https://itectec.com/ubuntu/ubuntu-cant-non-admin-users-install-software/](https://itectec.com/ubuntu/ubuntu-cant-non-admin-users-install-software/)

Giving users, particularly new users complete root/sudo privileges is a very bad idea.  It may make some things easier but without much knowledge, they can easily destroy the entire system.

---

### Post by QIII on 2021-08-07
Hello!

If you are talking about having to re-enter your password after some time of inactivity in the terminal, or between terminal sessions, or between GUI activities that require a password, then the behavior is expected.  That is by design and it is for security.  What if someone gained access to your device and wanted to make changes either for nefarious or mischievous reasons?  In general, allowing passwordless commands usually reserved for su/root is a very bad practice and comes with terribly dangerous security risks.

This behavior can be modified by slight modifications to a configuration file.  Somewhat more detailed, but also possible, is allowing certain commands to be run without a password, say by automated processes.  But those commands must be very carefully selected and the risk compared against the value of convenience.

But please [B]take some time to consider the security ramifications and havoc that may be wreaked on the device.
[/B]

---

### Post by grahammechanical on 2021-08-07
Have you taken responsibility for updating that system? When I use Ubuntu Updater it does not always ask for a password unless a new Linux kernel is part of the update/upgrade. Of course, updating through the terminal always requires a password.

Do you have the operating system set up for automatic login? What do your parents use the computer for? There are various web sites that many people use that require passwords. Often the web browser (Firefox) will ask if it can save the password. And there are password managers that do something similar.

As I am 74 years old I have decided not to save the various passwords I need but to enter them each time a password is needed. I do this to keep my mind working. Yes, it means I have things written down and that is said to be not a very secure practice. I think that it is more secure than being stored on the computer.

Regards

---

