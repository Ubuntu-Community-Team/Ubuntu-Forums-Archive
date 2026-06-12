---
title: "word press issue?"
date: 2008-04-01
forum: General Help
---

### Post by evilbuntu on 2008-04-01
i also have this post on the wordpress forum but am not having luck there so im tryng here too




hi this is second time installing wordpress for a project i am doing on ubuntu server.

i followed all the same steps as the first install but when i get to the part where you enter the

[http://localhost/wordpress/wp-admin/install.php](http://localhost/wordpress/wp-admin/install.php)

it tells me

The requested URL /wordpress/wp-admin/install.php was not found on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 Server at localhost Port 80

can someone tell me what i may be doing wrong. i have created the MySQL database and user the same way as last time it just doesnt want to work.....?

---

### Post by Oldsoldier2003 on 2008-04-02
> **evilbuntu said:**
> i also have this post on the wordpress forum but am not having luck there so im tryng here too




hi this is second time installing wordpress for a project i am doing on ubuntu server.

i followed all the same steps as the first install but when i get to the part where you enter the

[http://localhost/wordpress/wp-admin/install.php](http://localhost/wordpress/wp-admin/install.php)

it tells me

The requested URL /wordpress/wp-admin/install.php was not found on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 Server at localhost Port 80

can someone tell me what i may be doing wrong. i have created the MySQL database and user the same way as last time it just doesnt want to work.....?

post your /etc/apache2/sites-available/default

---

### Post by evilbuntu on 2008-04-06
hi and thanks for the response... i truly appreciae it, but i actually figured it out.

for some reason when i did the second install of the wordpress it created another apache virtual server in my webmin. i GUESS (?) as in im very bew to most of this, it caused a conflict of sorts because when i found it i deleted it and restored my original default apache server back to var/www instead of the var/www/wordpress it was/. after this all seemed to go fine with my site hosting and wordpress. only oproblem is cablevision my isp blocks the ports for personal hosting, and i have tried to PAT the line with so many others i just gave up/. i dont have 65000 ports of time so i just bought godaddy hosting space for my senior project.

but on this hand could anyone tell me why this double apache server issue caused this problem as in i love to know WHY things happen and thought the problem is fixed i dont know why lol.

also when i fixed this my apache 2 folders site enabled and availalbe lost all their coding (?)/ text and replaced them with a second wordpress fille next to them. i deleed the wordpress file and replaced the two originals with a friends and everything seems to to be.

also if wnyone knows another way to get around the port hosting problem i would love to ehar it as i woulve love to host my own blog....

---

