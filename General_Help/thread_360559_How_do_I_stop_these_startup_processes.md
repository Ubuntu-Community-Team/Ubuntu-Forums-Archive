---
title: "How do I stop these startup processes?"
date: 2007-02-13
forum: General Help
---

### Post by jTHEn on 2007-02-13
The following processes are useless to me, but they keep starting up automatically, eating up memory space. (I use Xfce)

evolution-alarm-notify
evolution-data-server-1.8
update-notifier
gnome-power-manager
evolution-exchange-storage
bonobo-activation-server
gnome-volume-manager

How do I keep these programs from starting? I kill them and save my sessions upon reboot, but they keep coming back.

---

### Post by Gibbs on 2007-02-13
A lot of them are core processes to the Ubuntu (GNOME) desktop. Disabling/uninstalling them might make things not run... they are used for a variety of things (I believe).

---

### Post by jTHEn on 2007-02-13
I don't use Gnome. Killing them doesn't cause anything to break. Could someone explain what they do exactly? It just seems to me they're leftovers from when I was using Gnome that aren't relevant anymore.

---

### Post by recrispi on 2007-02-13
Hi!
evolution is an e-mail client (something like thunderbird or outlook) and have a calendar that allows you to program some reminders at specific times (so the evolution-alarm-notify)
gnome-volume-manager is a program to automount your cds and usb flash drives when you insert them on your PC.
The other programs I don't know.
In the computer at my office I'm running openbox without Gnome or KDE (did a server install and then installed openbox and some programs I needed). I think it could be safe for you to uninstall evolution completely. For the other programs I don't know if it would be safe to uninstall them.

Hope that helps.

---

### Post by krishnarp on 2007-11-19
Is there any way to turn off these programs??

---

### Post by rsambuca on 2007-11-20
I think you may have to delete them from the Startup Programs and the Current Session, and then save in the Session Options.

I personally wouldn't turn off the bonobo or the volume manager.  All told, I don't think they take even 10MB of ram anyways.

---

