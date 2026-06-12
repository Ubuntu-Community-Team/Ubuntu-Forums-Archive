---
title: "PolicyKit/DBUS errors (The maximum number of active connections for UID 1000)"
date: 2008-05-03
forum: General Help
---

### Post by Daniel15 on 2008-05-03
Every so often, most of the applications in System -> Administration (eg. Network) won't start, showing this message:
> 
The configuration could not be loaded

You are not allowed to access the system configuration.


Running it from a terminal produces:
> 
daniel@daniel-laptop:~$ network-admin 

(network-admin:6953): Liboobs-WARNING **: The maximum number of active connections for UID 1000 has been reached

(network-admin:6953): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject
process 6953: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3280.
This is normally a bug in some application using the D-Bus library.

(network-admin:6953): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

** (network-admin:6953): CRITICAL **: Cannot create system bus: The maximum number of active connections for UID 1000 has been reached

(network-admin:6953): Gtk-WARNING **: Unknown property: GtkComboBox.items


(network-admin:6953): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed



Similar commands also produce the same "**The maximum number of active connections for UID 1000 has been reached**" error message. What is this maximum number of connections, and how can I fix this problem?

Thanks :)

---

### Post by Daniel15 on 2008-05-04
Bump...
This seems like a common problem, I get this on two PCs of different specs, and my friend gets it too

---

### Post by peitschie on 2008-05-04
I'm getting this issue for various things as well...

I just figured out that restarting the dbus daemon seems to fix this!  WTF?

Anyways, run the following command AFTER you logged in and see if that helps:
```

sudo /etc/init.d/dbus restart

```

How annoying...

---

### Post by peitschie on 2008-05-14
Ok... A shameless bump on this...

I have upgraded from Hardy Beta to Hardy, and this problem *seems* like a configuration issue but I have no idea how to solve it.  Is there any way to see all the current programs using DBus for any kind of connection?  I don't have this issue on the live CD (as far as I can tell), but I have it for any new users created locally on my PC. 

The problem manifests itself in that the user can open only a certain number of applications depending on the DBus before the error "The maximum number of active connections for UID 1000 has been reached" is displayed on the command line.  Generally its between 1 & 5 "users-admin" dialogs will do it (less if Firefox is running for some reason...).

Does anyone have any clues what might cause this?  If this fails a reinstall might be in order... which makes me feel rather dirty coz that sounds like a windows fix :D

---

### Post by peitschie on 2008-05-15
Okay... I have a fix.

For whatever reason it seems the default max_connections_per_user is NOT being set to 256 like it should (according to the source code!).  I have no idea why this is the case, and might investigate it further if I can be bothered.

Now for the fix... this is trivially easy once you work it out.  Do the following:
```
gksu gedit /etc/dbus-1/system-local.conf
```

And paste the following text into this opened file:
```

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<!-- for some reason this isn't being set properly in Hardy 15 May, 2008 -->
	<limit name="max_connections_per_user">256</limit>
</busconfig>

```

Now save this file, and then either restart the computer, or save all your work and do the following in a terminal:
```

sudo /etc/init.d/dbus restart

```
and then log out and log in again.

This fixes the issue (for me at least)... but I still have no idea why the programmed defaults aren't working though...

---

### Post by Daniel15 on 2008-05-18
Thanks for posting that, I'll be sure to try it :)

---

### Post by Ingenium on 2009-02-16
peitschie, I love you. I've had so many problems with my system since upgrading to hardy (and I'm on intrepid now), including recent updates that just broke the system. I've been searching forever on a way to fix them. They've all been fixed now. Thank you.

---

### Post by MadMax2 on 2009-05-16
I tried that fix except that during restart I left the CD Rom in. The icon appeared on the desk top > it opened >I closed it then did

sudo /etc/init.d/dbus restart

problems continued   ?

I did a reinstall and then upgrade to 9.04

---

### Post by peitschie on 2009-05-17
Hi MadMAx2... are you able to describe the program & exact error messages you're seeing?

---

### Post by MadMax2 on 2009-05-17
The first message was
Unable to mount J and K w (CD title.... the drive on the menu aquired this label)
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.

Possible causes include:
-the remote application did not send a reply
-the message bus security policy blocked the reply
-the reply timeout expired
- or the network connection was broken.

I tried a different CD data disk left it in and did a restart. The icon was on the desktop and it displayed.
Tried the original and it said:
Unable to Mount Volume 'J and K w'
Mount: block device /dev/scd0 is write protected, mounting read only mount: No medium found.


john@LoungePC:~$ ls -l /media

total 2

lrwxrwxrwx 1 root root 6 2009-04-17 19:22 cdrom -> cdrom0

dr-xr-xr-x 1 root root 2048 2006-03-13 13:30 cdrom0

the system log just said mounted/ unmounted (but I don't have a record)
I did a reinstall then decided to upgrade to 9.10.
Thanks.

---

### Post by peitschie on 2009-05-17
Hi MadMax... this is a different error than the one this thread was created to address sorry.  Hope the upgrade fixed it.

---

### Post by dlindster on 2010-08-30
peitschie, I freaking love people like you (which is so, so may awesome people around the world!) who spend a few minutes finding fixes and answers for newbs like me.

I did exactly what you said in response #5 in this thread and it worked perfectly!!   You're amazing.

My error was being generated by my trying to open a bookmark for sftp access to my home router while having a browser (Chrome in this case) open simultaneously.  I'm running Ubuntu 10.04, so I changed the entry line from "<!-- for some reason this isn't being set properly in Hardy 15 May, 2008 -->" and I simply replaced it with " <!-- for some reason this isn't being set properly in Lucid 30 Aug, 2010 -->"

I hope that's okay, but everything seems to work just great!  Thanks again.

---

### Post by Paul A C on 2010-11-09
I too had this error when trying toget a share from a Lubuntu (Maverick) PC to Windows samba share.

peitschie's 15 May edit fixed this. (although in Lubuntu you will find the file to edit is:-
/etc/d-bus-1/system.conf

Looks like a long standing problem.

(I did not get the problem with a Lucid Lubuntu install though, which seems strange)

---

