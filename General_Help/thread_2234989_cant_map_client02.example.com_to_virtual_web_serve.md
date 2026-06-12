---
title: "cant map client02.example.com to virtual web server."
date: 2014-07-18
forum: General Help
---

### Post by nos09 on 2014-07-18
I am trying to map all my subdomains to different IPs but this perticular server is giving me headache ..

So the scenario is I have mapped my ec2 instance's elastic ip to client02.example.com but it always points to '/var/www/html'. 

With ip however, its running fine. its configured with /etc/apache2/site-available/default. I tried to add 'ServerAlias' with domain name but its just doesnt seem to work. 

so I copied it and I have created client02.example.com.conf from default and just changed server name to client02.example.com. then I enabled the site by a2ensite. but still not working ... 

my other server client01 (exact copy of client02 with different ip) works just fine with domain name.. i didn't even have to change anything .. just mapped the domain name to the ip and it works.

can anybody help me with this ?

---

