---
title: "Samba Shared and CHMOD"
date: 2006-11-11
forum: General Help
---

### Post by gleem on 2006-11-11
Through my samba server, I am able to connect to my linux samba server with no problems from windows and mac. In order to be able to add files and remove files to my samba shared, I have chmod -R 777 /sharedfolder

now.. my problem is now. everything works great except if I go on the linux server, any files that I modify and or add I do not have access to. How can I make it so that my linux admin user account is not locked out?

---

### Post by gleem on 2006-11-11
I found the chown command which worked.. however.. how can I make it so I do not have to do this everytime i upload a file from my windows or mac machine to my linux machine?

---

### Post by david3d on 2006-11-11
There are a few ways to do this with samba.  Hard to say which method would best lend itself to your particular situation.

What you'll want to do is edit your /etc/samba/smb.conf and add the following to your [sharedfolder] section.

  create mask = 0664
  directory mask = 0775

Depending on your situation you may need to tweak those bits a little.  Also depending on your situation you can set the group sticky bit on your sharedfolder by running "sudo chmod g+s sharedfolder".  You may also find it helpful to add the following option to your share in the smb.conf.

  inherit owner = yes

--
David Miller

---

