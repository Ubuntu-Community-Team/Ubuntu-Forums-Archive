---
title: "Linux &amp; Active Directory Users and Computers"
date: 2006-10-16
forum: General Help
---

### Post by Powercat on 2006-10-16
Hello.
I am trying to switch my work computer from Windows XP to Linux.
We are using a pure Windows environment, so that means Exchange + AD.
I've got the Exchange part settled, with Evolution, and I found a tutorial to join AD.
However, I often need to browse Users and Computers to reset passwords and such.
Is there a way to either get AD to show up on linux, or at least reset passwords?

Thank you!!

---

### Post by Powercat on 2006-10-16
Is there truly no way of reseting user's passwords in AD?

---

### Post by Iowan on 2006-10-16
I suspect there's a way, but I don't have a good answer for you...
You might give folks more than an hour to respond. :)

---

### Post by timlev on 2007-11-07
shameless bump ... Has anyone been successful in doing this?

---

### Post by Mithrilhall on 2007-11-07
Setup a Virtual Machine (VMWare or some other virtualization software) and install Windows 2000, XP, 2003, etc...

That's what I would do, or keep 1 Windows box around and rdp into it to do your AD work.

---

### Post by Fire_Chief on 2007-11-07
The Active Directory Users & Computers utility is an add-in that uses the Microsoft Management Console to run. This (MMC) is not really a stand-alone component that you can install (last I checked anyway).

---

### Post by afiorillo on 2007-11-07
if you a citrix server you can publish the mmc snap in tool for users & computers..you can doo all the snaps..then install the citrix client for linux and point it to that server and you will be able to start the app

---

