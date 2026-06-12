---
title: "Synergy Help"
date: 2007-09-19
forum: General Help
---

### Post by mikeylikesit on 2007-09-19
Hi all i have a windows pc and a ubuntu 7.04 desktop that i would like to connect with synergy, i  have installed the client on both computers, but for some reason i can not get it to connect. any suggestions? I want my ubuntu box to be the server is this even possbile 

Thank 

Mike

---

### Post by aJayRoo on 2007-09-20
Absolutely, you should be able to set this up just fine. If you are not too confident with the command line you might want to install a graphical front-end for synergy in Ubuntu. Search in Synaptic package manager for 'quicksynergy' and install it. When you run this click on the server tab and type in the hostname (though often ip address works better) of your windows machine in the relevant box and start the server. Then you should be able to start up the client on the windows machine and connect to your Ubuntu machine. If you want to do something more complex then you may need to create your own configuration file and use the command line server, but for basic use quicksynergy should be just fine. Good luck, let us know how it goes.

---

### Post by mikeylikesit on 2007-09-20
great thanks, the error that i keep on getting from the windows box is that it starts up fine then it says: "not connected failed to connect to server" i was thinking that ubuntu could be blocking the port or something but i can not figure it out. 

thanks for the help guys

Mike

---

### Post by aJayRoo on 2007-09-20
That could be the case I suppose but I have never had a problem using Ubuntu as a synergy server. It could equally be the case that XP (or rather an application running in XP) is interrupting the connection. Usual suspects are firewalls (especially ZoneAlarm in my experience) either 3rd party or the windows firewall. You could try disabling your firewall in Windows temporarily to determine whether or not that is the cause.

---

### Post by mikeylikesit on 2007-09-20
hi all i got it to work fine, thanks for all the help, now my question is how do you switch between computers? i seem to only have to move the mouse to certain parts to the screen and other times it seems that i have hit the scroll Lock button and once it goes to windows i cant get it to go back to linux (the server) 

any help would be great 

thanks Guys!!! 

Mike

---

### Post by aJayRoo on 2007-09-20
You should be able to switch between screens just by moving to the edge of the screen. Not being able to get back from a screen indicates you have not set the server up properly. For instance, if I were using a laptop and a desktop it is not enough to tell synergy that the laptop is to the right of the desktop, I must also explicitly specify that the desktop is to the left of the laptop. How are you configuring your server, by text file or quicksynergy? This problem should not occur when using quicksynergy, but forgetting to define both screen relationships is a common problem when configuring the server manually or using Windows as a server. Let me know what configuration method you are using and how you are starting the server (if starting manually) so your issue can be fully resolved.

---

### Post by mikeylikesit on 2007-09-21
Thanks all i got it to work fine, took a little bit of configuring but it works like a champ now 
thanks for all that helped!

---

