---
title: "Win2k3 share ls permission denied"
date: 2007-03-30
forum: General Help
---

### Post by 00coday on 2007-03-30
I am having a problem with permissions on a windoze 2003 share on a server recently added to active directory. Before the move to AD, I was able to mount shares on the windoze box with no problem. Now the mount statement executes fine, but when I do an ls of the mount I get a permission denied error and the permissions for the mounts look like:

?--------- ? ? ? ? ? /mnt/dvicweb/http
?--------- ? ? ? ? ? /mnt/dvicweb/weblogs

The mount statement is as follows:

mount //155.7.145.84/weblogs /mnt/dvicweb/weblogs -o username="<domain>\<user>",password='<password>',dmask=777,fmask=777

The weblogs share has everybody/full control permissions, so anybody should have access to it. The user I am using for the mount is a domain admin, so there shouldn't be any problems with permissions there.

I also followed the HowTo at [http://doc.gwos.org/index.php/Active...thentification](http://doc.gwos.org/index.php/Active...thentification) for using AD authentication and joining the Ubuntu box to the AD domain.

Any thoughts...

---

### Post by rnwld999 on 2007-03-30
I had the same problem before, here is my /etc/fstab configuration to connect to a server in AD.

//ServerName/shareddrive /mnt/sdrive     cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777   0       0

---

### Post by 00coday on 2007-03-30
Thanks for the help.  I gave that a shot with the appropriate server changes and received an error saying the line was bad.  I am also trying to script the mount/unmount of the shares so they are non-persistent.  

I found another post that shows a command line cifs mount that works.  The code is below if anyone is interested:
mount -t cifs //server/share /mnt/share -o username="<domain>\<user>",password="<password>",domain=<domain>,file_mode=0777,dir_mode=0777

Thanks again for the help!

---

