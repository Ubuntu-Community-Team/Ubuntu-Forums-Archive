---
title: "[Easy] New LAMP install questions"
date: 2006-07-06
forum: General Help
---

### Post by Daiver on 2006-07-06
So, I decided to install LAMP by means of: sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server       

1) I see that /var/www/ contains the files that are going to be displayed by browsers, but where is public_html, etc?  All I see is apache2_default.  Did I do something wrong?

2) Can someone please link a n00b guide to securing apache, php, mysql, etc?

3) If there is a MUST for new LAMP installs, could you please share them?

Thanks =)

---

### Post by Maggot on 2006-07-06
/etc/apache2/apache2.conf has a a section for the public home folders in there. Just uncomment it.

---

### Post by Daiver on 2006-07-06
Thanks!

Also, I have another problem which is sort of LAMP related.  The machine that I'm testing this stuff on is remote and I have no access to the router except via Http.  I have port 80 on the router pointed to the router so I can access the firmware.  I have a conflict of interests now, since Apache also wants port 80 for obvious reasons.

Does anyone know how to set up everything so port 80 leads to the content of public_html and have the router's firmware available through a browser?

---

### Post by Daiver on 2006-07-06
Here's what I have now, but public_html hasn't been created in /var/www/

# UserDir is now a module
UserDir public_html
#UserDir disabled root

---

### Post by skirkpatrick on 2006-07-06
[QUOTE=Daiver]Here's what I have now, but public_html hasn't been created in /var/www/

# UserDir is now a module
UserDir public_html
#UserDir disabled root[/QUOTE]
You'll have to create that directory manually.  Use
**sudo mkdir /var/www/public_html**
then
**sudo chmod 755 /var/www/public_html**
or
**sudo chmod 777 /var/www/public_html**
so that anybody has read/write permission to that folder to make modifying the files easier.

---

### Post by Daiver on 2006-07-06
Thanks for the quick reply!  Already done :)

If anyone knows something about the router issue, please post since I'm also stuck there :/

---

### Post by Daiver on 2006-07-06
So, I've successfully managed to lock myself out of the router.  =(

The good news is that Apache works! :D

---

### Post by skirkpatrick on 2006-07-07
But doesn't your router and your Apache server have different IP's?  Or is your router catching all port 80 requests?  You might be able to set your router up to use a different port (like 8080) for its webpage.

---

### Post by Daiver on 2006-07-07
And how would I instruct Firefox to access it? [www.domain.com:8080?](www.domain.com:8080?)  Because I tried port 5555 for the router and did [www.domain.com:5555](www.domain.com:5555) and it didn't load.

Apparently, if I assign port 80 to Apache, then the router does it's job and redirects all traffic to 192.168.10.4, which is where Apache is.  Then, Apache gets the request and displays the page.

My Apache server is behind the router.

---

### Post by Daiver on 2006-07-07
Apparently, this US Robotics router is quite kick-*** and I didn't even know it.  It has a function called "Remote management" where I can enable port 8080 to access the firmware and leave port 80 to Apache.

Previously, as I said, I tried to use something like port 5555 but it didn't work.

Now it does and I'm all set.  Thanks for the help!

Edit: Actually, the remote management port also works with 5555, but only if I click the number.  The firmware is tricky, but it does seem to work amazingly.

---

### Post by skirkpatrick on 2006-07-07
Sounds good!  Not all routers will allow you to change the port they listen to.

---

