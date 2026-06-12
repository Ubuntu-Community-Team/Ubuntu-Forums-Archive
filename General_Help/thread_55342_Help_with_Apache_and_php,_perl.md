---
title: "Help with Apache and php, perl"
date: 2005-08-08
forum: General Help
---

### Post by dieselpower on 2005-08-08
I have just installed ubuntu on my desktop, and converted it to kubuntu. I love it, it's FAST! I am going to do it to 5 more pc's, so I wanted apt-cacher, so I installed apache2, apt-cacher and the php-mod or whatever and could not get it to work. No problem, I uninstalled it all and used apache 1.3.33 because apt-cacher ran perfectly fine using that on my old debian box. Well, it still did not work, and now I'm back with apache2. When I try to access http//:192.168.0.2/apt-cacher firefox asks me what to do with apt-cacher.pl? I yelled at it, and told it to send it back to the sever because it had no bussiness trying to do anything with a perl script! So how do I make apache proccess it BEFORE it sends it to the browser? From my googling it seems to be a ubuntu specific problem, but nobody has the answer.

Here's someone else with the same problem, only I'm not as smart as him!
[http://wordpress.org/support/topic/30366](http://wordpress.org/support/topic/30366) 

Sorry for my humor!!!

Lawrence Shafer

BTW, been using linux for 4 years now so I can understand a little more than a n00b!

---

### Post by Dragonmantank on 2005-08-08
Is Perl installed? And if it is, is Apache set up to use it as a module? For example, with PHP you need to install and load it as an Apache module, otherwise Apache assumes you want to download it or display it in the browser, not actually parse it.

You'll also want to make sure that the .pl files have execute permissions.

---

### Post by dieselpower on 2005-08-09
OK, the scripts are all owned by root and the permissions are 755. So that should be OK? And here is my php test page,  [http://www.lbs.frihost.net/php.html](http://www.lbs.frihost.net/php.html). I uploaded it to my server, Does that tell you anything? The scripts are located in /usr/share/apt-cacher and there is a file in /etc/apt-cacher that apache loads on restart. here is the contents.


/etc/apt-cacher/apache.conf
-----------------------------------------------------------------------------------------
Alias /apt-cacher /usr/share/apt-cacher/apt-cacher.pl

<DirectoryMatch /usr/share/apt-cacher/>
	Options Indexes FollowSymLinks
	Options ExecCGI
	AddHandler cgi-script .pl
	AllowOverride All
	order allow,deny
	allow from all
</DirectoryMatch>
-----------------------------------------------------------------------------------------

I just can't figure this out? Any ideas?

Lawrence Shafer

---

### Post by dieselpower on 2005-08-10
[QUOTE=dieselpower]OK, the scripts are all owned by root and the permissions are 755. So that should be OK? And here is my php test page,  [http://www.lbs.frihost.net/php.html](http://www.lbs.frihost.net/php.html). I uploaded it to my server, Does that tell you anything? The scripts are located in /usr/share/apt-cacher and there is a file in /etc/apt-cacher that apache loads on restart. here is the contents.


/etc/apt-cacher/apache.conf
-----------------------------------------------------------------------------------------
Alias /apt-cacher /usr/share/apt-cacher/apt-cacher.pl

<DirectoryMatch /usr/share/apt-cacher/>
	Options Indexes FollowSymLinks
	Options ExecCGI
	AddHandler cgi-script .pl
	AllowOverride All
	order allow,deny
	allow from all
</DirectoryMatch>
-----------------------------------------------------------------------------------------

I just can't figure this out? Any ideas?

Lawrence Shafer[/QUOTE]
 Someone please help, I got apt-proxy to work but I don't like it. I really want to figure this out. I installed the debian version of apache 3.3.33 and apt cacher worked fine. but I really messed up some libs, and broke a lot of packages. So I reinstalled and want to learn how to make my little apache indian be my good slave!

---

### Post by dieselpower on 2005-08-19
Update, [http://localhost/apt-cacher](http://localhost/apt-cacher) works. but [http://192.168.0.2/apt-cacher](http://192.168.0.2/apt-cacher) still asks me to download a *.pl file. What would happen if i put a true debian /etc/apache2/apache2.conf file on this machine? And is anyone willing to email me one to lawrence [at] pastimes.cc?

---

