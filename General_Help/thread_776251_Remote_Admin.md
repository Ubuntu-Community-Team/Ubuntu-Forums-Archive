---
title: "Remote Admin"
date: 2008-04-30
forum: General Help
---

### Post by gordee78 on 2008-04-30
Hi Folks,

New to ubuntu, and relatively new to linux.  First and foremost let me say that ubuntu has got to be one of the best linux experiences I have had so far!

I'm trying to setup a ubuntu server, so all access is remote.  I've followed the VNC how-to, and have gotten everything to work except for what I need:  Ability to login to desktop environment without an actual login at the terminal -- "VNC Server with Login Screen via GDM".

The VNC how-to was here: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

I am indeed able to:
-ssh/telnet in
-export displays, and create xterms etc.
-Create additional remote logins, *IF* there is a a local login already to the machine
-I can remotely access via "Remote Desktop" and vnc where is already a local login (ie desktop sharing) also

I think I am close though:  When there is NO local login and I try to vnc into the machine, I receive a different error message:

Real VNC:  "reading version failed:  not an RFB Server?"
TightVNC:  "Invalid Protocol"

I am trying to access my 192.168.0.x:1.

There doesn't appear to be any additional useful log files of any sort for me to test / debug this issue.  Can anyone lend a hand?

TIA!

---

