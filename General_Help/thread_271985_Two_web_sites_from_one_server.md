---
title: "Two web sites from one server ??"
date: 2006-10-05
forum: General Help
---

### Post by SteffJay on 2006-10-05
I have now got Ubuntu (Dapper Drake) up and running and is very stable :cool:  Now i want to run two web sites from one server using Apache2. Does anyone know how this can be done ?. I can only show the default Apache web page at the moment. Any help here would be greatly appreciated. ;)

---

### Post by Old Pink on 2006-10-05
[http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server)

Should help you. :) Got a link to your server?

---

### Post by SteffJay on 2006-10-05
Thanks for the quick reply Matt.H  but I have all that installed, up and running. The problem is.....  i need to know how to get it to serve 2 x web sites at the same time....  Have'nt even done one yet.....   lol

---

### Post by ezenaide on 2006-10-05
you can try make two folders inside /var/www/ and write an index.html with links to each folder.

but you are trying to host a web server or just using like localhost?

anyway, it'll work to both...

---

### Post by SteffJay on 2006-10-05
I'm ttrying to make a web server ....  I have made 2 x folders both containing an index.html but it still finds the Apache2 default site.......  :(

---

### Post by ezenaide on 2006-10-05
hm... i mean you should write an index on /var/www/ folder, wich will have links to the folders where you put the sites.

like:

/var/www
        index.html
        /site1
        /site2

localhost will return your index.html and you'll be able to access your sites.

---

### Post by .t. on 2006-10-05
Look up on the Apache2 documentation about VirtualHosts (or, if you so wish, NameVirtualHosts). This is where Apache interprets the HTTP header to see which site you want, and sends that one back. It's quite easy to set up. You will need modified versions of /etc/apache2/sites-available/default, placing them in /etc/apache2/sites-available/, and running a2ensite on that site (with the argument being the basename of the file). That's a rough outline for you. Hope it helps.

---

### Post by SteffJay on 2006-10-05
Any demo available ?  lol

---

### Post by .t. on 2006-10-05
Demo in what sense?

---

### Post by SteffJay on 2006-10-05
How its all done.........  Total noob here you know.......
](*,)

---

### Post by .t. on 2006-10-05
[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

If you still have trouble after reading through that, post here, and I may upload my config (with private stuff erased, of course). I think it'd be good for you, though, if you wrote the configs yourself. You will gain knowledge, wisdom, understanding and of course confidence! Look at /etc/apache2/sites-available/default (I think that exists on a default install...), and /etc/apache2/apache2.conf for nice commented config files. Read through them, and you should have no problems!

---

### Post by SteffJay on 2006-10-05
Ok, thanks .t. I'll give it a bash.......  Your right of course, doing it yourself is the best way but you have to know how to do it first...   lol  ;)

---

### Post by .t. on 2006-10-05
Nah! You don't know how to do it, but you will once you have. I didn't until a few weeks ago. A few weeks before that, I didn't even know how to administer a server via SSH. I learn by doing! :)

---

### Post by SteffJay on 2006-10-05
;)

---

### Post by SteffJay on 2006-10-06
Ok.  having looked at all of this and looking at the default in Apache2, there is no resemblement to what i have and whats on the web site....  Soooooooooo....  if you would'nt mind **.t.** if you can send me a copy of your setup, i would greatly appreciate it. It's a bit like reverse engineering, lol......  ;)  Thanks in advance.......

---

### Post by .t. on 2006-10-07
I have attached my config.

---

### Post by SteffJay on 2006-10-07
Ok..  **.t.**, Thanks for the setup. I have not installed it yet though. I have got to the stage of setting up both sites and one runs ok but the other keeps being directed to the first one. Heres a site i have been looking at....  [http://linuxhelp.blogspot.com/2006/02/host-websites-on-your-local-machine.html]("http://linuxhelp.blogspot.com/2006/02/host-websites-on-your-local-machine.html") I have done everything that it has suggested. The only problem is, when i restart apache2, it gives an unknown VirtualName for web 2 !! Cant get my head around it as yet ](*,) . Any ideas ?

---

### Post by SteffJay on 2006-10-08
Well....  I have managed to get both web sites working now. The only problem that remains is, when i start Apache2, from the terminal, it gives a warning......  **[warn] NameVirtualHost website2:80 has no VirtualHosts [ok]** but they are both running ok :confused:  Can anyone give me an idea how i can rectify this problem ?

---

