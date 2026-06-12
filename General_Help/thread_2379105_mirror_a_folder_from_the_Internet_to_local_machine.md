---
title: "mirror a folder from the Internet to local machine"
date: 2017-12-01
forum: General Help
---

### Post by atux on 2017-12-01
I have a machine in my LAN that runs *Ubuntu* and I have full access in it.
There is another PC on the Internet that has a public IP eg 3.3.3.3 and it servers as **https server** and access to it is by username and password. 
At the moment I'm logging to the *ubuntu* and using wget to get folders that I want. 
I would like to automate the boring stuff and every 1 hour to check if the server has new content compared to the ubuntu's /var/www/html/x3 and /var/www/html/y7 local folders.
 The Internet server has as series of folders eg x1, x2,...,xn, y1,y2,...,yn. i do need to get only 2 particular folder and its contents and not the whole server. 
If those 2 folders have different content, then download the new content and delete the old ones in the corresponding folder. 
It is a one way sync. is there any script that could do the job with cron, please?

---

### Post by leunam12 on 2017-12-01
You have to use rsync and ssh to accomplish that.
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by atux on 2017-12-08
hi. i took a look to the link you've send me about rsysnc and it looks nice. The problem is that i have only https access to the server and nothing else. So how could i use the rsysnc tool? Also the server might have a folder called g1 with file01, file02, file03 and after 2 hours delete all files and have only file56, file 65, file67. i would like to have the same structure in my server, please. as i said now everything runs manually and someone runs wget once per day. I  would like to automate it and run it every 30minutes and download only if there are different files.

---

### Post by leunam12 on 2017-12-08
Oh, so you don't have ssh access to the server?

---

### Post by atux on 2017-12-08
no, i do not have ssh access to the server

---

