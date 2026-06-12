---
title: "Connecting to Ubuntu web server from XP"
date: 2007-05-18
forum: General Help
---

### Post by notamonopoly on 2007-05-18
I've been using Ubuntu for about a year now (drapper, edgy and now feisty) and absolutely love it. I have XP running under VMware for a few commercial applications and to be able to test out websites on Internet Explorer for compatibility.

I have the host (Ubuntu) and the guest (XP Pro) sharing files via Samba and I can also use the remote desktop without issue. What I've been struggling with is how to test out local websites (Apache on Ubuntu) from the guest XP machine. I thought it would be as simple as typing the IP address for the localhost but that does not seem to work.

So this might be painfully obvious, but I've never had to connect to a local site from another machine, I've always developed and tested on the same computer before uploading to a web host.

Any help would be appreciated,

Thanks

---

### Post by flowingfire on 2007-05-18
Somebody more experienced might contradict me, but I believe local websites (as far as their propagated IPs go) are inaccessable within one's own network.  

When I set one of my home computers up as a server, I was never able to access it from other computers in the house. I was always able to access it outside my own network, though.... So maybe proxies might help?  Using a different connection to test?

Of course, I'm just a n00b around here. lol.... I hope you CAN do what I don't think is possible.

Of course, if you're using Samba and want to view any old HTML file... well, share the HTML file and click it . . .

---

### Post by dfreer on 2007-05-18
My computer's on my LAN cannot access my web server by host name/domain name (due to a specific router issue), and of course you cannot access a web server from it's external IP address (due to the nature of TCP/IP). You should be able to access it from your internal IP address if you have apache set up correctly and there are no other programs using port 80 (or blocking port 80 if you installed a firewall). It may be as simple as telling /etc/apache2/ports.conf to listen to port 80.

EDIT: you need to type the actual network IP address, in case you were using the loopback IP address of 127.0.0.1 but if you have remote desktop and file sharing working, you shouldn't have a problem with this. it is most likely that your apache isn't configured right.

---

### Post by notamonopoly on 2007-05-18
I think that I am seconds away from solving this!

I used xampp to set everything up so there is no /etc/apache2 folder. I did a system wide search and the only "ports.conf" file I found was under /usr/share/ubuntu-docs/ubuntu/sample. It was set to "Listen 79". I changed it to 80. I don't know if that made a difference.

I checked the network settings and only found two IP addresses: 

127.0.0.1 - Localhost
127.0.1.1 - The Ubuntu desktop

So I did an ifconfig from the terminal:

eth0 - xxx.xxx.x.xxx
lo (local loopback) - 127.0.0.1
vmnet1 - 172.16.192.1
vmnet8 - 172.16.242.1

I went into XP and tried the vmnet1 (172.16.192.1) and sure enough, I got the default localhost site. "http://172.16.192.1/xampp/" from Ubuntu.

That's fantastic, now the only question is how do I access the virtual hosts that I set up in apache. I currently have multiple sites under htdocs in their own folder and have configured the virtual hosts file to allow me to type in site1.localhost, site2.localhost, etc. to access them. In XP now if I try "http://172.16.192.1/site1.localhost/" the page can not be found.

If I can get help with this last thing I will be one happy camper.

---

### Post by Cene on 2007-05-18
> **notamonopoly said:**
> I think that I am seconds away from solving this!

I used xampp to set everything up so there is no /etc/apache2 folder. I did a system wide search and the only "ports.conf" file I found was under /usr/share/ubuntu-docs/ubuntu/sample. It was set to "Listen 79". I changed it to 80. I don't know if that made a difference.

I checked the network settings and only found two IP addresses: 

127.0.0.1 - Localhost
127.0.1.1 - The Ubuntu desktop

So I did an ifconfig from the terminal:

eth0 - xxx.xxx.x.xxx
lo (local loopback) - 127.0.0.1
vmnet1 - 172.16.192.1
vmnet8 - 172.16.242.1

I went into XP and tried the vmnet1 (172.16.192.1) and sure enough, I got the default localhost site. "http://172.16.192.1/xampp/" from Ubuntu.

That's fantastic, now the only question is how do I access the virtual hosts that I set up in apache. I currently have multiple sites under htdocs in their own folder and have configured the virtual hosts file to allow me to type in site1.localhost, site2.localhost, etc. to access them. In XP now if I try "http://172.16.192.1/site1.localhost/" the page can not be found.

If I can get help with this last thing I will be one happy camper.

Dont keep my word as an absolote truth, but shouldn't you type in [http://site1.172.16.192.1/](http://site1.172.16.192.1/) ? AFAIK that is how the virtual hosts work; the identifier before ip or address (like [http://example.foo.com/](http://example.foo.com/) where example is the vhost).

