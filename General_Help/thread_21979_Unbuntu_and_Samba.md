---
title: "Unbuntu and Samba"
date: 2005-03-25
forum: General Help
---

### Post by Amdmhz on 2005-03-25
Hi all. I am using warty and the newest samba. I have been editing the smb.conf file like I always have with other distros. My problem is when I try to put in a different netbios name, I am getting connection failed. Here  is an example:

netbios name = AMD

When I do a: smbclient -L //AMD it tells me connection failed but if I put:

netbios name = UBUNTU 

Then smbclient -L //UBUNTU it connects fine.

Is this a bug in warty? Has anyone esle seen this problem?  ](*,)  I can't seem to fix it.  Thanks for your help

Amdmhz

---

### Post by Happy on 2005-03-25
probably stating the obvious here but did you restart the smb server after changing smb.conf?

sudo /etc/init.d/samba restart

---

### Post by ubuntu_demon on 2005-03-25
In my experiences samba and smbclient work better in hoary

---

