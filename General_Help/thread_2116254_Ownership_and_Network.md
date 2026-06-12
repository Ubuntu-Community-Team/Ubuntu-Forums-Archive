---
title: "Ownership and Network"
date: 2013-02-15
forum: General Help
---

### Post by oeeve on 2013-02-15
Hi,

I just have some general questions about shared folders. On ubuntu 12.04 I've share the folder /home/shared and chmod it 777, because I want everyon on the local network to be able to create/delete stuff in it. ... But even still, if the location /home/shared is chmoded 777, all files created there from other clients will get drwxr-xr-x and owner and group usually set to noboy nogroup. 

Everytime I then log in to the ubuntu account and want to move/delete the files in /home/shared .. I have to go through the terminal as sudo.. cause right-click "cut" is obviously does not working when the files have different permissions and not property of this particular user account.

Is it possible to make all files created in that particular shared folder keep the same permissions as the folder (i.e 777)?

---

