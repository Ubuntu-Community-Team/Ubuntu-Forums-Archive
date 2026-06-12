---
title: "Switching users causes system to freeze"
date: 2015-09-16
forum: General Help
---

### Post by Hugo_Boss on 2015-09-16
I've recently installed latest Ubuntu GNOME 15.04. I have an administrator account with password which is functioning properly. I wanted to create a new standard account without password. (Yes I am aware of the security implications, no need to point it out) Using the ```
useradd myname
``` and ```
passwd -d myname
``` I thought I was done and tried to Switch users. Clicked on the newly created account and it asked password from me. I just pressed enter and the screen went into the booting screen (the one where '[ OK ] Done something here' messages are displayed). The last message was '[ OK ] Started *ACPI event daemon*.' Then the screen went black for couple seconds, then again intot he boot with ACPI and cycled infinitely there.
I restarted and tried to use the GNOME Users utility. I set the 'Enter password on first login' option. Switched users. Chose the account and it asked to enter password to login, just like before. (It didn't ask me to enter password that I would like to associate with the account.) Using blank password didn't help. So I couldn't set the password on first login.
Lastly I tried to supply the password right during creation of the account. Instead of 'Enter password on first login' I chose specific password. Switched users. Selected the newly created account and entered the password. The screen just went blank (with just the Login screen background and mouse). And stuck there forever. 

Am I made effectively unable to make new users?

---

