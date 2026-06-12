---
title: "Accessing smb mount from the command line"
date: 2007-10-19
forum: General Help
---

### Post by grahams on 2007-10-19
I can successfully mount the smb using >places>connect to server via the gui and access all the files correctly. However I can not get it to mount via the command line. I've followed what seem to work for others but I get the following error

sudo mount -t smbfs -o username=graham,password=secret,uid=graham,gid=graham  //mtifs01/graham ./smb
13043: session setup failed: ERRSRV - ERRbadpw (Bad password - name/password pair in a Tree Connect or Session Setup are invalid.)

thanks in advance

---

### Post by mahousaru on 2007-10-19
Should the file type be cifs?

I've just mounted a share in gutsy using

mount -t cifs //server01/multimedia /home/username/network/multimedia -o username=username,uid=username,gid=groupname,file_mode=0640,dir_mode=0750,iocharset=utf8

---

### Post by grahams on 2007-10-19
thanks that works :)

---

