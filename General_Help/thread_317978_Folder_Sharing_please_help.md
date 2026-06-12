---
title: "Folder Sharing please help"
date: 2006-12-13
forum: General Help
---

### Post by Naegling23 on 2006-12-13
Ok, so I have been trying to share folders on my network for about 3 months.  I have read through hundreds of guides, forum postings, etc.  I have tried, samba, nfs, and another way whose name I cant remember.  Nothing works!  I am trying to share some files in my /home directory (music, videos, etc).  I am running two computers, both edge, one kubuntu (my main one), one ubuntu (my wife's computer).  In kubuntu I click on the file, share, I have tried nfs, and samba.  On my wife's computer, I go to browse the network, it shows up under windows network (mine is called 202amboy), but clicking on it brings up an error message, network, or folder not found.  If I try to share a folder on my wifes ubuntu box, I see absolutely nothing on my kubuntu box.  I have been spending way too much time on this.  Can anyone simply walk me through the steps needed to share folders over a network?  Step by step, starting at the beggining, assuming that I know nothing.  Please dont point me to a faq, or wiki, I have already read the one your going to suggest.  Please help, why is this so difficult to do?

---

### Post by useResa on 2006-12-13
Sorry if I ask for the obvious, but I just want to make sure.
  Do you have the *Folder sharing service (samba)* running?

---

### Post by Naegling23 on 2006-12-13
always ask the obvious, most computer problems result from people not having them plugged in.

I have samba installed on both computers.  That would mean that it is running at startup correct?  Or do I need to set it up to start?

---

### Post by useResa on 2006-12-13
> **Naegling23 said:**
> always ask the obvious, most computer problems result from people not having them plugged in.

I have samba installed on both computers.  That would mean that it is running at startup correct?  Or do I need to set it up to start?

I only recently noticed - because I had some file sharing problems too - that on my PC it was not running. However, this does not mean it wasn't running when I first installed it (sometimes I mess up things by my own doing ;)).

I can indicate how you can check it for your Ubuntu installation. 
Go to *System --> Administration --> Services*
Check if your *Folder sharing service (samba)* is checked.
If not, check it and restart.

Additionally you can check it (however I am not completely sure about this, but maybe someone else can confirm this) by typing ```
ps -ef | grep smbd
```

---

### Post by Iowan on 2006-12-13
> **Naegling23 said:**
> I have samba installed on both computers. 
The server?
You have added the usernames to passwd and smbpasswd?
I've had better luck using Places>Connect to Server (Gnome).

---

### Post by bodhi.zazen on 2006-12-13
[NFS the easy way](http://ubuntuforums.org/showthread.php?t=249889)

I followed this guide and was up and running in < 5 minutes :)

Big thanks to **malco2001** :)

---

