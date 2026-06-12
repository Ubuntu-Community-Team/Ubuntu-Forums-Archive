---
title: "how to make ntfs mounted partition writeable"
date: 2005-07-24
forum: General Help
---

### Post by diffuser78 on 2005-07-24
In [www.ubuntuguide.org](www.ubuntuguide.org) its specified how to make How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?

How to write on the windows partition from Ubuntu ?

Dan

---

### Post by aggiechemist on 2005-07-24
General answer: You don't.

Sorry for this bad news, but Linux generally has a really hard time writing to NTFS. FAT and FAT32 are fine, but Linux cannot write on NTFS. Reading is fine, but writing is not. There is a research effort to fix this (look around sourceforge.net for info), but it is not ready yet.

Sorry to be the bearer of bad news.

---

### Post by skatedawe on 2005-07-24
I don't think you could do it, cause linux doesn't support it.

 Maybe becuase NTFS is a Microsoft invention :/.

---

### Post by karim_eng on 2008-03-09
The Following way for Kubuntu

Go to your Konsole
First add the repositories in your sources list:

Command:
kdesu kate /etc/apt/sources.list

This command will open a file, add these lines to the bottom of the file, and click save then close the opened file

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) edgy main main-all
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all

Add the gpg key:
Command: (you dont have to write the following command if you are kubuntu 7.10)

wget [http://flomertens.keo.in/ubuntu/givre_key.asc](http://flomertens.keo.in/ubuntu/givre_key.asc) -O- | sudo apt-key add -

Update your system:

Command:
sudo apt-get update
sudo apt-get upgrade

Now install the packages:

Command:
sudo apt-get install ntfs-3g ntfs-config

Now enter the ntfs config:

Command:
kdesu ntfs-config

Now you can read/write NTFS partitions!

---

### Post by sandysandy on 2008-03-09
that was a very old post of 2005. 
with gutsy 7.10 there is no problem in reading  / writing to NTFS.

regards

---

