---
title: "ProFTPD Config Problem in Dapper"
date: 2006-12-13
forum: General Help
---

### Post by Mr Wilson USCG on 2006-12-13
Hello, I have been trying to set up a development server here at work, we're just getting in to Linux and all of our support techs are MS only guys. So far everything has been going smoothly, I've been following a good guide and I have setup Ubuntu 6.06 LAMP with SSH. Now I am trying to configure ProFTPD which is supposed to be an easy config, but it's not working. 

I can connect, I can log in but when I try and put up a file I get this:
[img]http://www.jasonwilsondesign.com/images/ftpError.gif[/img]

](*,) 

No idea what is going on. Our Dev server is on a router that is running another server so I changed to config to run it off of port 2121. I'm sure all of that matches up which leads me to believe it is a permissions problem in Ubuntu, our FTP user goes right into var/www. I can't figure it out though.

Any ideas?

Thanks.

---

### Post by Mr Wilson USCG on 2006-12-14
Just an update because this is still driving me psycho.

After suddenly having permission problems on the web side of the server, I learned how to use chmod. The root folder for the webserver is not wide open and works fine, however, the FTP uses the same folder and still has permission problems. 

What on earth could this be, I've run out of places to set permissions from what I can see.

---

