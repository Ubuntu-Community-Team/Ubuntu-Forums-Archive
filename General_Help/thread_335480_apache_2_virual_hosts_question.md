---
title: "apache 2 virual hosts question"
date: 2007-01-10
forum: General Help
---

### Post by a.d.gardiner on 2007-01-10
hey all,

I have a quick one about apache 2.

I run phpBB on my machine inside my works network. We port forward our boardbands static IP 81.149.11.11 to our servers internal IP 192.168.1.1

I just registered an FQDN with lycos, but Im unsure what to edit to get apache plugged into it.

I read in the manual that i need to configure my virtual hosts similar to below but don't want to make changes until I know if im going along the right lines? incidentally Im not entierly sure which files to edit?

```

    <VirtualHost *>
    ServerName www.chevinportal.co.uk
    DocumentRoot var/www/chevinportal
    </VirtualHost>

```

any ideas?

---

### Post by Johnsie on 2007-01-10
I'm using this. Caters for www. and other ways of accessingL
> <VirtualHost *:80>
ServerName [www.whatever.com](www.whatever.com)
ServerAlias whatevercom *.whatever.com
DocumentRoot /path/to/htdocs/for/this/site
</VirtualHost>


You also have to make sure the dns for your domain knows to point to your ip (dns and 'url forwarding' are not the same thing). I use dnsexit.com or zoneedit.com for my domains.

---

### Post by a.d.gardiner on 2007-01-10
cheers for the info :)

thing is where do i put that information? is it in httpd.conf or in sites-available?

I have setup lycos to forward the registered domain to my static IP, but don't know anything about configuring my dns? ](*,)

---

### Post by Johnsie on 2007-01-10
I use httpd.conf but I'm pretty sure there are other ways of doing it. You also need to restart apache when you make changes to this file. 

The main difference between dns and url forwarding is:

-Url forwarding uses a frame or a javascript to direct the visitors browser your ip address. This only works in web browsers. 
webbrowser---->your ip

-Dns works for any request made to the domain no matter which port is used.
any request made to your domain(smtp, ftp, browser etc)---->your ip

---

### Post by Johnsie on 2007-01-10
btw... there's a server specific forum on this site where you might be able to get more help. To be honest it's a little slower than this forum though. If you're running a server you really should look into assigning a dns for your domains though. It is really useful when it comes to setting things up on your domains/server.

---

### Post by pete on 2007-01-10
a.d. gardiner, if you're using the version of Apache in the repos...

You create a new file in sites-available w/the settings for the vhost, and then run "sudo a2ensite" in Terminal to bring up the vhost.

---

### Post by a.d.gardiner on 2007-01-10
Cool, so DNS is something I have to install on my apache machine, or something I have to configure at lycos? (I really wish I knew what I was on about lol)

Either way my apache is listening on 80. and only serves a phpBB so forwarding should do everything needed (i think).

Just looking my apache has got an empty httpd.conf.

In sites-available i have a file called 000-deafult and also in sites-enabled a file called default. both have the same contents (which is similar to the code above but has some other lines too).

will post them in a min.

:)

---

### Post by Johnsie on 2007-01-10
You dont really need dns if your're just using a web server, it's really only useful if you're using the server for more than one task (smtp,ftp,vnc,etc.) or domain. 


If you do want to use dns it's better to set up dns  here's how you would do that:
1. Sign up for an account on zonedit.com
2. Add your domain name to your account on zoneedit
3. In lycos change your nameserver to the one zonedit provided you with.

---

### Post by a.d.gardiner on 2007-01-10
awesome guys, help very much appreciated! everything looks to be working nicely now :)

---

