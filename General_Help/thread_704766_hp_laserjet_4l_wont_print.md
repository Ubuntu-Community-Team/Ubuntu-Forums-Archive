---
title: "hp laserjet 4l wont print"
date: 2008-02-22
forum: General Help
---

### Post by docusn on 2008-02-22
I am a total newbie to Ubuntu - so apologies in advance.

I have just installed Gutsy Gibbon as a dual boot option on an XP Pro SP2 machine. 

I am running a home workgroup called HOMELAN. I installed the printer using  System>Administration>Printing. Searched for networked printers. It found the LJ 4l right away (HOMELAN>Server>Laser4L), and I installed the recommended driver (HP LaserJet 4L Foomatic/ljet4). The I tried to print a test page.

Nothing happens. The dialog box remains Printer State: Idle. So I cancel the print job (I am up to job 9 now - somehow I don't think the print queue is really empty, but I don't know how to empty it.

So, any ideas why the printer refuses to print?

---

### Post by docusn on 2008-02-22
I finally got it to work. I had to add the username to the smb address. I.E,smb://mark@HOMELAN/SERVER/Laser4L, vice smb:HOMELAN/SERVER/Laser4L.

---

