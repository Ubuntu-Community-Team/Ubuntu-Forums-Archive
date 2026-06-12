---
title: "Running programs as services (before login, as root)"
date: 2007-06-07
forum: General Help
---

### Post by tszanon on 2007-06-07
Hi,

I've been trying to find out how to run programs in a session-independent way (before login), but I have not found anything yet.
I read somewhere that I should put them in /etc/rc.local and change permissions on it, but nothing works. Here's the file:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ddclient
echo $(date) > /home/<my username>/Desktop/teste.rc.local.txt

exit 0
```
As you can see, I added **ddclient** and **echo** lines. After logon, I check and see that ddclient is not running and the file ~/Desktop/teste.rc.local.txt doesn't exist. If I run the script manually, everything works fine. Permissions:
```
-rwxr-xr-x 1 root root 371 2007-06-04 13:08 rc.local
```
The last line of the boot messages is something like "Running /etc/rc.local...[OK]" but nothing happens.

Can anyone help me, please?

---

### Post by mitch.c on 2007-06-08
Tested on both Dapper and Edgy. Works as expected (echo command).

I am not sure what you are expecting with ddclient, but I believe when run with no argument, it simply updates the dynamic dns service and quits. If you are going to all this trouble for ddclient, you shouldn't, it's installed as an init script which starts it as a daemon and periodically updates dns without interaction.

As for your echo command, are you using a variable for username?

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by tszanon on 2007-06-08
> **mitch.c said:**
> Tested on both Dapper and Edgy. Works as expected (echo command).
I must be doing something wrong, because I just rebooted (again) and nothing happens. :(
> **mitch.c said:**
> I am not sure what you are expecting with ddclient, but I believe when run with no argument, it simply updates the dynamic dns service and quits. If you are going to all this trouble for ddclient, you shouldn't, it's installed as an init script which starts it as a daemon and periodically updates dns without interaction.
Oh...if I had gone through Synaptic instead of downloading it from its webpage, surely I would already have that init script you're talking about... ](*,)
And this version of ddclient I have, when run without arguments, it acts as a daemon.
> **mitch.c said:**
> As for your echo command, are you using a variable for username?
No, no, I just didn't want to display my real username. ;) The only dynamic thing there is the $(date) thing, so I could know if it really worked.

I'm gonna remove this ddclient I have and install the one in the repositories. Thanks!
(but, anyway, why my rc.local doesn't work????)

---

### Post by Mr. C. on 2007-06-08
If your file did not get created, then the script didn't run, or there was a permission problem.

Try the logger program to send a log to syslog.  First, see that you can log a message successfully:

# logger Testing...
# tail /var/log/messages | grep Testing

If you get the testing message, then add the command to your rc.local file and try again.  After your boot, look for the testing message in /var/log/messages.

MrC

---

### Post by tszanon on 2007-06-11
> **Mr. C. said:**
> If your file did not get created, then the script didn't run, or there was a permission problem.

Try the logger program to send a log to syslog.  First, see that you can log a message successfully:

# logger Testing...
# tail /var/log/messages | grep Testing

If you get the testing message, then add the command to your rc.local file and try again.  After your boot, look for the testing message in /var/log/messages.

MrC
I did what you suggested and the message was logged, as expected. It seems that I was doing something wrong before...
I installed the ddclient from the repos, but I haven't even checked if a new service was created. Gonna check it as soon as possible.

Thanks again!

---

