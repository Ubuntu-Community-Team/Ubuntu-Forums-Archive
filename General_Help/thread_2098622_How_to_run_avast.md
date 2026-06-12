---
title: "How to run avast?"
date: 2012-12-27
forum: General Help
---

### Post by Androzani1 on 2012-12-27
I have installed avast for linux via the deb package on the avast website. When I click the link in the menu to start the programme, nothing happens, no terminal, no gui, nothing. When I try
#```
update-avast
```
nothing happens. It's almost as if the icon is installed, but not the actual programme itself. Help?

---

### Post by Pjotr123 on 2012-12-27
It seems you're new with Linux.... You don't need antivirus in Ubuntu:
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

Relax, you're running Linux. :cool:

---

### Post by Rex Bouwense on 2012-12-27
It is probably a true statement that an anti-virus program is not needed when running a Linux OS.  However that being said you can still install one.  I found this:
[http://ubuntuforums.org/showthread.php?t=1977781](http://ubuntuforums.org/showthread.php?t=1977781)
which may assist you in running Avast.  While I do not run an AV program either, there are some people who deal with other people who have not yet seen the light and still use Microsoft Windows whose computers are at risk when it comes to evil virus programs.

---

### Post by GameX2 on 2012-12-27
I use Avast under Windows 7, and for a free antivirus, I'm really satisfied;
When I heard Avast was availible on Linux, I was curious and installed it.  Never managed to do anything with it, and I had a lot of trouble to simply uninstall the software.

Never using Avast on Linux again! #-o

I then read about BitDefender for Linux.  I think their statement is kind of... extreme.
[http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html)

> Linux is no longer immune to security threats

There *are* a few viruses and malicious scripts under Linux, but I would say an antivirus isn't required - I have trouble to actually *find* one!

---

### Post by Rex Bouwense on 2012-12-27
Last time I read, there were somewhere around 50 viruses and malware that would technically affect a Linux OS.  I don't believe that any are active.  I was once told that a Linux OS is like a room with all of the windows and doors locked.  For a virus or malware to get in and do any damage, it would have to have your permission.  Not sure if that is technically correct but it sure sounds good.

---

### Post by The Spectre on 2012-12-27
You might want to give ClamTk a try...

[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

---

### Post by Androzani1 on 2012-12-27
Ok guys, I have it installed, but the databases won't update. Any ideas?

---

### Post by Androzani1 on 2012-12-27
Forget it, I'll just uninstall avast and use clam. Thanks for your time.

---

### Post by JosephBeck on 2012-12-27
> **Androzani1 said:**
> Forget it, I'll just uninstall avast and use clam. Thanks for your time.

Don't worry, it isn't hard. I use Avast for Linux too. The point isn't so much for protecting your own computer from viruses but protecting anyone you send files to, as the files may have viruses that can effect windows users. 

Have you registered your copy of avast! with the key they send you in an email?

I personally do not use terminal commands to run it and prefer to use the user interface which you can find by searching in the dashboard.


If you still want to use terminal the command "avast --help" will give you all the commands needed. Just remember it will not work unless registered.

---

### Post by BertN45 on 2012-12-27
I run avast and it does find viruses, since some of the files stored on the network drive are coming from Windows or intended for Windows. After installation of Avast it did find 8 infected files, some of them were in the Thunderbird Inbox folder.
The program is old and not updated for a long time, but the virus definitions are up-to-date. To get the program running you have to do two things:
- Register it and use the key sent by Email.
- In the terminal do: "sudo echo 128000000 >/proc/sys/kernel/shmmax"

That last one is needed to have enough memory to store the virus definitions.

---

### Post by mrjava on 2012-12-27
Why even run Avast on a linux environment? It's unnecessary....if you really do want antivirus protection, use clam.

---

### Post by JosephBeck on 2012-12-27
> **mrjava said:**
> Why even run Avast on a linux environment? It's unnecessary....if you really do want antivirus protection, use clam.

Many people prefer Avast, and the point isn't to keep a linux computer safe but clean files to prevent viruses from getting on windows computers you send files to which Avast does well. Avast is one of the top free antivirus softwares for Windows which is why most people like to use it when starting out in Linux.It is also one of the top recommended on Linux as well.

---

### Post by VinDSL on 2012-12-27
> **Androzani1 said:**
> I have installed avast for linux via the deb package on the avast website. When I click the link in the menu to start the programme, nothing happens, no terminal, no gui, nothing. When I try
#```
update-avast
```
nothing happens. It's almost as if the icon is installed, but not the actual programme itself. Help?

SHM is set too low in Ubuntu (and many other distros).  To fix this:

[INDENT]Open a terminal
sudo gedit /etc/sysctl.conf
Add **[COLOR="Red"]kernel.shmmax = 128000000[/COLOR]** on the last line.
Save & reboot.[/INDENT]

This is how my /etc/sysctl.conf looks:

```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#

