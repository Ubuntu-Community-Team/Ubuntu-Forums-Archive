---
title: "Unable to access windows printer"
date: 2012-11-25
forum: General Help
---

### Post by asb3 on 2012-11-25
In my home network I have a printer attached to a windows machine.  I'd like to be able to print to it from my UBUNTU machine.  On
System->Printers->Add
I selected "Windows printer via samba"
In the smb printer field, I enter the machine name and printer name and push "Browse".
In the smb browser, the machine appears in the "Share" list, but the printer does not, so I can't connect.

Any ideas?

---

### Post by daslinkard on 2012-11-25
> **asb3 said:**
> In my home network I have a printer attached to a windows machine.  I'd like to be able to print to it from my UBUNTU machine.  On
System->Printers->Add
I selected "Windows printer via samba"
In the smb printer field, I enter the machine name and printer name and push "Browse".
In the smb browser, the machine appears in the "Share" list, but the printer does not, so I can't connect.

Any ideas?
What are the specs on the printer?

---

### Post by asb3 on 2012-11-25
Its an HP Photosmart C4200

---

### Post by daslinkard on 2012-11-26
When you say that the printer is attached to your home network....do you know what the IP address is for your printer? Or is the printer only connected through the network through your windows PC?

---

### Post by Jerry N on 2012-11-26
You didn't mention it so I have to ask.  Did you tell the Windows machine to share the printer?

Jerry

---

### Post by asb3 on 2012-11-29
The printer is only connected through the PC, and I did tell the windows machine to share the printer.

---

### Post by daslinkard on 2012-11-29
This link [here]("http://www.7tutorials.com/how-access-windows-shared-printer-ubuntu") has some information in sharing a printer with Ubuntu and Windows 7....check it out and hopefully it helps you make some progress....if not let us know.

---

### Post by asb3 on 2012-11-30
I looked at the links, and I still can't connect.  For debugging, from a terminal I typed

asb@cavu:/mnt/hd1$ smbclient -L 192.168.1.2 -N
WARNING: The "null passwords" option is deprecated
WARNING: The "password level" option is deprecated
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Anonymous login successful
Domain=[BARNETT] OS=[Windows 7 Home Premium 7601 Service Pack 1] Server=[Windows 7 Home Premium 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.2 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

Now what?

---

### Post by SteveinSC on 2013-02-24
I have the same problem.  A month ago I accessed the printer on my Windows Vista machine, no problem ever from my Ubuntu/LXDE.  Sometime, over night the thing stopped working.  It is a change in Samba problem because the HP 2015 printer is now reporting to the LXDE Printer Properties tha (NT_STATUS_ACCESS_DENIED)  The windows vista is and has been shared.  I have samba set with security = share.  The LXDE printers gui shows the networked HP p2015 but it can't connect to it.  This is making ubuntu a real pain.  Any help would be appreciated.

---

