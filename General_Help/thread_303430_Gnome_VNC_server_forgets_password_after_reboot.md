---
title: "Gnome VNC server forgets password after reboot"
date: 2006-11-20
forum: General Help
---

### Post by allebone on 2006-11-20
Hi there

I have just installed Ubuntu 6.10 x86 on a laptop at home.

After installation I set-up via login screen prefs for Gnome to auto login using the only user (peter).

I then set-up under remote desktop prefs users to be able to access the desktop via VNC with a password and no confirmation.

I then tested this from a windows machine using UltraVNC. This worked correctly and I could control the screen after typing in the password.

However if I restart the Ubuntu box, after it auto logs in i cannot access the box via VNC. The error states incorrect password. Resetting the password resolves this issue.

The password contains alphanumeric characters and an asterisk only.
I have tried different passwords. This did not help.

No updates or additional software was installed.
I have subsequently installed openssh-server. This allows me access to the command line after a reboot (using putty). However I cannot figure out how to reset the password via the command line for the VNC server, and don't know why rebooting loses the password every time.
I have tried typing "vncpasswd" at the terminal. This does not appear to reset the password so am unsure what this command is doing, however it is possible that i need to restart the VNC server after doing this but don't know how.

Any suggestions on how to reset the password via ssh, or make the password persistent would solve my problem.

Kind regards
Peter

---

### Post by gsaggior on 2006-11-20
I'm experiencing the same problem... I was only able to restore a "usable" password for the Remote Desktop operations using the Gnome interface:

System --> Preferences --> Remote desktop

\Gps
](*,)

---

### Post by TuRfYMaN on 2006-11-21
I am also experiencing this same problem!  I am glad it's not just me...  I think I'm going to just install the VNC Server anyways...

---

### Post by rockrhino27 on 2006-11-29
I also have the same problem.  You don't even have to reboot the entire system.  If you restart gnome / X Server you will lose the password also.  I'm surprised nobody knows how to fix this.  Any help would be extremely appreciated.  

Rock

---

### Post by StrikerNL on 2006-12-05
I have the same problem, is there any fix for this yet?

---

### Post by daveyiv on 2006-12-05
Same problem here as well, really annoying.

---

### Post by Qw3rT on 2006-12-06
This thread explain how to fix the issue:

[https://launchpad.net/distros/ubuntu/edgy/+source/vino/+bug/65795]("https://launchpad.net/distros/ubuntu/edgy/+source/vino/+bug/65795")

---

