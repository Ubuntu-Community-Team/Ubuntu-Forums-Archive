---
title: "Swat &amp; Samba will not load"
date: 2006-11-22
forum: General Help
---

### Post by Corolla92 on 2006-11-22
Hey guys,
I decided to reformat my XP files server to Ubuntu (6.10).
I have pretty much everything setup, except SWAT and Samba.

Samba appears to be working, but on my main machine (Mac Mini - OS X 10.4.8) and my secondary machine (Powermac G3 - OS X 10.4.8), they see the machine in Finder, but when I try to mount the share, OS X tells me the place the alias points to is missing.

Now, that's not all.

Despite following almost every guide possible for installing SWAT and Samba to play nice, SWAT will not run.
When I run **netstat**, SWAT does not show up in the list at all.

I have all the necessary packages (well, what I'm aware are the necessary ones), which includes *samba, samba-common, smbfs, smbclient, swat, xinetd*.

I'm absoloutly puzzled as to why it doesnt work. ](*,) 

Any help is greatly appreciated.

---

### Post by pixelpusher on 2006-11-23
1) apt-get install xinetd (I know you got this already)
2) vi /etc/xinetd.d/swat

# description: SAMBA SWAT
service swat
{
  disable  = no
  socket_type  = stream
  protocol  = tcp
  #should use a more limited user here
  user  = root 
  wait  = no
  server  = /usr/sbin/swat
}

:wq

3) #dpkg-reconfigure xinetd 
4) [http://localhost:901](http://localhost:901) & cross your fingers !

---

### Post by Corolla92 on 2006-11-23
didnt work :(

---

### Post by Corolla92 on 2006-11-23
Anybody? Please, I really need this up and going within the next few days.

---

### Post by OldDogNewTrick on 2006-11-25
I think that problem was covered here:

[http://www.ubuntuforums.org/showthread.php?t=58434&highlight=swat](http://www.ubuntuforums.org/showthread.php?t=58434&highlight=swat)

---

