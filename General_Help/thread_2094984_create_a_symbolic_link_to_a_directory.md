---
title: "create a symbolic link to a directory"
date: 2012-12-15
forum: General Help
---

### Post by mbohets on 2012-12-15
hi,

I am trying to create a symbolic link to a directory but it does not seem to work as expected

marc@marc-Aspire-7730G:~$ ln -s /nas/marc/marcdocs testnaslink
marc@marc-Aspire-7730G:~$ cd testnaslink
bash: cd: testnaslink: No such file or directory

When I check the link with the ls command, it seems ok
ls -al te*
lrwxrwxrwx 1 marc marc 18 Dec 15 16:27 testnaslink -> /nas/marc/marcdocs

and when I change directory directly to the destination with cd /nas/marc/marcsdocs
I am in the correct directory
/nas/marc/marcsdocs# ls
lost+found
mailsignature.txt
muziek

So what am I doing wrong here ?

Some extra info:
the directory /nas is a mount of a remote file system via  the following line in fstab[FONT=Arial, sans-serif][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Arial, sans-serif][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][FONT=Arial, sans-serif]
//192.168.0.101/homes /nas cifs credentials=/etc/cifsmarc,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0[/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]

---

### Post by dino99 on 2012-12-15
[http://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link](http://askubuntu.com/questions/56339/how-to-create-a-soft-or-symbolic-link)

---

### Post by vanadium on 2012-12-15
It may depend on the configuration of your cifs server whether a symbolic link can access it ([http://hd.kvsconsulting.us/netappdoc/733docs/html/ontap/filesag/GUID-23A30F6E-F81A-4C4B-A8C1-5E5027C1396A.html](http://hd.kvsconsulting.us/netappdoc/733docs/html/ontap/filesag/GUID-23A30F6E-F81A-4C4B-A8C1-5E5027C1396A.html))

Since you are configuring your /etc/fstab anyway, usng a "mount bind" to access the cifs also from within your home directory would probably work. That would require an additional entry. (I use mount bind to redirect tmp storage to my home partition: "/home/tmp/var/tmp /var/tmp none bind")

---

### Post by mbohets on 2012-12-15
Thx,

ln -s /nas/marc/marcsdocs /home/marc/marcsdocs

did the trick.
I guess I only read about symbolic links to files and immediately started
typing the command without reading any further

---

