---
title: "Apache HELP!"
date: 2007-02-20
forum: General Help
---

### Post by nick.inspiron6400 on 2007-02-20
Hi,

I have installed Apache and i also installed NVU. I tried to make a web page, and save it in /var/www. But i get a message:

CANNOT CREATE FILE. DIRECTORY /VAR/WWW/ IS NOT WRITEABLE.

What am i doing wrong?

I have a ton of other questions but this is my first! 

Thanks!

Nick,

---

### Post by cmertayak on 2007-02-20
Check the owner and permissions of the directory writing 

ls -l /var/www

If the owner is "root", you can either change the owner of the directory to yours or write it
with root priviladge.

(1st way) changing the ownership, assumed that you are the user "nick"

sudo chown -R nick:nick /var/www/
(this will change the owner of all files and directories in /var/www including itself)

(2nd way) you can directly copy your file with the root priviladge:

sudo mv tirt.php /var/www/

---

### Post by nick.inspiron6400 on 2007-02-20
Thanks! 

Now how do i upload these on to my web server and then view those files and pages on a different computer?

Nick,

UPDATE:

How do i view my pages from a different computer? I have a wireless router do i need to set that up?

---

### Post by cmertayak on 2007-02-20
Two ways are possible for it, too:).

(1) For the user "nick", in the home directory create a directory named "public_html". Make
its permissions as readable for "others". Put the content of your web page there.
Let's assume that your IP is x.y.z.t, then ...

"http://x.y.z.t/~nick/index.html" should be visible to other machines connected to the net.

(2) If you are the admin of the system you can modify the content of "/var/www". You can
upload your files there with the appropriate permissions. Also you can modify the directory
entry in the configuration file that apache uses as default (in order to use another directory 
instead of  "/var/www"). It should be /etc/apache2/apache2.conf, but I am not sure:(

---

### Post by punx45 on 2007-02-20
actually, i believe the DocumentRoot setting for each host under apache 2 is set in /etc/apache2/sites-available/*hostname* the default is named default.  but yes, the default DocumentRoot is /var/www.   this directory is created by root, so either 'sudo' everything you do in there, or for a more convenient (but possibly risky) solution, 'chown' /var/www to your user.

apache2 changed alot of things from apache 1.3. all the host configuration is geared towards virtual hosts.

if you have just installed apache, there are a few configuration steps left still before your site will be publicly visible.   i would strongly encourage the documentation found at [http://httpd.apache.org](http://httpd.apache.org)  and make sure you read the right docs for your version.   if you used  aptitude and installed 'apache' you probably have version 1.3 whereas if you installed 'apache2' you have 2.x, and as I said before, the configurations are very different.

> How do i view my pages from a different computer? I have a wireless router do i need to set that up?

if you are on a residential ISP you probably have a dynamic IP, so you will need to set up a dynamic DNS hostname.  there are quite a few providers of this so search around.   then, since you say you have a router, set the router to forward port 80 to the computer on your LAN that has the apache server running on it.  give that machine a static IP if you haven't already.   make sure your server config files refer to the domain name that you set up  with the dynamic DNS service.

thats the nutshell version.

finally, if you have Verizon DSL, or one of many other ISPs, all your efforts to make a HTTP server public will be thwarted, (the rest tell you not to but let you do it anyway) so either don't bother, or settle for a server that only functions on your LAN. :(

---

### Post by nick.inspiron6400 on 2007-02-21
Thanks for all your replies!

I have tried all your methods and have come up with my own!!!

i go to [http://myipaddress](http://myipaddress)

Then i get a list of files in my /var/www folder.

Is this a good idea?

Nick,

---

### Post by punx45 on 2007-02-21
if it is on your LAN that is fine.   but if you are trying to access it away from home you might find that the IP will change eventually, which is why a domain name set with a dynamic DNS host is helpful.

and, for inside your LAN, you can change the hosts files on all the computers to point to your server with a name rather than the IP.   you will find the hosts files on ubuntu/Mac OS x, other *nixes in /etc/hosts.   in windows i forget where it is, but i think it is called hosts or similar.

---