(btw, how do you configure apache to use virtual hosts? :))

---

### Post by notamonopoly on 2007-05-18
I tried "http://site1.172.16.192.1/" but it didn't work.

To configure the virtual host I did the following:

1) Edit httpd.conf located "/opt/lampp/etc/" or wherever your apache files are.
2) Uncommented the include statement "Include etc/extra/httpd-vhosts.conf". Change the path to the file, you may have to create the file if it does not exist.
3) Edit the httpd-vhosts.conf file with the following:
------------------------------------------------------------------------------------------------------------------
NameVirtualHost *:80

# This is the default used when you enter "localhost" into the browser
<VirtualHost *:80>
    DocumentRoot /opt/lampp/htdocs
    ServerName localhost
</VirtualHost>

#These are the rest of the sites that you would normally access using "localhost/site1" etc.
<VirtualHost *:80>
    DocumentRoot /opt/lampp/htdocs/site1
    ServerName site1.localhost
</VirtualHost>

<VirtualHost *:80>
    DocumentRoot /opt/lampp/htdocs/site2
    ServerName site2.localhost
</VirtualHost>
------------------------------------------------------------------------------------------------------------------

Finally you have to edit the hosts file located "/etc".

------------------------------------------------------------------------------------------------------------------

# The first line (localhost) should already be there, just add the rest
127.0.0.1	localhost
127.0.0.1	site1.localhost
127.0.0.1	site2.localhost

# These lines were already there
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes


ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

------------------------------------------------------------------------------------------------------------------

Note that the naming convention for the vhost (site.localhost) does not matter, call it whatever you like, just make sure that it is the same in both the "httpd-vhosts.conf' and the "hosts" file.

Hope that helps

---

