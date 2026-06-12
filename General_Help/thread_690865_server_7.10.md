---
title: "server 7.10"
date: 2008-02-07
forum: General Help
---

### Post by regtek on 2008-02-07
hi
so i just set up an old box i found around the house with linux 7.10 server on it now i can connect to it with putty and all that now i want to host a website on this box now is there a tutorial of some sort that i may look at that explains how to secure the server for public level and how i can upload and download files into the website www folder?  

thank you

~regtek

---

### Post by hamstersquasher on 2008-02-07
if your server is going to be headless and you are solely remoting to it , you can use NFS shares between linux and linux machines.  if you primarily use windows, you can install samba on the linux box to allow for SMBC/CIFS shares.  apache2 should be used for a webserver on the box.

---

### Post by mrsteveman1 on 2008-02-07
It's unlikely you can host an HTTP server on that box if this is a residential ISP, most ISPs block port 80 to prevent you from doing this.

If you really really want a public webserver, you should probably just spring for $5-10 shared hosting somewhere like netactuate.com. They use linux on their servers, are highly secure and have very fast networks. You'll also get a lot more bandwidth and transfer than a home account can possibly hope for.

---

### Post by regtek on 2008-02-07
thanks for ur reply.

my isp didnt block port 80 if thats what u mean but i am doing a linux to linux so ill give NFS share a try and im not planning on making it a big site its sorta a php practice and just overall web desgin and stuff. i am new to programming and i thought linux would be a good way to start and work my way up to high level programming.

---

### Post by hamstersquasher on 2008-02-07
you can get a dyndns account from dyndns.com.  It makes it possible to resolve dynamic IPs.  my ISP is Verizon and they don't block TCP 80 but legally i am not suppose to have my own 'server' of any sort with my package but oh well - i host my own website anyway.  if you ever wanted to get a real domain name, you can always use a blink URL redirect to your dyndns account like i did.  I just recently purchased robert-hopkins.com for $10.00 from godaddy and have it set to redirect to robertpaulhopkins.homelinux.com (free dyndns account)

---

### Post by mrsteveman1 on 2008-02-07
Basically all you need to do is install php and apache2,  then start apache and have a look over its config files (should be in /etc/httpd or /etc/apache2).

Install Apache

```
sudo aptitude install apache2
```

Install PHP5 and the Apache PHP5 module
```

sudo aptitude install php5 libapache2-mod-php5
```

Restart Apache

```
sudo /etc/init.d/apache2 start
```


The system should have webroot setup in /srv/www/htdocs by default so anything you install there should run correctly.

---

### Post by regtek on 2008-02-07
yep thanks for all ur replys ive got LAMP running on the server already and i did do dnydns only thing i was searching for was an efficient easy way to transfer files to my /var/www/ folder i have putty right now but thats command line basically im new to the terminal so i am not to acknowledged on how to upload and download stuff from terminal from different boxes.

---

### Post by mrsteveman1 on 2008-02-07
ahh ok.

What you probably want to use to transfer stuff is SCP or SFTP, which should be supported out of the box on the server itself.

You can use WinSCP from a windows box, since you said putty i assume your on a windows machine, but both of those work on WINE in linux as well.

Alternatively you can also mount ssh as a filesystem in linux by using sshfs

---

### Post by regtek on 2008-02-07
ok so SFTP seems to be ok at this point but how would i go about creating a remote directory on my linux machine to my server box ? 

if there is a guide u can link me to id be more than happy to read it. 

thank you for your help.

EDIT: also when i use scp to upload somthing it keep telling me that permission is denied.

---

### Post by mrsteveman1 on 2008-02-10
Basically SFTP and SCP both work within the permissions on the remote box.

You can resolve the permissions thing by changing the permissions on the directories such that you are either the owner of the directory, part of the group which has rights to that dir, or change it so that the "other" section of permissions allows writes.

IE to make a directory read/write for everyone, do:

```
sudo chmod -R 777 <directoryname>
```

If you are going to be using the commandline client for SFTP its relatively simple, most of the commands are the same as they would be locally. theres a simple reference [here]("http://kb.iu.edu/data/akqg.html")

If you are going to be doing a lot of transferring over SFTP or SCP i would recommend using WinSCP, even if you have to use WINE to run it in linux. It does both protocols and makes things a bit easier.

---

