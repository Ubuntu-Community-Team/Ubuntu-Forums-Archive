---
title: "Adding domains to the server?"
date: 2008-06-18
forum: General Help
---

### Post by gamingneeds on 2008-06-18
Probably a very stupid question, but how do you add domains to your server so it can host your websites?

I just got a server and installed LAMP, so now I need to know how to host a domain on the server.

Thanks.

---

### Post by gamingneeds on 2008-06-18
I have some domain names I purchased and want to put them on my server. How do I do this?

Thanks.

---

### Post by cariboo on 2008-06-18
Check out this link:

[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

Jim

---

### Post by gamingneeds on 2008-06-18
Wow that is crazy. That is a lot of work to host a domain!

So if I wanted to run a script on these websites, like lets say I wanted to run a blog on both sites, first I would have to add each site in the sites-enabled folder, and then install the blog script where? inside each site folder?

---

### Post by Rocket2DMn on 2008-06-18
If you are using a single machine, you should just have to setup LAMP (or at least just Apache) and have the people you bought your domain name from set your public IP as the destination for the domain.  Then you have to configure your router to forward the web server port to the outside world (usually port 80).  That is a very simple setup - no subdomains, no other servers except your one box.

---

### Post by gamingneeds on 2008-06-18
I'm trying to put some real website up on the web. Like JohnDoe.com or JaneDoe.com. Something anyone can access, like real websites!

Isn't that what most people use servers for?

---

### Post by Rocket2DMn on 2008-06-18
Servers are used for many things, and web hosting is one of them.  You can setup your own website on your own server computer.  Apache is web hosting program, so you need to install LAMP on your server then get yourself a domain name.  You did the first part, and now you need to purchase a domain name.  You can google around for that, there are plenty of companies that will sell you domain names and even online space if you don't want to host the server yourself which is what most people want.  Ex: godaddy.com
You seem interested in running the server yourself, which is cool, but you just need a domain name.
An alternative to getting a plain [www.something.com](www.something.com) domain name is to get a free DNS, like mypage.somehingelse.net - check out [http://www.dyndns.com/](http://www.dyndns.com/) 
 - register there for free and checkout Dynamic DNS.  They might even be willing to sell you a real domain name, too.  Basically, they just tie your public IP to a domain name.  This allows other people to access your website hosted on your computer.

---

### Post by gamingneeds on 2008-06-18
Hey bud, I already have a handful of domains I want to host on my server that I have already purchased. Now what?

---

### Post by cszikszoy on 2008-06-18
30 seconds of googling brings up these results:

[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)
-probably your best bet - from apache's own documentation
[http://webdesign.about.com/cs/apache/a/aa051301a.htm](http://webdesign.about.com/cs/apache/a/aa051301a.htm)
-might be a little helpful, although not as comprehensive
[http://www.google.com/search?hl=en&safe=off&q=apache+add+domain&btnG=Search](http://www.google.com/search?hl=en&safe=off&q=apache+add+domain&btnG=Search)
-the actual google search

Remember - google is your friend.

---

### Post by Rocket2DMn on 2008-06-18
You need to go back to where you purchased those domains and have them direct themselves to your public IP - see [http://whatismyip.com/](http://whatismyip.com/) to find your IP.
If you are hosting different websites on different domains, you will want to be running multiple instances of apache on different ports, then have those domains direct to the correct port, like youriphere:aoacheport

---

### Post by cszikszoy on 2008-06-18
> **Rocket2DMn said:**
> 
If you are hosting different websites on different domains, you will want to be running multiple instances of apache on different ports, then have those domains direct to the correct port, like youriphere:aoacheport

You don't need to run multiple instances of Apache.  You can serve hundreds of different domains with only one instance of Apache.  This is all done through name-based and IP-based virtual hosts.

---

### Post by Rocket2DMn on 2008-06-18
> **cszikszoy said:**
> You don't need to run multiple instances of Apache.  You can serve hundreds of different domains with only one instance of Apache.  This is all done through name-based and IP-based virtual hosts.

Indeed.  I do not know much about more advanced apache configuration like that, though.  Please feel free to enlighten us :)

---

### Post by gamingneeds on 2008-06-19
So I don't even know where to begin.

Where do I put these files? I read the through the info that csziksoy gave me but I don't know where the **httpd.conf** file is so I can add domains to it. Then, do I just make new directories in the /var/www/ folder like 'mydomain.com' and put all the files in there?

Also, I installed PHPMyAdmin fine, or so I thought, but when I go to myip.com/phpmyadmin/ it just goes to a blank white screen. :(

Thanks in advance for the help.

---

### Post by cariboo on 2008-06-19
You may want to have a look a webmin it is available in the repositories you can install it using synaptic. Here's a link to the website, 

[http://www.webmin.com/](http://www.webmin.com/)

you can check out their demo site and there are lots of screenshots

Jim

---

### Post by gamingneeds on 2008-06-19
That is cool, I probably will use it. Will it help me initially setup domains?

Thanks.

---

### Post by gamingneeds on 2008-06-19
Do you know the ssh command code to grab it?

---

### Post by rwalsh on 2008-06-28
You are probably going to need these dependencies so do
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

and it should install webmin as well if it doesn't, follow up with
dpkg --install webmin_1.420_all.deb

---

