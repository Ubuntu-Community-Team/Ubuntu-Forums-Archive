---
title: "Where would I find good set-by-step for my own personal server setup"
date: 2019-11-23
forum: General Help
---

### Post by dohm11 on 2019-11-23
Hi all,
                So as a previous post, I am new to Linux, using Ubuntu 18.04 (Desktop) which I like to view files and folders. 

My current setup is I have my OpenSSH and VSvsftpd, which I use PuTTy to access my terminal for quick access and use FileZilla to upload my files on my “server computer”. I can then go online using my IP or web name which I got from NoIP. I am looking to add some more component but now all my try-out came null. So I have the Ubuntu web page from local Ip and can do some html coding, that’s ok, but was looking to implement WordPress so that I could create a personal website. 

Is there a step by step where I could learn how to properly make this happened? 

I have been following Digital Ocean’s step by step guide but there seem to never connect to anything. I do check if I can access my html page from an outside connection other than my local access and yes it does work. 
Just looking for tip and tricks and guides. 

My end results would be to have my own hosting server and a WordPress site run from my own personal home and not from an external company which to be franc was running me way too high in price and the amount of space, well I got the space right here at home.

Thank you,

P.S.: Just looking for guides and instructions, not for someone to do it for me as what is the point if I am not learning what I'm doing, even to run troubleshoots. 

Dohm

---

### Post by gnusci on 2019-11-23
Are you looking for how to setup a web server?

[https://howtoubuntu.org/how-to-install-lamp-on-ubuntu](https://howtoubuntu.org/how-to-install-lamp-on-ubuntu)

---

### Post by HermanAB on 2019-11-24
Well, you cannot just dive in and install complicated services and think it will magically work if the underlying network is not configured right...

First decide how you are going to manage the IP address and domain name and get it to resolve using DHCP and DNS and only THEN worry about the services on top of that.

---

### Post by TheFu on 2019-11-24
Digital Ocean guides often assume you are on their infrastructure.  If you aren't, then the setup stuff outside the VPS needs to be handled and most of that isn't an Ubuntu question. It is more about networking, routers, firewalls, DNS, and domain registration.  Each of those things are separate.  Which have you already addressed?

I tend to write *why* blog articles, not "*what to type*" articles.  *Why* a service is needed, not how to set it up. 
[https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) is intended to provide some background.

Securing a wordpress website is non-trivial.  There are 2M hacked wordpress websites on the internet today. Because people set them up and ignore it.  Wordpress is like MS-Windows.  Attacks against MS-Windows happen because 90% of the desktops in the world run Windows and average users don't properly security their PCs.  Attacks against Wordpress happen because it is the most popular blogging platform and average wordpress admins don't properly patch, secure, firewall, their wordpress sites.  The problems with wordpress being hacked are so great that an entire subculture of wordpress security services exists.

OTOH, I run a non-WordPress blog on a very unpopular blog engine and have never been hacked in 15 yrs.  In no way do I think the blog I run is perfectly secure.  It just isn't a priority target.  Plus, if anything did happen, there are 90 days of versioned backups which can be restored. Very little chance of data loss.  
Tip: Setup backups on a system that you know can be restored before putting anything on the internet.

---

### Post by dohm11 on 2019-11-25
To TheFu: Yes, Routers, firewall, dns (which already set up and can use IP addr and domain name which already have from NoIP. I don't mind the 30 days refresh as I am always here working on stuff) 

The IP/Domain name is working fine... Tested the PHP info file and everything works as it would normal intend to work. I also have VSvsftpd set up so I can upload files from computer to computer and test it on local browser and outside browser to troubleshoot and see if everything is ok. I mean only using the IP addr is all good for now but the Domain name is working pretty good and not to shabby doing html pages. 

I used to be with Hostpapa and using wordpress was a delight, usually just for plain stuff so being hacked never been a problem has I always have multiple place I save everything. 2 6T on this putter so all good. The problem is with a hosting provider the amount of space was never enough for the files I would have to upload. With having full control, I am more than happy. Just trying to seek information and learn as I go along.

I already have LAMP set up and configured to point to PHP over HTML. 

Will check and read on your blog. 

Thank you all :)

---

### Post by SeijiSensei on 2019-11-25
Most times, the default permissions for WordPress allow the web server pseudo-user, "www-data" on Ubuntu, to write into the WP directories. This allows automatic updates, but to me it poses a security issue. I prefer to remove those permissions and enable them only when I need to update WP which I do manually. For details, see [https://ubuntuforums.org/showthread.php?t=2430231&p=13902583&viewfull=1#post13902583](https://ubuntuforums.org/showthread.php?t=2430231&p=13902583&viewfull=1#post13902583)

WordPress is updated pretty frequently, and most updates include some additional security fixes. It's important to stay current.

---

### Post by aljames2 on 2019-11-25
Not sure what your bandwidth needs are but consider if you might run in to issues with your ISP.  I run a Drupal website on a Drupal centric webhost.  I let them handle the security and such.  Never had issues.  Mine is more trivial though and I have tons of backups.

---

