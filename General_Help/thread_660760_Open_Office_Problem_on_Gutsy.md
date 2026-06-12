---
title: "Open Office Problem on Gutsy"
date: 2008-01-07
forum: General Help
---

### Post by ragadanga63 on 2008-01-07
Help!! Everytime I open an Open Office file shared in another Ubuntu pc in my network, i would get this error :  "General Internet Error has occurred" and the file would not open.  I can copy files to and from other Ubuntu pc's in the network.  Printing using network printers are also working flawlessly.  I can also open non-Open Office files located in other pc's in the network.  Can anyone help me out?  

Thanks.

---

### Post by zipperback on 2008-01-07
> **ragadanga63 said:**
> Help!! Everytime I open an Open Office file shared in another Ubuntu pc in my network, i would get this error :  "General Internet Error has occurred" and the file would not open.  I can copy files to and from other Ubuntu pc's in the network.  Printing using network printers are also working flawlessly.  I can also open non-Open Office files located in other pc's in the network.  Can anyone help me out?  

Thanks.

Are you opening it across the network with the file still residing on the remote computer? Or are you copying it to your local system and then opening it? Also, is the file also opened on the remote pc? And does the file being opened on the remote computer produce any sort of errors if it is opened on that local host?

- zipperback
:popcorn:

---

### Post by ragadanga63 on 2008-01-08
I am opening it across the network with the file still saved/residing in another Ubuntu PC or Windows PC (same thing happens in both cases).  The file can be opened locally and when copied to the local system.  The file was not open at the PC where it was residing.

---

### Post by zipperback on 2008-01-09
> **ragadanga63 said:**
> I am opening it across the network with the file still saved/residing in another Ubuntu PC or Windows PC (same thing happens in both cases).  The file can be opened locally and when copied to the local system.  The file was not open at the PC where it was residing.

Hmmm that might be a bug. I don't know for sure as I don't have a windows machine here any longer to test it with.

For now, I would just copy the file to your local system, edit it, and then copy it back. 

Sorry I couldn't be much more help with that one.

- zipperback
:popcorn:

---

### Post by zveroboy on 2008-01-09
There are actually two tickets open about this issue:
Bug #94326
Bug #114289

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/94326](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/94326)
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/114289](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/114289)

So, it seems to be a widespread issue.  
I am going to try it with Xubuntu/Ubuntu/PcLinux and see what happens.

---

### Post by ragadanga63 on 2008-01-10
Thanks for your replies.  Solved the problem in File-in-Windows-box>opened-in-Ubuntu-box.  One of my staff had unticked the "Allow network to change files" box on XP.

However, the problem remains with Ubuntu to Ubuntu OO documents.

---

