---
title: "Problems using administration tools"
date: 2007-04-24
forum: General Help
---

### Post by craz on 2007-04-24
I recently upgraded Edgy to Feisty and now I cannot use such system administration tools such as networking, users and groups, or adjusting the date and time.  When I try to do this I get the message: > [B]The configuration could not be loaded
You are not allowed to access the system configuration.[/B]  I have researched this quite heavily and already tried re-installing all dbus packages, as well as a couple others, I AM a member of the admin group, and in alacarte menu editor the commands DO start with gksu.  I have restarted my computer after trying all of these.  Also, when I try to start, for example, the networking administration tool, I get the following in the terminal:```
(network-admin:6639): Liboobs-WARNING **: There was an unknown error communicating with the backends: The name org.freedesktop.SystemToolsBackends.HostsConfig was not provided by any .service files

(network-admin:6639): Liboobs-WARNING **: There was an unknown error communicating with the backends: The name org.freedesktop.SystemToolsBackends.IfacesConfig was not provided by any .service files
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

```
Whats up, and what can I do about it?  Thanks in advance.

---

### Post by craz on 2007-04-24
Anyone else have this problem?

---

### Post by craz on 2007-04-25
*bump*

---

### Post by craz on 2007-04-26
Anyone???

---

### Post by craz on 2007-04-27
****bump****

---

### Post by taoufix on 2007-04-28
Same here. I just installed Edgy (not an upgrade)
I tried reinstalling system-tools-backends and all dbus packages I could find: dbus dbus-1-utils  libdbus-1-3  libdbus-glib-1-2  libnet-dbus-perl, but it didn't help.

---

### Post by craz on 2007-04-28
Strange.  Can anybody help us out?

---

### Post by taoufix on 2007-04-29
It worked after trying the following:
```

sudo aptitude install  libdata-dumper-simple-perl
sudo apt-get install --reinstall  data-dumper

```
Then rebooted

I dunno which one fixed it though ^_^

---

### Post by John Azelvandre on 2007-04-29
I am having the same problem on Edgy pre-installed on a Linux Certified laptop I just bought.  As you described, my main user is in the admin group (and the adm group, whatever that does).  But I don't even get an error message; Users and Groups just hangs, and I can't access other administrative tasks.  

I'll try the fix noted and report back the results.

---

### Post by John Azelvandre on 2007-04-29
The fixes above did not work for me.  More details on my symptoms:

System/Admin/Networking freezes when called, requiring force quit;

System/Admin/Users and Groups freezes when called, requiring force quit.

Other Admin tools, such as Date and Time work fine.

In Power Management, some options, like suspend and hibernate, aren't available to me, leading me to believe a permissions problem is responsible.

Networking and Users and Groups work if I log in as the root account.

The vendor pre-installed Edgy with the root account activated, I have had to leave it activated because of this problem with my main user, which I added while logged in as root.

I've already checked several times, and by all appearances, my main user is assigned to have full admin privileges and belongs to the requisite groups.

This is a very annoying problem.

---

### Post by craz on 2007-05-07
It is annoying.  I just tried taoufix's advice, and no luck.  I shouldn't need to log in as root every time I want to change administration settings.

The weird thing is, though, is that once I log into my account, if I try to access one of these admin abilities, it will ask for the admin password, like usual, THEN say I don't have permission.  If I try to access any of the admin tools again within that logon session, it will not promt for password but directly tell me that I do not have permission.  The whole thing is very frustrating.

---

### Post by taoufix on 2007-05-08
What's the output of the following command ? 
```

locate SystemToolsBackends

```

---

### Post by craz on 2007-05-09
```
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.GroupsConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.HostsConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.IfacesConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.NFSConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.NTPConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.Platform.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.ServicesConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.SMBConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.TimeConfig.service
/usr/share/dbus-1/services/org.freedesktop.SystemToolsBackends.UsersConfig.service
/usr/share/system-tools-backends-2.0/scripts/SystemToolsBackends.pl

```

