---
title: "torrents lock up computer"
date: 2008-04-29
forum: General Help
---

### Post by Redls1bird on 2008-04-29
Hey guys.  I am using xubuntu 7.10 .  Any time i try to download a torrent, it locks the computer up, and i have to manually reboot it.  I have tried with deluge, bittorrent and bot tornado with the same results.  It never errors out, just freezes up.  I read something about a blacklist file?  but i dont know what that is.  Any one have any help?

---

### Post by Rainstride on 2008-04-29
what are you system specs?

---

### Post by Redls1bird on 2008-04-29
ancient dell laptop.  does ubuntu have a spot like windows where i can pull the hardware info?  

I forgot to mention that torrents worked for about a week leading up to this,  with no major system changes made prior to the problem.

---

### Post by Rainstride on 2008-04-29
the only one i can think of is device manager, you can find it in add/remove

---

### Post by Jammin80503 on 2008-04-29
Its possible that your laptop is having trouble running Xubuntu. if that is the case, I would recommend Fluxbuntu. I installed it on my friend's ancient laptop and it works like a dream. 

Also, I would try Azureus first. Its a great program, give it a shot.

---

### Post by twright on 2008-04-29
i had this problem with deluge in gutsy but hardy seems to have fixed it for me

---

### Post by Redls1bird on 2008-04-29
> **twright said:**
> i had this problem with deluge in gutsy but hardy seems to have fixed it for me

unfortunatley,  i cant get my wireless internet working with hardy.  

THe laptop has no problem running xubuntu, its rather quick.  It doesnt freeze up or slowly open items.  It just comes to a screeching hault during opening any torrent program.

---

### Post by Jammin80503 on 2008-04-29
You could try something like Frostwire that does torrents, but is meant for other stuff.
If its the torrents themselves that are freezing the computer rather than the program, its possible that your ISP is blocking torrents.

---

### Post by Redls1bird on 2008-04-29
I just recently switched to xubuntu on my personal laptop at work, prior to that i was running win xp home.  Ive been downloading torrents here for over a year now.  I dont think that that is,  but to be certain ill try it on another computer later.  

Also,  some other people here have p2p sharing networks on their pcs,  would they still work correctly if the isp has shut off torrents?  I know that they arent the same, but you never know.

---

### Post by Redls1bird on 2008-04-29
this is what i get if i try sudo deluge :

Traceback (most recent call last):
  File "/usr/bin/deluge", line 132, in <module>
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 218, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 107, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 121, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I dont speak linux lol,  so i dont know if its saying my machine isnt working,  or my connection.  Obviously im connected to the net though, its how im posting now.

---

### Post by Redls1bird on 2008-04-29
Does anyone know what that error means?

---

### Post by Jammin80503 on 2008-04-29
I don't know what most of it means, but a few words in there make me think it is your ISP. try canceling your torrents and opening the program, see if that still freezes it.

---