### Post by dfreer on 2007-05-18
So let me get this straight. Ubuntu is running Vmware with a virtual OS of windows XP. Ubuntu is also running apache webserver, and you are trying to test the web pages using IE on windows XP. You can reach the website from windows XP IE by typing [http://172.16.192.1/](http://172.16.192.1/) but you want to know how to reach the virtual hosts you have set up ([http://www.example.com](http://www.example.com)   [http://vhost.example.com](http://vhost.example.com)).

can't remember the file name in windows XP, but basically you can assign a domain name to an ip address (much like editing the /etc/hosts file in linux). In linux you would put the ip address on a new line, and then tab over and enter the name you would like to reach it from. Here's my /etc/hosts (remember I can't access my website from my LAN using domain name, so this is my fix):

```
127.0.0.1       localhost
127.0.1.1       danlaptop
10.1.YYY.XXX     www.dfreer.org torrentflux.dfreer.org packages.dfreer.org dfreer.org rowdy

# The following lines are desirable for IPv6 capable hosts

```

Note I have my virtual hosts all seperated by a space on the same line as the IP address. Anyways, there is a file in windows (lemme look up an old post and see if I can find it) that does the same thing although the syntax may be different.

EDIT: Here's that windows file
C:\windows\system32\drivers\etc\hosts
Didn't check it out but I was advised to use it by Mr. C on this thread:
[http://ubuntuforums.org/showthread.php?t=390461](http://ubuntuforums.org/showthread.php?t=390461)

---

### Post by notamonopoly on 2007-05-18
I took a look at the host file in XP and the only line is:

127.0.0.1       localhost

So I added the others, although I'm not sure that makes sense in this situation, and it made no difference.

---

### Post by dfreer on 2007-05-18
What I recommended doing was mapping the virtual host web site names to an specific IP address in windows. basically, if you can only access your example.com website by using the IP address [http://172.16.192.1](http://172.16.192.1) on the windows VM, you can map each virtual host name (site1.example.com, site2.example.com) to the IP address of [http://172.16.192.1](http://172.16.192.1), that way in your IE browser you can type [http://site1.example.com](http://site1.example.com) OR [http://site2.example.com](http://site2.example.com) and you will reach each site correctly.

However, without knowing how your virtual hosts are set up and more information about how your machines are setup, it's hard to help you further (was I correct in your machine layout in the first paragraph of my previous post?). We will need to know which version of apache you are running (you can grab the banner of a error page or execute this command: 
```
nc -v *your_site_name_or_ip_address_here* 80
```
Once it connects, type ***<cr>*** and hit the enter key.
You should see something like this:
```
$ nc -v 10.1.10.110 80
www.dfreer.org [10.1.10.110] 80 (www) open
<cr>
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>501 Method Not Implemented</title>
</head><body>
<h1>Method Not Implemented</h1>
<p>&lt;cr&gt; to /index.html not supported.<br />
</p>
<hr>
**_*<address>Apache Server at www.dfreer.org Port 80</address>*_**
</body></html>

```

This doesn't work on my server, but it should tell you your apache version number right there.

EDIT: Exactly what lines did you enter into C:\windows\system32\drivers\etc\hosts ? can you post this file please?

---

### Post by notamonopoly on 2007-05-18
BINGO!

I misunderstood what you were saying about the XP hosts file. I entered the sites the same way I did for Linux: 127.0.0.1 site1.localhost, etc. I did not use the working IP: 172.16.192.1

So I corrected it and now the XP Hosts file has:

172.16.192.1   localhost
172.16.192.1   site1.localhost
172.16.192.1   site2.localhost

This isn't the most ideal setup as I will have to remember to add these entries in any guest OS that I use but it's certainly working and that's the main thing.

To answer your two questions:

1) Server Info: "Apache/2.2.4 (Unix) DAV/2 mod_ssl/2.2.4 OpenSSL/0.9.8e PHP/5.2.1 mod_apreq2-20051231/2.5.7 mod_perl/2.0.2 Perl/v5.8.7 Server at localhost Port 80"

2) Yes, you were correct about the setup I have. I am running Ubuntu with XP in a virtual machine. I thought I mentioned that part, sorry.

Thank you dfreer (and everyone else) who took the time to respond. I worked in a Microsoft environment for years and getting help was like pulling teeth. The open source community is incredible.

By the way Cene, did you get the vhosts working? It really makes life easier, especially if you have paths in your server script using root references "/".

---

### Post by dfreer on 2007-05-18
This forum is really the reason why I use ubuntu :D The wealth of information around here is incredible. 

Yeah, you mentioned that part but I was a little unclear, but since you got it working it doesn't look like we need that info. If you ever put your server online, be sure to disable that banner display because it displays a LOT of information.

It isn't the most ideal setup, you are quite correct (I hate my router for making me do things this way). You may not need to do this, it all depends on whether your router will let you access the internal IP by it's domain name. Mine doesn't. You can see that thread I posted earlier as it as a lot more information about my particular problem, but in your case it will most likely work once you create a FQDN.

If it doesn't (or you want to keep your webserver on the LAN only) your other option is to create a DNS server in your LAN, and have your DHCP server point to it as the primary DNS server. When any clients using DHCP on your LAN lookup [http://site1.yourinternalsite.com](http://site1.yourinternalsite.com), it will check it's /etc/hosts file, see the IP address for that domain name, and it will point it to your web server.

P.S. btw, I don't remember how vmware networking works, but that windows hosts file looks like it could create a rift in the space/time continuum, 0_0 it's confusing as hell. but it works, eh?

---

### Post by swells5 on 2007-12-09
I know this thread is old but if you guys are still out there, I need a little more help with this problem.
I am same situation as first post.
Ubuntu gutsy host, vmware xp guest , bridged networking.
from the virtual machine, I can surf the internet. All my LAN computers show up in virtual xp network, I can ping everymachine from everyother machine.
But I cannot connect to Apache2 on the ubuntu host.
I have started developing web sites that are just the way I want them on firefox, but lousy in ie6. I just want xp ie6 on my development machine so I can learn how to make my css work for more browsers.
I have read your thread and can't find any others regarding this problem. You two are more advanced than I am with regard to networking.
I did not reinstall everything using xampp but I tried with apache2 default site both enabled and disabled. I have 2 virtual sites. I cannot get at them.
If you have a few minutes, could you please try to help me with this.
Thanks
Steve

---

### Post by dfreer on 2007-12-09
Ok, so from the vmware windows XP guest, did you try accessing your website using the webserver's LAN IP address, like [http://192.168.2.5](http://192.168.2.5) ?

If that works, you can edit the *C:\WINDOWS\system32\drivers\etc\hosts* file, enter the webserver's LAN IP address on the left, and then put the virtual hosts names on the right. 

So for example, let's say your Webserver has a LAN IP address of 192.168.2.5, and it has the virtual hosts names site1.mydomain.com and site2.mydomain.com. The new line in your vmware windows XP guest's hosts file would be:
```
192.168.2.5       site1.mydomain.com site2.mydomain.com
```

After you save that file, when you go to [http://site1.mydomain.com](http://site1.mydomain.com), you will hit the site1 virtual host on your webserver. Hope this helps!

---

### Post by swells5 on 2007-12-10
I went over the post again last evening and now with this added suggestion, I have it working. Thank you for the quick reply and the help
Steve

---

