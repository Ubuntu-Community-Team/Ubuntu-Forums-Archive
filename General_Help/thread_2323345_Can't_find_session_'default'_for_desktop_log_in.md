---
title: "Can't find session 'default' for desktop log in"
date: 2016-05-04
forum: General Help
---

### Post by alex536 on 2016-05-04
Hi,

I have a puzzling issue on a newly installed 14.04.4 LTS. I configured it for nis and it works when I ssh into the machine. But if a user tries to log in on the desktop it fails with the "Can't start session" error". Here's the excerpt from the lighdm log:

> [+37.71s] DEBUG: Session pid=2481: Authentication complete with return value 0: Success
[+37.71s] DEBUG: Session pid=2028: Authenticate result for user user112: Success
[+37.71s] DEBUG: Session pid=2028: User user112 authorized
[+37.71s] DEBUG: Session pid=2028: Greeter requests default session
[+37.72s] DEBUG: Seat: Failed to find session configuration default
[+37.72s] DEBUG: Seat: Can't find session 'default'
[+37.72s] DEBUG: Session pid=2028: Greeter start authentication
[+37.72s] DEBUG: Session pid=2488: Started with service 'lightdm', username '(null)'
[+37.72s] DEBUG: Session pid=2481: Exited with return value 0
[+37.72s] DEBUG: Seat: Session stopped



The way things are working now, only local account can log in on the desktop. So far I reinstalled gnome-session without any improvement. 

Here's the nsswitch.conf:
> 
passwd:         nis compat 
group:          nis compat
shadow:         nis compat


hosts:          nis files mdns4_minimal [NOTFOUND=return] dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis


/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf: 


> [SeatDefaults]
user-session=ubuntu


/etc/lightdm/lightdm.conf.d/lightdm.conf: 
> 
[SeatDefaults]
greeter-show-manual-login=true
allow-guest=false


Could anyone advise me on what's the problem and how to fix this?

Appreciate any help.

---

### Post by ajgreeny on 2016-05-04
have a look to see if the package **ubuntu-session** is installed; it is needed if you are trying to use "ubuntu", ie unity, as your default session in the GUI.

---

### Post by cariboo on 2016-05-04
Moved to General Help.

---

### Post by alex536 on 2016-05-05
Hi. I verified that ubuntu-session is installed and is the latest version. Anything else I can check? The strange thing is that it works for the local accounts, but not for the NIS accounts. 


> **ajgreeny said:**
> have a look to see if the package **ubuntu-session** is installed; it is needed if you are trying to use "ubuntu", ie unity, as your default session in the GUI.

---

### Post by steeldriver on 2016-05-05
If it's only happening with non-local accounts, I wonder if the problem is related to AccountsService? something like these

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=690898](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=690898)

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/897212](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/897212)

---

### Post by alex536 on 2016-05-06
This could be related, but it seems that I have the latest version of the lightdm package. 

When lightdm complains that it "Can't find session 'default'", what exactly is it looking for and where? Maybe I can manually create the missing session file?


> **steeldriver said:**
> If it's only happening with non-local accounts, I wonder if the problem is related to AccountsService? something like these

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=690898](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=690898)

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/897212](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/897212)

---

