---
title: "Sharing printers between Ubuntu machines on LAN"
date: 2006-10-31
forum: General Help
---

### Post by srunni on 2006-10-31
Hi,

I was wondering if anyone knew how to set up my Ubuntu desktop computer so that my Kubuntu desktop computer could access/use it. Is there a tutorial on this?

Thanks in advance for the help!!

---

### Post by David Corrales on 2006-10-31
Access it how? like using the desktop? or accessing shared files?
To easily share the desktop, go to System/Preferences/Remote Desktop.
For sharing files, go to System/Administration/Shared Folders.

---

### Post by srunni on 2006-11-01
As I said in the title - so I could share printers.

Thanks

---

### Post by sefs on 2006-11-01
I got it done by installing samba.
the printer in question was on a windows machine though.
Then in the printing menu item of the ubuntu machine i just added a new printer and via samba was able to browse and select the printer on the windows machine.  luckily the printer drivers were even present in ubuntu already also.

a link for a howto: install samba.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+samba)

---

### Post by David Corrales on 2006-11-02
My bad, probably too late at night :(
But yeah, you'll need to install samba in order to browse shared printers.
If you don't have a problem with it, you can set the authentication mode to *share* since it simplifies things. That is, you won't have to create samba accounts in any of both computers.

---

