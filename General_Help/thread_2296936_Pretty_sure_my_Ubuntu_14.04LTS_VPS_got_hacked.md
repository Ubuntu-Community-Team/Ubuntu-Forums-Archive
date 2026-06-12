---
title: "Pretty sure my Ubuntu 14.04LTS VPS got hacked"
date: 2015-09-29
forum: General Help
---

### Post by rob134 on 2015-09-29
A server of mine in Amsterdam got hacked. Just curious to find out how this happen... 
My setup:
- 2 active wordpress websites. The plugin/themes/CMS files were not outdated or insecure as far as I know. I pay close attention to updating those to avoid security risk.
- Enabled root access a month ago.
- Other than that very basic LAMP setup. PHP, mysql, apache.

What happen:
1. Starting 3 days ago I noticed website#1 could not be pinged from outside and website could not be accessed. If I pinged the URL from my local computer it returned a local IP address here in China. This was weird in my opinion but did not think any of it. DNS settings were all normal and working before.
2. Because that website could not be accessed I restarted the VPS. After I've done that all folders under /home/username were gone. Including website#2 that was working fine 5min before the reboot. Luckely I had website #1 stored in var/www/

My solution now:
- I'm installing a new VPS so will get a new IP.
- Import the 2 wordpress websites on the new VPS and update the plugin/theme files. Change login passwords for those websites.

Is there a way I can find out how this could happen? Also how to prevent this from happening on my newly installed VPS.

Thanks

---

### Post by CharlesA on 2015-09-30
If you already reinstalled the VPS, it is unlikely you'll be able to determine what happened.

As far as having a folder go missing after a reboot.. that is quite strange, but I don't know what would have caused it unless the home directory was being mounted from another disk and that disk had failed.

As far as the DNS issue goes, it sound like someone fudged with your domain settings in China which was why it was resolving to a local IP instead of the IP your VPS provider supplied.

Also: Please tell me you were using key-based authentication rather than passwords for logging in as root.

---

### Post by mastablasta on 2015-09-30
> **CharlesA said:**
> 
Also: Please tell me you were using key-based authentication rather than passwords for logging in as root.
...

and also tell us you used some security plugin on wordpress. something like wordfence or sucuri or both. + a very long and complex password and not "admin" user. 

my site is constantly under attack. got hacked once before as I updated the plugin 3 days too late. 3 days after a blog reported on vulnerability while patch wasn't out yet. 
after installing extra plugins it is better and only now I see how many efforts are made each day to guess the "admin" username and to try to login. I am still not sure how they manage to create a comment (though it is not seen on the website, comments are disabled and I can easily mark it as spam so it never get's shown to the users).

wordpress is attacked a lot. it's easy to use and popular platform.

after hack I also installed updraft backup that can backup to cloud or local disc. so now I have kind of proper backups made. it's still not as automated as I would want. but better than almost nothing I had before.

---

### Post by rob134 on 2015-09-30
> **CharlesA said:**
> If you already reinstalled the VPS, it is unlikely you'll be able to determine what happened.

As far as having a folder go missing after a reboot.. that is quite strange, but I don't know what would have caused it unless the home directory was being mounted from another disk and that disk had failed.

As far as the DNS issue goes, it sound like someone fudged with your domain settings in China which was why it was resolving to a local IP instead of the IP your VPS provider supplied.

Also: Please tell me you were using key-based authentication rather than passwords for logging in as root.

I still have the hacked VPS online. I installed a new VPS with new IP.
My guess the home/user directory got deleted because of some script that ordered it to after a reboot.... Who knows :)

Just password auth for root. Perhaps that's what might have happen... On my new VPS I already have 2000 brute force attacks on root. Installed fail2ban and set a long bantime. Although key-based auth might be a good idea.

DNS issue is still unresolved. When I ping it from my own computer it shows a local ip address (not my own though!). Pinging it from anywhere else gives a timeout most of the time. Although from who.is is pings an IP in Denver, US.

> **mastablasta said:**
> ...

and also tell us you used some security plugin on wordpress. something like wordfence or sucuri or both. + a very long and complex password and not "admin" user. 

my site is constantly under attack. got hacked once before as I updated the plugin 3 days too late. 3 days after a blog reported on vulnerability while patch wasn't out yet. 
after installing extra plugins it is better and only now I see how many efforts are made each day to guess the "admin" username and to try to login. I am still not sure how they manage to create a comment (though it is not seen on the website, comments are disabled and I can easily mark it as spam so it never get's shown to the users).

wordpress is attacked a lot. it's easy to use and popular platform.

after hack I also installed updraft backup that can backup to cloud or local disc. so now I have kind of proper backups made. it's still not as automated as I would want. but better than almost nothing I had before.
 Yes I do use Wordfence. I agree wordpress websites need daily backups!

---

### Post by CharlesA on 2015-09-30
> **rob134 said:**
> I still have the hacked VPS online. I installed a new VPS with new IP.
My guess the home/user directory got deleted because of some script that ordered it to after a reboot.... Who knows :)

Just password auth for root. Perhaps that's what might have happen... On my new VPS I already have 2000 brute force attacks on root. Installed fail2ban and set a long bantime. Although key-based auth might be a good idea.

DNS issue is still unresolved. When I ping it from my own computer it shows a local ip address (not my own though!). Pinging it from anywhere else gives a timeout most of the time. Although from who.is is pings an IP in Denver, US.

The best way to secure SSH is to disable root login and only login to a user who has access to su or sudo via key-based auth and switch to root as needed, rather than logging into root directly.

[http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security)

I would say your box was owned, but since you already reinstalled, it is unlikely you will be able to find out exactly how.
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

As far as the DNS issue goes, have you tried a different DNS server? What domain is working and which one is non-functional?

The only time I have heard of a VPS company issuring a new IP after a reinstall is when you are using someone like Digital Ocean and destroy the existing VPS and create a completely new one. That wouldn't solve your original issue, though since you would still get owned if you left ssh open with passwords only and no bruteforce protection.

---

### Post by rob134 on 2015-10-01
> **CharlesA said:**
> The best way to secure SSH is to disable root login and only login to a user who has access to su or sudo via key-based auth and switch to root as needed, rather than logging into root directly.

[http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security)

I would say your box was owned, but since you already reinstalled, it is unlikely you will be able to find out exactly how.
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

As far as the DNS issue goes, have you tried a different DNS server? What domain is working and which one is non-functional?

The only time I have heard of a VPS company issuring a new IP after a reinstall is when you are using someone like Digital Ocean and destroy the existing VPS and create a completely new one. That wouldn't solve your original issue, though since you would still get owned if you left ssh open with passwords only and no bruteforce protection.

Root is disabled from SSH login now. It came with the image install. I'm just logging in through the terminal at my hostings companies' web-based SSH terminal thingy.

I just checked login history of my hacked VPS and didn't see anything unusual there though. I still have my hacked VPS online. The new VPS I installed is a different box.

Thanks

---

### Post by CharlesA on 2015-10-01
Erm. As soon as you think your machine is hacked, you take it offline, and look through the logs to see how it was compromised, not leave it up and running.

See here:
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

