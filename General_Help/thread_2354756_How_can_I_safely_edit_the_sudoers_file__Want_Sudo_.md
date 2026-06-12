---
title: "How can I safely edit the sudoers file?  Want Sudo to send mail when Sudo used."
date: 2017-03-06
forum: General Help
---

### Post by MechaMechanism on 2017-03-06
I am following this guide here; [https://likegeeks.com/linux-security-tricks/](https://likegeeks.com/linux-security-tricks/)

I need to do the following;

> Sudo Notification

You can configure sudo to send an e-mail when the sudo command is used by adding the following line to the file.

```
mailto yourname@yourdomain.com
```

And then modify when sudo sends that e-mail

```
mail_always on
```

I know that there is a help.ubuntu.com guide, but that talks about 8.04 and 8.10.  I want to use nano.  I assume cp /etc/sudoers /etc/sudoers.backup to start with right?

---

### Post by &amp;KyT$0P# on 2017-03-06
Nope.  The safer approach is to create a new file in [FONT=Courier New]/etc/sudoers.d[/FONT], then edit it using [FONT=Courier New]visudo[/FONT].

```
$ sudo cat /etc/sudoers.d/README
#
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
#       #includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# 
# Note that there must be at least one file in the sudoers.d directory (this
# one will do), and all files in this directory should be mode 0440.
# 
# Note also, that because sudoers contents can vary widely, no attempt is 
# made to add this directive to existing sudoers files on upgrade.  Feel free
# to add the above directive to the end of your /etc/sudoers file to enable 
# this functionality for existing installations if you wish!
#
# Finally, please note that using the visudo command is the recommended way
# to update sudoers content, since it protects against many failure modes.
# See the man page for visudo for more information.
#

```

---

### Post by MechaMechanism on 2017-03-06
> **halogen2 said:**
> Nope.  The safer approach is to create a new file in [FONT=Courier New]/etc/sudoers.d[/FONT], then edit it using [FONT=Courier New]visudo[/FONT].

```
$ sudo cat /etc/sudoers.d/README
#
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
#       #includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# 
# Note that there must be at least one file in the sudoers.d directory (this
# one will do), and all files in this directory should be mode 0440.
# 
# Note also, that because sudoers contents can vary widely, no attempt is 
# made to add this directive to existing sudoers files on upgrade.  Feel free
# to add the above directive to the end of your /etc/sudoers file to enable 
# this functionality for existing installations if you wish!
#
# Finally, please note that using the visudo command is the recommended way
# to update sudoers content, since it protects against many failure modes.
# See the man page for visudo for more information.
#

```

Ah; excellent, thank you.  I'll mark thread solved.

---

### Post by MechaMechanism on 2017-03-07
Here's exactly what I did for future reference and to help anybody else that has this desire to edit sudoers.

I wanted to get an email from the computer every time sudo was used successfully or not.  You need an MTA or mail transport agent.  I have Postfix on my computer.  There may be other ways to send an email; but that is beyond the scope of this thread.  I will show you what I did and I will assume you have an MTA already setup.

> The first command tells visudo where to create the file.  All edits should go to /etc/sudoers.d because this will make software updates more sane.
```
sudo visudo -f /etc/sudoers.d/mail_sudoers
```
File should look exactly like below.  Be sure to include double quotes.
```
Defaults    mail_always
Defaults    mailto="youremail@gmail.com"
```
visudo will set the proper permissions for you.  No need for chmod.

man sudo, visudo, sudoers will help greatly.
I've included a screenshot of what the email looks like.  Naturally the important bits after the @ have been removed.

---

