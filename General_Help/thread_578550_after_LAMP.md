---
title: "after LAMP?"
date: 2007-10-17
forum: General Help
---

### Post by poisonmushroom on 2007-10-17
Hello,

I have followed a tutorial i found using google to install LAMP on my server and it all worked fine! i have php, mysql and apache on my ubuntu machine.

Now that i'm done with installing LAMP, what do i do now? I mean if someone can lead the way for me it would be nice heh, this is my frist time doing a server and would love to see how to work with it.

Thanks! :)

---

### Post by p_quarles on 2007-10-17
There are a lot of things you can do. It just depends on how you want to use it.

Could you post a link to the tutorial you used? There are a few different ways of installing this setup, so it would be helpful to know which method you followed.

---

### Post by LanDan on 2007-10-17
well if you want to waddle the waddle and try to set up several servers, you might as well go for a virtual server set up ;)

have a look at xen, would be a nice start ;)

---

### Post by az on 2007-10-17
You need to install a web application onto your server

[https://help.ubuntu.com/community/Servers?action=show&redirect=Server#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4](https://help.ubuntu.com/community/Servers?action=show&redirect=Server#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4)
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by Druke on 2007-10-17
grab a good IDE (or just se vi as many would say) I prefer quanta plus, hear daptana is really good too!

think up random projects o give yourself w3schools has alot of really good tutorials

---

### Post by poisonmushroom on 2007-10-17
Thank you for the replies, since i do not know what Xen and the other complicated things are, i will check the link AZ gave since they look they can be understandable by a beginner.

I think il try hosting a website, or maybe use it as an FTP server! :)

---

### Post by reckless2k2 on 2007-10-17
well if you did the LAMP install depending on your sources you will not have an ftp server running. i suggest vsftpd install via the command line:

sudo apt-get install vsftpd

and you will have to read up on how to make it work. the initial setup is pretty simple. there are vsftpd how tos in this forum. 

as far as apache, it's already running. you just have to put content in /var/www and restart the server and you'll have a website. domain names and dynamic DNS is another issue that you will have to address rather quickly. 

can you code html as well? you'll need to know how to do that good stuff. my stuff is written in simple html. not that flashy but i assume you don't have macromedia and such to spice up things. haha. 

if this is all a foreign language to you. go to the store and buy a book. that's the best way to learn and get your hands dirty. hahaha

---

### Post by poisonmushroom on 2007-10-17
If putting the website files in /var/www is what i have to do to make it work then it's not a problem, as for the HTML question well i do have basic knowledge about HTML, nothing deep (I dont know ANY computer languages except basic batch scripting lol) But i think i can make a good layout for my site with Photoshop :)

As for FTP, you say it can't work. Isn't it possible to create a new user and install some FTP application there or is it 100% impossible?

@p_quarles: It took me quite a while to find that tutorial, when i find it again i will post it there. I have to say, it was short and easy, simple for beginners, just like me! :D

---

### Post by SeanTater on 2007-10-17
LAMP is only the beginning!
If you want to tearn the format of the web, a web page, learn HTML. I've used mozilla's developer center wiki and I find it's the most helpful.
PHP is a good dynamic language to learn if you want a more interactive website. Python is a very good choice too as it's more flexible and can be used outside of web scripting. Perl is a good choice if your name is "3 of 5" (borg) and you want a really fast program.

Meanwhile, don't forget, Linux is the world of choice! For example, I use:
LLPP == "Linux Lighttpd Postgres Python"  PostgreSQL is a database alternative to mysql and Lighttpd is a web server alternative to Apache. There are not quite so many tutorials for these setups so you might find it more challenging.

I used Pylons (A Python Web Application Framework) for a few months and with all it's intricacies, I found learning it quite enjoyable..

---

### Post by poisonmushroom on 2007-10-17
Well i can always design a simple website using only HTML links and photoshop layout with some random addons i find on the net then upload them :D but i guess with programming knowledge i can build a more complex website, i might have to start studying python.

P.S: Is it possible to create a new user, and beside hosting a site also host things like an FTP server, or Game server or maybe even a Ventrilo server? or is it only one purpose for one box?

Thanks again, i'm starting to understand slowly :) I will look for a good python book in the library when i get my pay and i will also try to memorize the bash commands and such.

---

### Post by reckless2k2 on 2007-10-25
i run a web, wordpress, music, mail, ftp, and samba all on one box. it's not really suggested to do this unless you have some high specs and low usage. i fall into the high spec low usage on my server and i don't run X either. i try to limit the resources so as much memory as possible can go to server functions. 

vsftpd is very simple to install and use on ubuntu. you can edit the one file that will allow only certain users to access if that's your choice. the ftp options are so limitless that it's hard to describe. i have logins that map to only certain locations in the directory tree. there are a lot of functions in all the servers that will surprise you.

---

