---
title: "can't access internal hdds on multiple users"
date: 2012-12-18
forum: General Help
---

### Post by jphl on 2012-12-18
I'm fairly new to linux just trying to experiment with a file server.  I have an 80 gb drive for the system and a few 1 and 2 tb drives for data.  I formatted my internal data drives to ext4 but when I tried to write to them I couldn't searching online someone said that it was because root was considered the owner of the drive and gave me directions to change the ownership of the drive to my main account.  I did this and setup samba and can access the share on my other computers.  however I also wanted my parents to be able to do so with their own accounts so I made the accounts on ubuntu and in the gui I use to configure samba but I get access denied when I try to access them on the network using those accounts.  so i tried logging into their accounts on ubuntu and was surprised to find that the drives were mounted but I couldn't access them.  the error message said something about not being a folder.  I could unmount the drives using my main accounts password and then remount them using it again and access them but they still can only be read by that user then not my main till i unmount and mount them again.  what can i do to fix this and get the drive accessible by all users?

---

### Post by drdos2006 on 2012-12-18
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Allows your browser to connect and modify your server settings on your network, start and stop processes, change permissions etc.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.610_all.deb

Install with :
sudo dpkg -i webmin_1.610_all.deb

Add extra libraries with :
sudo apt-get -f install

```


regards

---