**[COLOR="Red"]kernel.shmmax = 128000000[/COLOR]**

```

This is the result:

```

vindsl@Zuul:~$ sudo sysctl -a | grep shm
[sudo] password for vindsl: 
kernel.shm_rmid_forced = 0
kernel.shmall = 2097152
**[COLOR="Red"]kernel.shmmax = 128000000[/COLOR]**
kernel.shmmni = 4096
vm.hugetlb_shm_group = 0
vindsl@Zuul:~$ 

```

---

### Post by Androzani1 on 2012-12-28
I reinstalled and have it working now, thank you :)

---

### Post by chin2 on 2013-09-16
Hi guys!

I am in need of help here too. Firstly, please no one  reply by saying that I don't need an antivirus with Linux. At this  point, that is irrelevant. I need to get this application to run as it  should do, more as a point of personal pride than because I need an  antivirus! So someone please be a legend and help me to the finish  line.. :D

So, here is what I have done so far:

I'm running a fresh install of Ubuntu 12.04

I installed avast.
$ wget [http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb)
$ sudo dpkg -i avast4workstation_1.3.0-2_i386.deb

I ran it in terminal, by typing "avast", and the prompt came up to enter the registration code. I went to the website, registered, entered the code, everything seemed to go fine. I used the command "avast-update", and it downloaded an update so far as I could see. But the launcher icon still just flashed and did not open the avast GUI.

So, I rebooted, avast was gone from the launcher, and now "avast" in terminal returns:
$ avast
/usr/bin/avast: 178: /usr/bin/avast: /usr/lib/avast4workstation/bin/avast: not found

However I can run:
$ avast-update
Checking for virus signature updates...
No updates available at this time.

Does this mean avast is successfully checking for virus definitions? Regardless, I want the GUI to work, so it doesn't help me much..

When I look for the help menu:
$ avast --help
/usr/bin/avast: 178: /usr/bin/avast: /usr/lib/avast4workstation/bin/avast: not found

However, "man avast" does take me to the avast manual.. But, all the possible commands listed there that I try return the same thing:
/usr/bin/avast: 178: /usr/bin/avast: /usr/lib/avast4workstation/bin/avast: not found

So, next I tried this:

Open a terminal
sudo gedit /etc/sysctl.conf
Add **[COLOR=Red]kernel.shmmax = 128000000[/COLOR]** on the last line.
Save & reboot.

And now:

$ sudo sysctl -a | grep shm
kernel.shm_next_id = -1
kernel.shm_rmid_forced = 0
kernel.shmall = 2097152
kernel.shmmax = 128000000
kernel.shmmni = 4096
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
error: permission denied on key 'vm.compact_memory'
vm.hugetlb_shm_group = 0

Is what is returned..

I tried reinstalling using gdebi:

me@me-VGN-NS10L-S:~$ sudo gdebi avast4workstation_1.3.0-2_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 


avast! antivirus for Linux
 The on-demand scaner which combines excellent detection rates
 with high speed and superior stability of the antivirus engine.
Do you want to install the software package? [y/N]:y
(Reading database ... 175104 files and directories currently installed.)
Preparing to replace avast4workstation:i386 1.3.0 (using avast4workstation_1.3.0-2_i386.deb) ...
Unpacking replacement avast4workstation:i386 ...
Setting up avast4workstation:i386 (1.3.0) ...
Processing triggers for man-db ...

me@me-VGN-NS10L-S:~$ 

Still it will not load the GUI from launcher, and all commands return:
/usr/bin/avast: 178: /usr/bin/avast: /usr/lib/avast4workstation/bin/avast: not found

I try an uninstall and reinstall:
$ sudo apt-get purge avast4workstation*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package avast4workstation_1.3.0-2_i386.deb
E: Couldn't find any package by regex 'avast4workstation_1.3.0-2_i386.deb'
E: Unable to locate package avast4workstation_1.3.0-2_i386.deb.1
E: Couldn't find any package by regex 'avast4workstation_1.3.0-2_i386.deb.1'
E: Unable to locate package avast4workstation_1.3.0-2_i386.deb.2
E: Couldn't find any package by regex 'avast4workstation_1.3.0-2_i386.deb.2'

And it cannot be found.. 

I do a reinstall regardless, I have the same set of issues, I go in circles, I get mad, I come to forums, I ask for help.....

Some wonderful L337 h4x0r (sarcasm) please come to the rescue, and save my sanity!

Thanks in advance!

PS. Started pissing around with this too.. [http://penguinpills.sourceforge.net/avast.php](http://penguinpills.sourceforge.net/avast.php) , but now I am tired and can't be arsed to open that can of worms too. HELP :(

---

### Post by chin2 on 2013-09-16
BTW, I only started using Linux this morning, so please be gentle with me! No L337 sp34k. ;)

---

