---
title: "Hardy Vmware Issue"
date: 2008-05-18
forum: General Help
---

### Post by jamillikan on 2008-05-18
I'm at my wit's end with sharing /home/username/mydata with VMWare workstation.  I have VMware installed correctly and working.  The problem is this:

I want to share the mydata folder and mount it as a samba share for the VMware workstation.  Here's what I've done.

sudo smbpasswd -a username
subo smbpasswd -e username

When I start the VMware workstation, and attempt to map the network drive, it asks for a password.  I enter the password I supplied with the smbpasswd command above and it tells me it's not the valid password (but it actually *is*.)

The same thing happens when I try to connect to the Hardy printer I wish to use from within VMware.

If anyone knows of a solution, it's crucial I remedy this situation as soon as possible.  Any help is greatly appreciated. 

FWIW, I'm running VMWare Workstation 6.0.3 patched with the any-any-update.  The Windows version in VMware is Win98SE.  This worked without issue with Feisty and Gutsy but not here with Hardy.  Any ideas what I'm doing incorrectly?

Any thoughts?

Thank you,

Joe

---

