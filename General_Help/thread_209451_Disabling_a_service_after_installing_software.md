---
title: "Disabling a service after installing software??"
date: 2006-07-05
forum: General Help
---

### Post by johann_p on 2006-07-05
I used synaptic to install tomcat5 to make some tests. Now I would like to disable  the server to get started on boot ... I am fine to manually start it with /etc/init.d/tomcat5 start when I need it.

I looked at the System->Administration->Services GUI but while apache2 is listed here, tomcat 5 is not. Why?
And what other method would you recommend to disable the service?

I am pretty new to Ubuntu ... this worked all pretty differently in the Suse system I had been using until now. 

Another thing that is strange in that Services GUI is that 
  - *both* klogd and sysklogd are checked, with identical descriptions: is there some redundancy or are both needed?
  - *both* gdm AND kdm are checked: is this reasonable, required?
(I have installed the kubuntu package, but am still using gdm for the login screen and I switch between using GNOME and KDE sessions).

---

### Post by Ramses de Norre on 2006-07-05
This will remove the link that starts the service:
```
sudo rm /etc/rc2.d/S??tomcat5
```

---

### Post by johann_p on 2006-07-05
[quote=Ramses de Norre]This will remove the link that starts the service:
```
sudo rm /etc/rc2.d/S??tomcat5
```[/quote]

Thanks for that hing!
I found in the meantime a program "boot up manager" that provides a nice frontent and shows *all* services and boot scripts and it does seem to work too :)

---

### Post by Ramses de Norre on 2006-07-05
It does the same yes;)

---

