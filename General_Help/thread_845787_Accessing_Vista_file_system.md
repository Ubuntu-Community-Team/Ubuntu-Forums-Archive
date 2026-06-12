---
title: "Accessing Vista file system"
date: 2008-06-30
forum: General Help
---

### Post by -Outcast- on 2008-06-30
I have a dual boot with hardy and vista ultimate. Vista and hardy on separate partitions.

I cannot get access to Vista's file system in order to access files. Ubuntu asks me for a user name and then password. I use the Windows one. Then denied. 

I have created a shared folder on vista too. 

Is there another way to access Vista's file system or am I doing something wrong here?  

I would prefer a shared FAT partition but don't have enough space.

---

### Post by darco on 2008-06-30
You need to tweak your Samba config file. I have the same setup and am able to access Vista w/o a prob. 
Been awhile since I had to tweak it but I think it was this;

/etc/Samba/smb.conf


###### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

Search the forum for more help
good luck
darco

---

### Post by -Outcast- on 2008-07-01
Thanks for that. I think it did something but now I am getting a cannot mount error when I try to access the file system. Quite strange. When ubuntu 8 installed it did not see Vista well enough I don't think either, as it said there were no user files to be imported, when there were. 

Still it sees the filesystem

---

