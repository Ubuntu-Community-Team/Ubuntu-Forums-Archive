---
title: "Help with ftp server"
date: 2007-05-13
forum: General Help
---

### Post by tic84 on 2007-05-13
On windows I use serv-u ftp to host my ftp server, but since switching to Ubuntu, the main program that has been holding me back is not having an ftp server. I have tried a few, including pure ftp and proftp.

I need an ftp server that can add separate users with differing file permissions and different upload speed caps. I would also like to be able to monitor the activity of the ftp server without having to do it through a webpage.

So basically I'm asking if theres a gui based ftp server for linux that is reasonably powerful.

I tried using gproftp, but couldnt figure out how to set different upload speed caps and have those users on the same port. If there is no such program, then would someone be able to give me an example config file for proftp or similar (with usernames and passwords removed of course :) ) so that i can edit it for my own use as this seems trickier than I expected

---

### Post by luckyaba on 2007-05-13
I don't know about a GUI but if your looking for a very configurable FTP server VSFTP is great. I used it for quite some time and never had any complaints. 

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)

---

### Post by Wim Sturkenboom on 2007-05-14
User accounts and file permissions are basically the responsibility of the OS and noit of the FTP-server. So you 'simply' setup local users.

I don't know about the capping.

For vsftpd, you can look [here](http://www.brennan.id.au/14-FTP_Server.html) how to configure it.

Attached is my config for vsftpd). Please note that I use SSL and only allow myself for FTP. Further I just noticed that I allow anonymous (which is not the intention).

---

### Post by tic84 on 2007-05-16
thanks very much for the example ftp conf. ill have a look at it as soon as i can, but have final exams at the moment. i wish they would go and port a nice graphical ftp server to linux though. youd think thered be even 1! hopefully serv-u get a move on an do the port

---

