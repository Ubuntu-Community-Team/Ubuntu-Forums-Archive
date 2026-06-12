---
title: "[SOLVED] Give user permission to run commands as root"
date: 2008-02-24
forum: General Help
---

### Post by bmccorm2 on 2008-02-24
Hi everyone,

I am playing around with Superkaramba and the desktop widgets.  I am trying to get the widget to display the temperature of my HD.  If i open up a terminal and, as root,  type in the command "hddtemp /dev/sda" it works perfectly.  I am trying to give the user permission to run this command as root without typing in a password (so i can autostart the widgets when i login) and because i do not want to run superkaramba as root.  

Any help would be appreciated :)

Thanks!

---

### Post by toa on 2008-02-24
> **bmccorm2 said:**
> Hi everyone,

I am playing around with Superkaramba and the desktop widgets.  I am trying to get the widget to display the temperature of my HD.  If i open up a terminal and, as root,  type in the command "hddtemp /dev/sda" it works perfectly.  I am trying to give the user permission to run this command as root without typing in a password (so i can autostart the widgets when i login) and because i do not want to run superkaramba as root.  

Any help would be appreciated :)

Thanks!

Im using the CPU temp screenlet, its eays and no typing is required just enable it on startup.

---

### Post by bodhi.zazen on 2008-02-24
Well I think the answer to your question is to configure sudo.

user the NOPASSWD option

IMO it is best of you read up on this one as it impacts security.

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

	[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

If, after looking it over, you have a more specific question, come on back ...

---

### Post by jeffus_il on 2008-02-24
You need to use > visudo
to run the command > sudo /usr/sbin/hddtemp (dev) without having to enter a password.
 If you need help with visudo post again.

---

### Post by kerry_s on 2008-02-24
+1 use sudo

i do it all the time for several things.

---

### Post by jeffus_il on 2008-02-24
so add /usr/sbin/hddtemp to the last line

---

### Post by bmccorm2 on 2008-02-24
Thank you all for the quick replies.  

> Well I think the answer to your question is to configure sudo.
 
 user the NOPASSWD option
 
 IMO it is best of you read up on this one as it impacts security.
 
 [http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)
 
 If, after looking it over, you have a more specific question, come on back ...

I went to the above website and tried to change the /etc/sudoers file and I must have put the incorrect syntax down.  Now, whenever, I try to do 'sudo + command' I get an error referencing the changes i made in the sudoers file.  Since i now cannot gain root privileges, is there anyway to reset the sudoers file from a user perspective?  Keep in mind that i cannot do sudo anything...

Thanks again!

---

### Post by bodhi.zazen on 2008-02-24
You will need to boot to recovery mode then.

AS was suggested by jeffus_il, you should always use visudo to edit that file as this checks for syntax errors and prevents these kind of problems ;)

Also, if yo like, post the line you added and we can check the syntax ;)

---

### Post by bmccorm2 on 2008-02-24
> **bodhi.zazen said:**
> You will need to boot to recovery mode then.

AS was suggested by jeffus_il, you should always use visudo to edit that file as this checks for syntax errors and prevents these kind of problems ;)

Also, if yo like, post the line you added and we can check the syntax ;)

Thanks I don't know what i would do without you guys :)  So the sudoers file is fixed and i tried adding the line but i still can't run the command as a user.  Here is what i added to the file:
(i want to run hddtemp with the argument /dev/sda)

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
bryan ALL=NOPASSWD: /usr/sbin/hddtemp, /dev/sda     

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Thanks for all your help!

---

### Post by jeffus_il on 2008-02-24
You must run the command eactly like this ```
sudo /usr/sbin/hddtemp
``` [SIZE=5]**NOT**[/SIZE] ```
sudo hddtemp
``` or```
 hddtemp
```

---

### Post by bmccorm2 on 2008-02-24
> **jeffus_il said:**
> You must run the command eactly like this ```
sudo /usr/sbin/hddtemp
``` [SIZE=5]**NOT**[/SIZE] ```
sudo hddtemp
``` or```
 hddtemp
```

Thank you for your help.  It works fine now!!  One last question......how do i thank you guys for your posts?           *************Nevermind i found it :)

---

### Post by bmccorm2 on 2008-02-24
I'm sorry but I think my issue was solved before because my password was cached in the sudoers database :)  Now i get this:

```
bryan@bryan-pc:~$ sudo /usr/sbin/hddtemp /dev/sda
[sudo] password for bryan:

```

And this is the contents of the user section of my sudoers file:

```
# User privilege specification
root	ALL=(ALL) ALL
bryan ALL=NOPASSWD: /usr/sbin/hddtemp, /dev/sda, /usr/bin/adept_manager

```

I restarted my machine and it still asks for the password.  In theory i should be able to run the command without the prompt for the password right?  Did i do something wrong in my sudoers file?

Thanks again.

---

### Post by bodhi.zazen on 2008-02-24
You do not need /dev/sda as that is not a command.

Otherwise it looks good :(

---

