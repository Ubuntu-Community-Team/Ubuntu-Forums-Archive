---
title: "Ubuntu 18.04 and Locally Hosted wordpress installations."
date: 2018-09-19
forum: General Help
---

### Post by crocspot on 2018-09-19
I expect I've put this in the wrong place however I could find very little in google to provide specific guidance regards current installation details for Wordpress and Ubuntu 18.04 the latest LTS.

This assumes you know what ports to forward / NAT and how to do it ? If not give me a yell :D

So here goes :popcorn:

Follow the guide at 

[help.ubuntu.com/lts/serverguide/lamp-overview.html.en]("https://help.ubuntu.com/lts/serverguide/lamp-overview.html.en") 
 
This is pretty comprehensive guide and should get you going for all intents and purposes.

I just installed as per the guide the PHP Admin and Wordpress, including the mySQL section on the Wordpress page

There may be one glitch following that guide re mysql perms and / also / or DNS ?

 Let me know if you hit it and I'll update this doco and record the mysql and DNS problems I'm just not sure if that was just me or not ?

After all that you just need to also enable web uploads and updates within Wordpress on your website etc.
 
chown -R www-data /usr/share/wordpress (this took me forever to figure out noting the below)
 
Igonre all the doco that points to /var/www/wordpress installs as that's not Ubuntu 18.04's install path. As per above ; 
 
/usr/share/wordpress is the path for Ubuntu 18.04

Well hope the search engine of your choice finds this and makes your life a little easier. Having "come" out the other end of the rabbit hole just let me know if you run into any problems. I'm no expert but I'm happy to help where I can and I'm sure there's far more qualified people to assist available as well.

All the Best ):P

Kronk

:guitar:

---

