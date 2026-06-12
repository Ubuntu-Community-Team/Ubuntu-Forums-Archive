---
title: "Hi everyone looking for a little help with setting up a Samba file sharing Box"
date: 2019-05-15
forum: General Help
---

### Post by martsmac on 2019-05-15
Hi everyone,

So I'm pretty new to linux/unix and am currently running the LTS version of Ubuntu server which I have setup an LVM on with my storage disks and formatted them to NTFS so that windows will be able to read and write to them. I am struggling with the way that linux handles mounting of drives and file systems etc and getting Samba set up. My drive structure is as follows.


/var/lib/samba/MEDIASTOREAGEPOOL <<<This is where I currently have my media folders stored that i will be sharing (as of right now i have not transfered my media over so everything can still be wiped and I can still start again if necessary....


When I used to run this server on a windows 10 box I had it installed with the OS on a seperate ssd )just going to leave this the default ext format for the ubuntu OS

I then had all my storage drives (just shy of 10 TB set up using a storage spaces pool) I'm trying to re-create this kinda setup but using linux instead of windblows.

any help would be much appreciated.

---

### Post by HermanAB on 2019-05-15
There are many a book on Samba, which are worth reading.

Otherwise:
[https://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf](https://www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf)

---

### Post by martsmac on 2019-05-15
Thanks but it's more the fact that setting up the samba share on the seperate LVM (not the OS Drive) and making sure I have it mounted correctly that I'm having issues with

---

### Post by Morbius1 on 2019-05-16
I'm going to regret getting involved in this because I have no experience with using LVM but you stated that you have have a mountpoint at /var/lib/samba/MEDIASTOREAGEPOOL. 

Have you tried to create a samba share to that mount point and it doesn't work?

You might want to run the following command on the server and post the output so folks who understand LVM and Samba can see how you are set up:
```
testparm -s
```

You also might want to tell folks the operation system on the clients - it makes a difference in how you set up the samba server - at least in a home lan.

Miscellaneous side notes:

** There are no Samba Books that are current.
** The link to the pdf file above is 9 years old and doesn't reflect where we are today. Example from the pdf:
> Example 2.3.1 Anonymous Read-Only Server Configuration 
# Global parameters 
[ global ] 
workgroup = MIDEARTH 
netbios name = HOBBIT 
s e c u r i t y = share 
[ data ] 
comment = Data 
path = / export 
read only = Yes 
guest ok = Yes 
That smb.conf file as presented will prevent your samba server service from starting.

** Although it's not worth changing now but you didn't have to format the storage disks to NTFS. Samba provides an abstraction layer that hides from the client the inner workings of how the filesystem works on the server.

---

### Post by him610 on 2019-05-16
A couple of months ago, I found this website helpful, [https://linuxconfig.org/how-to-configure-samba-server-share-on-ubuntu-18-04-bionic-beaver-linux]("https://linuxconfig.org/how-to-configure-samba-server-share-on-ubuntu-18-04-bionic-beaver-linux")

---

### Post by HermanAB on 2019-05-16
Just a few notes:
If it is a home server, or a very small business server with a handful of trusted users, then you can set up an Anonymous FTP server instead.
The advantage is that you then have absolutely no issues with user names, passwords etc. - since there aren't any.
An Anonymous FTP server is insecure, but a Samba server is insecure also, anyway.
The file system on the server should be a Linux file system, such as Ext4 so that Linux can fix disk errors properly - it cannot fix NTFS errors.
If you have a larger number of users and want proper control over users and which files and directories they can access, then a document management system is better than a file server (Opendocman, Mayan, Nuxeo...)

---

