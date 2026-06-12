---
title: "proftpd howto"
date: 2007-10-11
forum: General Help
---

### Post by SpikeyMike on 2007-10-11
Hi, I have installed proftpd and followed this howto:

[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

but when I restart proftpd I get the following error message:

[COLOR="Red"]mikey@MyUbuntu:~$ sudo /etc/init.d/proftpd restart
 * Stopping ftp server proftpd                                                                                 [ OK ] 
 * Starting ftp server proftpd                                                   
 - IPv4 getaddrinfo 'MyUbuntu' error: No address associated with hostname
 - warning: unable to determine IP address of 'MyUbuntu'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                                                                                      [fail]
mikey@MyUbuntu:~$[/COLOR] 

can anyone point me to an easy to follow howto for this, any help appreciated 

Spikey

---

### Post by Belinrahs on 2007-10-11
SpikeyMike:

Do you connect through a router?

---

### Post by gaebriel on 2007-10-11
make sure your /etc/hosts file is updated to include a line that says: ```
LOCAL.IP.ADDRESS.HERE    myubuntu
``` 
otherwise your system won't be able to determine the IP address of itself. Either that or update the proftpd.conf file to use the local IP address for the server instead of it's name if that's what you have in there now.

---

### Post by SpikeyMike on 2007-10-12
> **Belinrahs said:**
> SpikeyMike:

Do you connect through a router?

yes, I have a modem/router in one......

Spikey

---

