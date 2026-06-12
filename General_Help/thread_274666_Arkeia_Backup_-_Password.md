---
title: "Arkeia Backup - Password?"
date: 2006-10-10
forum: General Help
---

### Post by Ted_Smith on 2006-10-10
Just installed the GUI version of Arkeia Ubuntu package from [www.Arkeia.com](www.Arkeia.com) and installed it. When I run it, it comes up with the name of the localhost (that being the machine I am running it on) and it asks for a password. 

If I leave it blank it says connection refused, and if I use the log on password for the user account I'm using it says the same. 

Having read some of the threads in their forum, a french guy seems to suggest that you have to install the arkeia server seperalety. I have spent ages trying to find a seperate server install, and all I could find was this : 

 
[ftp://www.arkeia.com/pub/arkeia-6.0/arkeia-network-backup/linux/amd64/TARGZ/glibc2.3/arkeia-6.0.0.tar.gz](ftp://www.arkeia.com/pub/arkeia-6.0/arkeia-network-backup/linux/amd64/TARGZ/glibc2.3/arkeia-6.0.0.tar.gz) 
 

which is invalid. 

Any ideas?

Thanks

Ted

---

### Post by coincoin on 2006-10-10
Hello,

Change the Login/Password in /opt/arkeia/arkc/arkc.param and try to connect on localhost.

++

---

### Post by Ted_Smith on 2006-10-10
I edited the file and entered 'localhost' for the value of 'NODE', I entered the username of 'ted' for the username and a password for the password value. Saved. Re-started utility. Keeps saying 'Incompatible Server Version'.

It's all based on the fact that I have not run the server installation I think. The website keeps making reference to arkeiasb-server_<version>_<architecture>.deb, but I cannot find this to download ANYWHERE!! I thought I'd cracked it when I found this : [http://rpms.mandrivaclub.com/rpms/AByName.html](http://rpms.mandrivaclub.com/rpms/AByName.html) but no - the downloads do not work!!! AAAAaaaaarrrrrggggghhhhh!!!

---

### Post by Ted_Smith on 2006-10-10
I am an idiot!!

Found it here : [ftp://www.arkeia.com/pub/arkeia-5.4/arkeia-smart-backup/server/linux/ia32/debian3.1/arkeiasb-server_5.4.3-1_i386.deb](ftp://www.arkeia.com/pub/arkeia-5.4/arkeia-smart-backup/server/linux/ia32/debian3.1/arkeiasb-server_5.4.3-1_i386.deb)

I didn't realise that the two versions of Arkeia have two different server utilities that you have to install. I was using the wrong server app for the type of Arkeia that I was using. 

Thanks for help - hopefully my reply may help others.

---

