---
title: "Bletooth not visible"
date: 2006-12-12
forum: General Help
---

### Post by iitywygms on 2006-12-12
Hey all.  I have bluetooth installed and I can send files to my phone.  My phone can seem my computer when I send files to it.  Problem is, I can't see my computer from the phone.  If I want to send a file to the computer, the phone cant see it. (no device found) Any idea how I can fix this?
I am using edgy with all the latest updates.
Thanks

---

### Post by iitywygms on 2006-12-13
No other devices can see my computer either.

---

### Post by iitywygms on 2006-12-14
Anyone?  Is there any more information needed?

---

### Post by Zalbor on 2006-12-14
I have the opposite problem: The phone can see my computer, but the computer can't see the phone (except very rarely, and the phone has to be trying to send something for it to happen).
By searching on the boards, I found that it seems to be a general bug in edgy, that apparently no one has fixed (yet, I hope).

---

### Post by defishguy on 2006-12-14
Try this.

> sudo hcid

Then try a default scan from the pc / phone by typing
> hcitool scan

Whenever I need to send files to my Palm TX it only works when I start the service manually as opposed to starting it at boot.

---

### Post by iitywygms on 2006-12-16
> **defishguy said:**
> Try this.



Then try a default scan from the pc / phone by typing


Whenever I need to send files to my Palm TX it only works when I start the service manually as opposed to starting it at boot.

That is a way to discover a device from your computer.  Is there a way to force the computer to broadcast that it has bluetooth?  To become visible?

---

### Post by iitywygms on 2006-12-20
Okay it sort of works now.  One more problem to solve. (new thread)](*,) ](*,) 
The phone and computer can see each other.  I can send files from computer to phone, just not the other way.  The phone ask for a service list.  Whatever that is.  Anyway.  To make it work I have to do this.

 sudo /etc/init.d/bluetooth restart
 dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable

then it seems to work. sort of

Hope this can help someone else.

---

### Post by legzelda on 2007-05-04
After struggling with the same problem in Feisty, your advice successfully allowed me to connect my T-Mobile MDA to my Dell E1505 with built-in Bluetooth.  Thank heaven you found a fix!  I never had this problem in Edgy, and I don't think I had the problem when I first installed Feisty.  Regardless, thank you for your perseverance, as well as sharing how you fixed your problem, as you helped more than just yourself!

> **iitywygms said:**
> Okay it sort of works now.  One more problem to solve. (new thread)](*,) ](*,) 
The phone and computer can see each other.  I can send files from computer to phone, just not the other way.  The phone ask for a service list.  Whatever that is.  Anyway.  To make it work I have to do this.

 sudo /etc/init.d/bluetooth restart
 dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable

then it seems to work. sort of

Hope this can help someone else.

---

