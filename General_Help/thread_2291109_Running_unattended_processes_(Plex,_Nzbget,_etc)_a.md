---
title: "Running unattended processes (Plex, Nzbget, etc) as Kerberos users for CIFS shares?"
date: 2015-08-17
forum: General Help
---

### Post by sofakng on 2015-08-17
I currently have an Ubuntu server that runs a bunch of unattended daemons (plex, nzbget, sonar, airvideo, etc) and I recently install an Active Directory server on my network.

Each of the applications listed above reads and writes files to a SMB/CIFS and/or NFS server located on a Solaris 11.2 box.

I'd like each application on my Ubuntu box to use it's specific Kerberos credentials when it changes any files on my file server.  Is this possible?

For example, when I look at a file in Windows Explorer (on my Windows 10 machine), I'd like to see that my Plex user created/modified a file, etc.

If I used Windows to run the processes, I think I'd just need to configure each Service to run as a Domain User and everything would work as expected, but this seems very, very difficult to configure under Linux?

---

