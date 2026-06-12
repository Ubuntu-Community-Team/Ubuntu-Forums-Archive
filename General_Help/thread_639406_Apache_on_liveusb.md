---
title: "Apache on liveusb"
date: 2007-12-13
forum: General Help
---

### Post by fennec62 on 2007-12-13
Hi

i make a usb live with ubuntu 7.10 in persistent mode

all is ok 

But i want to work with local web server 

i install all package apache2 

But when i load server localhost, i have no image 

nothing image is display just link 

error.log give that 

[Thu Dec 13 04:44:29 2007] [info] [client 127.0.0.1] (22)Invalid argument: core_output_filter: writing data to the network

this error just on [http://localhost](http://localhost) with a adress on web image is display 

Can you help me

thanks

---

### Post by d0nny2600 on 2007-12-13
Have you tried restarting apache?

---

### Post by fennec62 on 2007-12-13
nothing to do

image on localhost never display

---

### Post by d0nny2600 on 2007-12-13
Restart the server:
sudo /etc/init.d/apache2 restart

Then try opening the browser to localhost.

Out of interest is it a LAMP configuration you are going for?

---

### Post by fennec62 on 2007-12-13
i try but nothing

lamp configuration is the original

nothing change

---

### Post by Lostincyberspace on 2007-12-13
Try pinging 127.0.0.1 then putting that in the address bar.

---

### Post by nofix on 2007-12-18
hi !

I just had the same problem and and i found a soluce. There is due to non standard filesystem like squashfs for example.
Just add the directive "EnableSendfile Off" in your httpd.conf


[http://httpd.apache.org/docs/2.0/faq/error.html#error.sendfile](http://httpd.apache.org/docs/2.0/faq/error.html#error.sendfile)
[http://httpd.apache.org/docs/2.0/mod/core.html#enablesendfile](http://httpd.apache.org/docs/2.0/mod/core.html#enablesendfile)

---

### Post by fennec62 on 2007-12-30
very thanks it's ok

---

### Post by periphery on 2008-04-14
> **nofix said:**
> hi !

I just had the same problem and and i found a soluce. There is due to non standard filesystem like squashfs for example.
Just add the directive "EnableSendfile Off" in your httpd.conf


[http://httpd.apache.org/docs/2.0/faq/error.html#error.sendfile](http://httpd.apache.org/docs/2.0/faq/error.html#error.sendfile)
[http://httpd.apache.org/docs/2.0/mod/core.html#enablesendfile](http://httpd.apache.org/docs/2.0/mod/core.html#enablesendfile)

Thanks for that, fix. After installing PHP, MySQL and Apache on my new ASUS eeePC, this problem popped up and was drinving me up the wall.:mad:

---

