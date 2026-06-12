---
title: "MythTV Setup Woes"
date: 2005-03-19
forum: General Help
---

### Post by kaptk2 on 2005-03-19
I am making a switch from Fedora 3 to Ubuntu for my mythtv box.  I had Mythtv working in FC3 fine, there were plenty of things that bugged me though in FC3 so that is why I made the switch.

Here is how I setup my box:
Did a normal install of Ubuntu
After the inital boot up I logged in and added the universe and multiverse packages to my /etc/apt/sources.list

I then added samba server, apache2, mysql-server to my install.

I setup mysql-server like this:
```
sudo mysqladmin -u root password mynewpassword
``` 
After that I compiled the ivtv drivers for my Hauppauge PVR-350 card and then proceded to try and install MythTV.

To do that I did this:
```
sudo apt-get install lame mythtv
```
I was then prompted to enter mysql root password which I did (mynewpassword)
Then I created a password for the new mythtv user (sudo passwd mythtv)
After that I was able to log in and run the mythtv-setup program.

After everything was all setup I went to start the mythtv-backend like this:
```
sudo /etc/init.d/mythtv-backend start
``` 

I get this error message:
```
Starting MythTV server: mythbackendQSettings: error creating /home/andrew/.qt
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

``` 

I did try to make the file manually like this:
```
touch /home/andrew/.qt
``` 
That did not have any affect.

Any idea on how to make this work?

---

