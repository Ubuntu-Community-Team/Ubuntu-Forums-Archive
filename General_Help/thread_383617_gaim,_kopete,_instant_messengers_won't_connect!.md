---
title: "gaim, kopete, instant messengers won't connect!"
date: 2007-03-13
forum: General Help
---

### Post by euthyfro on 2007-03-13
So, yesterday gaim 2.0.0beta6 up & stopped being able to connect.  It started with my whole internet connection going down, after a long talk with the verizon Fios guy yesterday & again today my connection is back up & working but...
running gaim from the terminal gives me: 
 
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files

now i don't know where "org.freedesktop.NetworkManager" came from but all i've ever done with gaim is open it up & message friends.  never had any problems before.

then i got kopete to see if it was a problem with gaim.  thought i had everything i needed to run kopete but when i tried that i got:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

yup, same thing 4 times over, probably didn't have it configured correctly or something.  That's not the problem though, i don't want to use kopete anyway, i want gaim to work like it was 26 hours ago.

---

### Post by arthur_kalm on 2007-03-15
I'm having the same problem. I haven't been able to connect using either GAIM or Kopete on my laptop (Ubuntu 6.06) and desktop (Ubuntu 6.10). None of the services I use (MSN, Gtalk and Xfire) can connect anymore. I can use Gmail's built in talk and I can also use MSN live messanger as well as Windows Messenger on Windows. What's going on?! Help, please!

---

### Post by arthur_kalm on 2007-03-15
Anybody? This is a really big and annoying problem for me... I need to be online...

---

### Post by itazuki on 2007-03-16
I too am experiencing this issue. It may be permissions related since I was just messing around with the permissions on /home and my home folder. I get:

greg@Outsider:~$ kopete
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
greg@Outsider:~$

Anyone have any ideas?

---

### Post by itazuki on 2007-03-16
So yeah, ever since I messed with the permissions on my home folders things have been breaking/broken. When I first altered my permissions I was unable to do anything, such as ls my home folder or open my home folder in konqueror. Idon't have set UID or GUID or sticky on my /home/greg folder. My ipod doesn't automount and my kde doesn't bring up the "What do you want to do?" dialog when a new device, like my ipod, is plugged in.  Amarok does not detect the ipod because it's not mounted.

On /home/greg the permissiosn are

Owner 7

Group 7

Other 5

Too permisve if anything. Any ideas?

---

### Post by Psychobudgie on 2007-03-16
Can't connect to the msn network with any non ms client at the moment from any pc. Would suggest that MS have made a protocol change. oh joy.

---

### Post by clintonthegeek on 2007-03-16
Psychobudgie... although it sounds unrelated to the original problem stated in this thread, I'm having the same issue... Kopete opens, will connect to Aim, Yahoo!, and Gmail, but not to my MSN accounts, as of today. Worked yesterday until I went to bed around 2:00am EST, but not this morning.

---

### Post by zorkerz on 2007-03-16
Having the same problem here.  I was going to suggest using [meebo.com]("http://www.ubuntuforums.org/meebo.com") for a temp fix but they have the same problem also.  Seems as though microsoft is being an *** as usual. I feel like we are going to just have to wait this one out.  Although for those of you who have not checked out meebo or an equivalent multi-protical instant messaging browser application i recommend you do.  They are great for a friends house or lab computers where you cannot install an application but need to connect to all of you various instant messaging programs.

---

### Post by arthur_kalm on 2007-03-16
I found out what my problem was.. seems somebody in my house was blocking these ports. Thanks anyways.

---

