---
title: "How to i setup my registered domain name to point to my web server"
date: 2007-09-28
forum: General Help
---

### Post by Uottawaess on 2007-09-28
I currently have feisty faun running with drupal 5.1, my question is how do i make my drupal site viewable from the internet ? and how do i make the url stay as [www.uottawaess.ca](www.uottawaess.ca) (the one i have registered)

thanks very much

---

### Post by GavinZac on 2007-09-28
you need to set up a domain name server.

I havent the foggiest idea how to do that, but I am interested.

---

### Post by SeanTater on 2007-09-28
I may be wrong, but I think you will only need a nameserver if you are going to use subdomains. Most likely, you can find your public IP address, by accessing [www.whatismyip.com](www.whatismyip.com) and then point that domain name to that IP.

---

### Post by joselin on 2007-09-28
You could use bind to do it, is the most powerful dns server.

---

### Post by Uottawaess on 2007-09-28
So like when i have my static ip up and running i redirect my domain name to [http://my_static_ip_here/drupal](http://my_static_ip_here/drupal) ???

Because currently my site [www.uottawaess.ca](www.uottawaess.ca) points to [http://www.genie.uottawa.ca/~essaeg/](http://www.genie.uottawa.ca/~essaeg/) which is where our current website is located on the university server. So i am worried that when someone types in [www.uottawaess.ca](www.uottawaess.ca) it wont say [www.uottawaess.ca](www.uottawaess.ca) , it will say [http://my_static_ip_here/drupal](http://my_static_ip_here/drupal) . 

Is there any way to ensure this does not happen?


Cause installing ubuntu was no problem whatsoever, same with installing drupal and getting all my tables and stuff up. 

I've just never had to worry about hosting on my own webserver before.

---

### Post by joselin on 2007-09-28
> **SeanTater said:**
> I may be wrong, but I think you will only need a nameserver if you are going to use subdomains. Most likely, you can find your public IP address, by accessing [www.whatismyip.com]("http://www.whatismyip.com") and then point that domain name to that IP.


You are wrong, you must use a dns server.

---

### Post by Uottawaess on 2007-09-28
I'm kind of confused, i read the how-to on how to setup a dns server with bind but i can't figure out how im supposed to fit the domain name i purchased into there as the domain name still has to be pointed to a url. 

Is the dns server/w bind basically saying that my static ip IS whatever the domain name I enter.



I noticed on your site ( looks like a drupal site) you have a registered domain name that works the way i want it to. 

I'm assuming you did that with Dns w/ bind ?

---

### Post by Uottawaess on 2007-09-28
im mainly confused cause when i looked up my webhoster they have 2 name servers up already


NS1-Hostname:   ns1.webnames.ca                                   
NS1-Netaddress: 65.39.140.92                                      
NS2-Hostname:   ns2.webnames.ca                                   
NS2-Netaddress: 192.73.5.105    

so im confused on what i should do in the guide

---

