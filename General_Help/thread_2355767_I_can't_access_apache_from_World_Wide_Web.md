---
title: "I can't access apache from World Wide Web"
date: 2017-03-16
forum: General Help
---

### Post by kainblock on 2017-03-16
I am trying to set up apache for educational purposes. Yesterday all works fine but today i cant access my server from Internet. So i check ports again and all is fine. All ports online tools successful reach my port. 
I am trying different ports with no success. 
I am trying```
 sudo apt-get purge apache2
``` and reinstall but no luck.
Now my ports.conf contains :`
> # If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen *:8000

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet



i am trying this from my server:

localhost:8000 WORKS
<local_ip>:8000     WORKS
<Public_Ip>:8000  REFUSE TO CONNECT

I am trying also <Public_Ip>:8000 with devices which connected out of LAN but still REFUSE TO CONNECT

---

### Post by SeijiSensei on 2017-03-16
Where is the server located?  Does it have a public IP address, or is it behind a router?  If the latter, have you configured port forwarding?  Does the server have an iptables firewall?

---

### Post by kainblock on 2017-03-16
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") thank you. You are responding faster than my server.

Actually server located in my personal laptop so is located in my LAN network. 
I am not have a static ip address if you mean that but check for my public ip address with various ways and i am trying to connect as i said before  " <Public_Ip>:8000 ". 

 [[IMG]http://pix.toile-libre.org/upload/img/1489678157.png[/IMG]]("http://pix.toile-libre.org/?img=1489678157.png")
I configure ports as said. Analytically change the line "Listen 80" to "Listen *:8000" . Set up my router and apply settings 
Check ports if works fine at [http://canyouseeme.org/](http://canyouseeme.org/)
I disable my router firewall and thats my iptables
```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

---

### Post by yancek on 2017-03-16
The IP Address you have in your last post is for local networks only.  You should be able to access it from another computer on the local network but not from outside unless, as indicated above, a public IP address.  Mont internet providers do not allow running a public server on a home computer system unless you pay an additional fee.  Not sure if this is your case as you said yesterday it all worked.  Does that mean you were able to access the server on your laptop from outside the LAN?

---

### Post by kainblock on 2017-03-17
> **yancek said:**
> The IP Address you have in your last post is for local networks only.  You should be able to access it from another computer on the local network but not from outside unless, as indicated above, a public IP address.  Mont internet providers do not allow running a public server on a home computer system unless you pay an additional fee.  Not sure if this is your case as you said yesterday it all worked.  Does that mean you were able to access the server on your laptop from outside the LAN?

Thanks for reply yancek. 

I change WAN Host End Ip Address to 254.254.254.254. My ISP instructions write "set them all zero". I cant understand the reason of working 2 days before with "all set zero" configuration. Never mind i will find that myself. Problem is solved ;)

I access my laptop outside the Lan via Mobile Data from my android device.

---

