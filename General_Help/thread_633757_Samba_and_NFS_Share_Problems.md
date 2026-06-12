---
title: "Samba and NFS Share Problems"
date: 2007-12-06
forum: General Help
---

### Post by koolkatkiwi on 2007-12-06
Hi. I asked a question in this thread:

[http://ubuntuforums.org/showthread.php?t=631453](http://ubuntuforums.org/showthread.php?t=631453)

because I was trying to get Samba working on my two networked computers. I tried the advice on that thread, but now the system is broken. Here's what happened:

Before: Both my computers could access the internet, via a modem/router that they are both plugged into. After: Only the main computer has internet access (I hadn't messed with this one). The second one - the one I tried these tutorials on - has lost all connectivity and networking capacity.

Before: Both my computers could see each other via Samba, and see all the folders on the other computer, but not access the files in the folders. I was almost there with Samba - just needed to sort out the permissions. After: Neither computer can see the other computer at all, nor see or access any of the files on the other.

There is something seriously wrong here. I wish I had left it alone. Is there anythiing like "System Restore" in Ubuntu?

What I want to do is to share the "home" folder of the main user on each computer, with the other computer. Just share all the files on both computers, basically, and the printer that's on the main computer.

With a lot of these tutorials, they have you adding users and groups, making a folder to share, and sharing this folder. That's all very well, but I don't want to add folders or users. I just want to share the "home" folder of each main user, on each of the computers - I only have one user on each computer anyway. But first I need to get it back to the way it was before yesterday, so I can at least access the internet with the second computer.

Which files should I show the contents of here, for troubleshooting? Any ideas? Thanks in advance.

Cheers,
Kath:KS

---

### Post by HermanAB on 2007-12-06
Have a look at this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)
The intent of that guide is to help you find the problems and fix them, using very simple tools.

Also visit the Samba web site and read the Official Howto a few times.

Note that Samba is NOT easy.  You have to read the official docs.  Other tutorials should be used with care.  Always try to understand what you are trying to accomplish before executing a command.

Cheers,

Herman

---

### Post by Aseld on 2007-12-07
Can you point us toward the tutorials that you followed, and/or the steps that you took to get where you are?

---

### Post by koolkatkiwi on 2007-12-07
Thank you Herman. I have saved your debug howto onto a CF card, and the first 11 pages of the Official Samba Howto onto the card as well (it doesn't seem to be available as a download of the whole thing at once). I will take these howtos down to the other computer and test some things on it. 

Here's the output of a couple of tests I did on this (the main) computer, as the howtos suggested. It looks like there's something wrong with the configuration of this computer's samba setup as well.

kath@bill:~$ smbclient -L bill
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE
kath@bill:~$ sudo testparm /etc/samba/smb.conf
[sudo] password for kath:
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[kath]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[kath]
        path = /home/kath
        read only = No
        guest ok = Yes
kath@bill:~$ 


Thanks for taking the time to look at this. I really want to get a handle on all things Linux. It's hard to know where to start. I'm a long time computer user - fairly competent as a user, but sadly lacking in the technical side. 

Cheers,
Kath:KS

---

### Post by koolkatkiwi on 2007-12-07
> **Aseld said:**
> Can you point us toward the tutorials that you followed, and/or the steps that you took to get where you are?

Hi Sharif. I did this video tutorial on networking:

[http://tinyurl.com/3avurg](http://tinyurl.com/3avurg)

then I tried to install and set up Firestarter as per this suggestion:

"About firewalls: If you've got a GUI, you should probably install firestarter and unblock ports 137-139 and 445 for incoming connections. If you want to set up a basic iptables firewall yourself, see this tutorial: http://wiki.vpslink.com/index.php?title=HOWTO:_Quick_n%27_Dirty_IPTables-Based_Firewall" 

I wanted to unblock the ports suggested, but couldn't figure out how to do that, and besides, Firestarter didn't install properly. I believe there is already a Firewall built into my router anyway, so possibly there would be a conflict there. Probably the best thing would be if I were to paste the results of the testparm on the downstairs machine into a message.

Cheers,
Kath:KS

---

### Post by koolkatkiwi on 2007-12-07
I found that Official Samba Howto in pdf form, which will make it a lot easier to take it down to read on the other computer.

Here's what happened when I tried to install Firestarter:

koolkatkiwi@kath:~$ which iptables
/sbin/iptables
koolkatkiwi@kath:~$ firestarter
koolkatkiwi@kath:~$ sudo firestarter
Password:
Error reading file /etc/firestarter/inbound/allow-from: No such file or directory
Error reading file /etc/firestarter/inbound/allow-service: No such file or directory
Error reading file /etc/firestarter/inbound/forward: No such file or directory
Error reading file /etc/firestarter/outbound/deny-to: No such file or directory
Error reading file /etc/firestarter/outbound/deny-from: No such file or directory
Error reading file /etc/firestarter/outbound/deny-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-to: No such file or directory
Error reading file /etc/firestarter/outbound/allow-from: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Warning: External interface previously configured not found
Warning: Internal interface previously configured not found
You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

Firewall script saved as /etc/firestarter/firewall
Adding Firestarter startup hook to /etc/dhclient-exit-hooks
Internal network device sit0 is not ready. Aborting..
Doing :sudo -u koolkatkiwi firefox [http://www.fs-security.com/docs/:](http://www.fs-security.com/docs/:)
koolkatkiwi@kath:~$ 


Also, when trying to start firestarter, I got the message: "Failed to start the firewall. The device sit0 is not ready. Please check your network device settings and make sure your internet connection is active."

Sooooo - I think I have really screwed something up here. :confused:

Cheers,
Kath:KS

---

### Post by seandiggity on 2007-12-07
I'm not sure if you created that /etc/init.d/firewall.sh file from the tutorial I posted in this thread [http://ubuntuforums.org/showthread.php?t=631453](http://ubuntuforums.org/showthread.php?t=631453) but I edited it to emphasize that ports 80 (HTTP), 22 (SSH), 443 (SSL), 21 (FTP), and 25 (SMTP) might need to be unblocked if you're running a general purpose web server.

---

### Post by seandiggity on 2007-12-07
I just read through this whole thread, and it's a bit odd that you couldn't install firestarter.  You may want to just uninstall it and take the "quick and dirty" approach.

All it required for me was a few minutes and the creation of a blacklist.txt, whitelist.txt, and a firewall.sh file.  I'll paste my comments from the other thread below:

> **About firewalls:** If you've got a GUI, you should probably install firestarter and unblock ports 137-139 and 445 for incoming connections. If you want to set up a basic iptables firewall yourself, see this tutorial: [http://wiki.vpslink.com/index.php?title=HOWTO:_Quick_n%27_Dirty_IPTables-Based_Firewall](http://wiki.vpslink.com/index.php?title=HOWTO:_Quick_n%27_Dirty_IPTables-Based_Firewall)

If you only want to allow incoming samba connections, make sure you change the "ALLOWED" line in the firewall.sh from the tutorial above to look like this:

```
## Specify ports you wish to use.
#
ALLOWED="80 137 138 139 445"
```

**IMPORTANT EDIT:** I don't think I emphasized this enough but IF YOU USE THE COMPUTER FOR ANYTHING ELSE BUT SAMBA, YOU'LL NEED THOSE PORTS UNBLOCKED. PORT 80 IS ESPECIALLY IMPORTANT. Ports 22 (SSH), 25 (SMTP), 443 (SSL), and 21 (FTP) might be necessary too if you have a general-purpose server.

---

### Post by koolkatkiwi on 2007-12-07
Well . . . you probably won't believe this. Today I booted up this second computer, and it is now able to access the internet again. What's more, I can now see the other computer again via the Windows Network icon. I still can't access the files, but at least I can see the folders again. There are a few files not in directories - just saved in the home folder itself. I can open these files in OpenOffice.org, but can't change them. The folders themselves (My_Documents, etc.) are not accessible.

Here's the result of a couple of tests on this computer today:

koolkatkiwi@kath:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[kath@bill]"
Processing section "[allusers]"
Processing section "[kat]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[kath@bill]
        path = /home/koolkatkiwi
        read only = No
        guest ok = Yes

[allusers]
        comment = All Users
        path = /home/shares/allusers
        valid users = @users
        force group = users
        read only = No
        create mask = 0660
        directory mask = 0771
        guest ok = Yes

[kat]koolkatkiwi@kath:~$ smbclient -L kath
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE
koolkatkiwi@kath:~$ 

        path = /home/kat
        read only = No
        guest ok = Yes
koolkatkiwi@kath:~$ 

So, since it seems to be working OK at the moment, I think I'll just read through the Official Samba Howto, plus the Samba By Example doc, which looks promising. I'll take Herman's advice and not be messing with things until I understand what I'm doing, and otherwise try to stick to the Absolute Beginner's Forum where I belong!

If you do have any ideas after seeing the results of this testparm, please tell me, but at this stage, I'm not desperate, having got my internet connection back. It was hell, having to fight my husband for time on the computer yesterday! I will study. See ya later.

Thanks, guys, for your help and advice. :popcorn:

Cheers,
Kath:KS

---

