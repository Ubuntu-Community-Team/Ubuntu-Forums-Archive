---
title: "Ubuntu Remote Access/Login/Log-out Needed!"
date: 2015-04-20
forum: General Help
---

### Post by Stece_The_Dev on 2015-04-20
So just a little information, I am setting up a new web/game server and I have multiple administrators wanting to connect to the computer machine. I am wondering "Hmm well I might want to access the computer machine at the same time whilst they are working, so what can I do? I could use Team Viewer, but then only one user will be able to configure and manage the system at that time." I was wondering is there any login/logout system like a virtual machine we can use so we can all be connected at the same time? We could use putty but we want it more secure than SSH. Plus we are using a GUI so chaps I am in need of your help :) Thanks all you will probably be seeing me around here quite a lot! Ha-Ha! 

Many Thanks!

---

### Post by TheFu on 2015-04-20
I don't know of anything more secure than ssh using ssh-keys. Never allow password for internet connected systems that is TOTAL FAIL.  There are ssh server config settings to control this stuff.  Don't give them admin writes for the entire system - just for the game. That can probably be accomplished by using normal UNIX groups.  Since UNIX began, groups and file permissions have been used for this purpose.

Lots of ways to lock down ssh further - 
* install fail2ban (blocks brute force attacks)
* block all external IPs except from the people who should have access
* put an iptables rule that slows down access from IPs with repeat login failures

GUI? GUI!  Run x2go, if you must, but that needs to use the same ssh-key-based authentication.

If you want more security with ssh, you could force 2FA with something like google-authenticator or ubikey. That is what PAM authentication is handy for.  But it would still be ssh for the encryption which is world-class as far as anyone knows. Exactly what sort of login do you think is more secure than key-based ssh?  If the keys are stored on a smartcard, I don't know anything better. Please educate me.

---

