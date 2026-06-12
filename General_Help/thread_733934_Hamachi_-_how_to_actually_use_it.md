---
title: "Hamachi - how to actually use it"
date: 2008-03-24
forum: General Help
---

### Post by zoopzoop on 2008-03-24
I installed Hamachi on Gutsy and everything worked fine.
I created a network and now I want to share some folders to other users in my network.
I want to use the command line version and no GUI like ghamachi.
Now I have some questions about how to actually use it that I could not find anwers to.

- How do I see my own Hamachi IP?
- When I want to share a folder, I have the options of sharing it using "Windows networks (SMB)" or "Unix networks (NFS)". I want to be able to access a shared folder from a Windows XP version of Hamachi as well as other Ubuntu versions. Which option do I choose?
- How do I browse shared folders of other peers in my network from Ubuntu?

---

### Post by zoopzoop on 2008-03-25
*bump*

Anyone? Pretty please?

---

### Post by rogblake on 2008-03-25
If there is no other way to see your Hamachi IP address, you can issue the "ifconfig" command and look for the IP address associated with the "ham0" interface.

To share directories to Windows systems it is simplest to use Samba (SMB) networking. NFS (the Nightmare File System) is a Unix thing, though there is NFS client software available for Windows.

---

### Post by zoopzoop on 2008-03-30
Can anybody help me with how to browse a remote folder?
What's the most common way to do it in Ubuntu?

---