---

### Post by taoufix on 2007-05-10
I thought you'll be missing some files, but I have exactly the same.

---

### Post by craz on 2007-05-10
Strange.  I am really lost, as of now I have tried every "fix" that I have come across.

---

### Post by craz on 2007-05-11
So does anybody have any ideas?  *Somebody* who upgraded must have had this problem.

---

### Post by craz on 2007-05-12
**bump**

---

### Post by craz on 2007-05-15
****************bump****************

---

### Post by craz on 2007-05-16
~~bump~~

---

### Post by Hadron Quark on 2007-05-17
*Bump* Same problems.

---

### Post by craz on 2007-05-17
This is really a problem as a system administrator.  Somebody must know the answer?

---

### Post by craz on 2007-05-19
*bump*

---

### Post by gmr on 2007-05-25
I have the same problem, but I use Debian Lenny. It must be something with the liboobs, but I don't know what it is :/

edit: I just update system-tools-backends and now it works!

```

system-tools-backends (2.2.1-2) to 2.2.1-3

```

---

### Post by craz on 2007-05-25
No go for me.  I tried reinstalling the Ubuntu version (only 2.2.0 is available) and it still doesn't work.

---

### Post by gmr on 2007-05-26
Try this:

[http://packages.debian.org/unstable/admin/system-tools-backends](http://packages.debian.org/unstable/admin/system-tools-backends)

---

### Post by nevernamed on 2007-05-28
I'm having this problem. I'm going to try the fixes that were listed and see if they help at all.
Anything under the system>administration doesn't work....

Tried the fix on the first page, didn't work. However, what do I need to download from the link above (from gmr)

---

### Post by rusty0101 on 2007-05-29
> **craz said:**
> This is really a problem as a system administrator.  Somebody must know the answer?

I don't know if this is 'the' answer, but it helped for me. Somewhere along the line I 'stopped' dbus. From that point on I was not able to get the services applet to come up. To get the services applet to come up again, I executed the command 

```
sudo /etc/init.d/dbus start
```

and I once again had a running dbus. I was then able to "System > Administer > Services" and re-check the 'System communication bus (dbus)" service to run in the future.

I don't know if this will help anyone else, but it was annoying to me, and my evidence that the service was not running was related to the fact that when I did an apt-get remove on the system-tools-backends as well as the apt-get install for the set of software it unloaded, one of the messages in the session was related to failures in attempting to re-attach to the dbus. 

I am about to reboot to make sure that the changes stick. Hopefully I will remember to follow up here.

-Rusty

{Edit}
Additional notes. After reboot I still do have a functioning Services applet. Now it does not prompt for a password. 

A bit of feedback to the people who created this applet, a 'restart service' button would be nice. Additionaly a recommendation or bit of information regarding each service would be handy as well. Is it necessary to have both hplip and cupsys daemons running? Even if I don't have any multi-function printer/scanner/fax machines anywhere in my network? Bluetooth device management is nice, how about some pointers on where someone could find out what bluetooth devices are in the area to decide which if any should be connected. Likewise Hard disk tuning is a really nice application to run if you want to get better response from hard disks that support the advanced features it supports, but to get the best results you should probably tune the settings. I'm thinking that there are probably a few people who would think it is a great idea to be able to know where to tel postfix how to go about sending e-mail as well. While I like screen very much, I'm unsure as to why it is listed as a service. are there advantages to having the screen application launched as a service vs launching it from the command prompt? Will it keep track of what applications or screens were running before a reboot and restart them?

Additionally the 'Help' button at the bottom of the applet provides misleading information. It describes the 'check box' as indicating whether the service is running or not. In reality the check box indicates whether the service is supposed to be running. After manually starting dbus as described above there was no check box in the System communications bus (dbus) service entry.
{/Edit}

---

### Post by siddhadev on 2007-05-30
I had the same problem with Ubuntu 7.04. This worked for me: 

* search for **system-tools** in Synaptic Package Manager 
* Select "Mark for Complete removal" for all installed packages, Apply
* then "Select for installation" only the **system-tools-backends** and **xubuntu-system-tools**
* Apply

---

### Post by craz on 2007-05-30
Thanks for the suggestions everybody.  I will try all listed fixes now and update soon.

---

### Post by jdmcg on 2007-06-04
> **taoufix said:**
> It worked after trying the following:
```

sudo aptitude install  libdata-dumper-simple-perl
sudo apt-get install --reinstall  data-dumper

```
Then rebooted

I dunno which one fixed it though ^_^

After much, searching, scouring and looking everywhere, this solved the problems I was having with gedit,  root gui, and other admin things freezing up. Wooooooooot!!!!!!   THANK YOU!!!!

---

### Post by gundumfx on 2007-08-23
i have the smae problem i think that we have to reinstall our os

---

### Post by gundumfx on 2007-08-23
> **craz said:**
> It is annoying.  I just tried taoufix's advice, and no luck.  I shouldn't need to log in as root every time I want to change administration settings.

The weird thing is, though, is that once I log into my account, if I try to access one of these admin abilities, it will ask for the admin password, like usual, THEN say I don't have permission.  If I try to access any of the admin tools again within that logon session, it will not promt for password but directly tell me that I do not have permission.  The whole thing is very frustrating.

i am having the same problem but one more thing does this happen to you i can not go to USER AN GROUPS in my ubuntu so do you know how to fix that an when i try to go there it freezes
so try to help an i will too

---

### Post by ashmew2 on 2007-12-13
> I don't know if this is 'the' answer, but it helped for me. Somewhere along the line I 'stopped' dbus. From that point on I was not able to get the services applet to come up. To get the services applet to come up again, I executed the command 

```
sudo /etc/init.d/dbus start
```

and I once again had a running dbus. I was then able to "System > Administer > Services" and re-check the 'System communication bus (dbus)" service to run in the future.


Man , You're a genius !!
I recommend every1 to try this fix (Im on Edgy 32 Bit )  , Thanks !!!

---

### Post by sinami on 2008-01-16
i have this problem and i tried this solution:

"I had the same problem with Ubuntu 7.04. This worked for me:

* search for system-tools in Synaptic Package Manager
* Select "Mark for Complete removal" for all installed packages, Apply
* then "Select for installation" only the system-tools-backends and xubuntu-system-tools
* Apply"
	
but services and users and groups have disappeared

i have gusty amd64..and on the feisty everything worked

---

### Post by sinami on 2008-01-16
:confused::confused:

---

### Post by sinami on 2008-01-17
:(

---

### Post by sinami on 2008-01-17
Resolved with removal and installation gnome-system-tools

---

### Post by Kelli on 2008-01-19
> **rusty0101 said:**
> I don't know if this is 'the' answer, but it helped for me. Somewhere along the line I 'stopped' dbus. From that point on I was not able to get the services applet to come up. To get the services applet to come up again, I executed the command 

```
sudo /etc/init.d/dbus start
```

and I once again had a running dbus. I was then able to "System > Administer > Services" and re-check the 'System communication bus (dbus)" service to run in the future.




Just wanted to note that this worked for me as well!  I ended up in the situation with a fresh (but turbulent!) Gutsy install to a laptop, and I don't know how I got into it, but using the above command in a terminal got me out of it.  I am now able have administrator access in the gui.  Thanks very much, Rusty!

---

### Post by sochbat on 2008-01-21
Yeap.

Worked for me as well.

I accidentally turned off DBUS in services, so i had to restart it.

Thanks!

---

### Post by fiftyMIPsparc on 2008-07-02
I am having this issue as well. None of the previously mentioned fixes worked for me. Also, I can use gksudo to open gedit, but if I try to open a file it abruptly quits and refuses to start as root again until reboot. Related? :confused:

---

