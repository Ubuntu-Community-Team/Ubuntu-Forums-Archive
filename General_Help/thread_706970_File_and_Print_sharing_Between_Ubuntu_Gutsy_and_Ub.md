---
title: "File and Print sharing Between Ubuntu Gutsy and Ubuntu Gutsy / Windows XP"
date: 2008-02-24
forum: General Help
---

### Post by morning_napalm on 2008-02-24
I am trying to get the following configuration working on my home network.  I posted this in the Networking forum and have not had any responses yet.

System 1: Dual boot Ubuntu Gutsy /Windows XP (Primarily Ubuntu Gutsy)
2 printers connected to this computer
This is our main computer

System 2: Dual Boot Windows XP / Edubuntu Gutsy (run each system about equally)
This is our kids computer

Both systems are connected to the network router.

What is the best way to set this up so that I can share files between the two systems (Ubuntu Gutsy on 1 and either XP or Gutsy on system 2) and be able to print from either XP or Gutsy on system 2 to the printer attached to system 1 (running Gutsy)?

I have tried to get this working with SAMBA, but so far haven't managed to get anything working. I have been using Linux since last July and am trying to switch over completely, but am still learning how things work. Getting this networking thing sorted out will help a lot.

Also: Would I be better off using one way to communicate between the two Gutsy systems adn a separate way when I run XP on the second machine. It seems like some of the other potential solutions (NFS, CUPS, ??) way run faster. Any thought would be appreciated.

---

### Post by GuDoN on 2008-02-25
For File sharing from Linux to Windows (In your case Windows XP), you need to download and configure SAMBA.

You can # sudo apt-get install samba smbfs

---

### Post by Phosphoric on 2008-02-25
As far as I know, you don't need samba just for printer sharing.

Have a look at this link:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

I've used this how to successfully for a similar requirement.

---

