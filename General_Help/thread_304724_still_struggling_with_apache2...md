---
title: "still struggling with apache2.."
date: 2006-11-22
forum: General Help
---

### Post by a.d.gardiner on 2006-11-22
hi guys,

im struggling to get apache2 up and running on xubuntu.I've been looking around the forum and manuals/related sites but pulling all of the info together is still kinda confusing me.

I have apache 2 installed with 'sudo apt-get install apache2' on xubuntu 6.06. It is installed in /etc/apache2/ and by default points to /var/www/apache-2/. When i type localhost into firefox i get taken to a view of folder /var//www/apache2-/, but it doesn't load the default apache page. (One assumes this might have to be configured to check the server is functional).

I know I have to edit the httpd.conf file to point the server at the location of the files I want to host on my machine. I want them at /home/shop/chevincal/ so I set about this and now my config looks like this:

```

Listen "192.168.0.2:80"
DocumentRoot “Alias /shop/ /home/shop/chevincal/”
ServerRoot "/etc/apache-2/"
Timeout 300
ServerAdmin info@chevincycles.com
ScriptAlias “ScriptAlias /cgi-bin/ /home/shop/chevincal/cgi-bin/”
HostnameLookups off
ErrorLog “Alias /shop/ /home/shop/chevincal/errorlog/”

```

I have no doubt that its wrong or the syntax is incorrect or something, but I'm stuck.

Furthermore I came to the conclusion that to make apache host files on my local network at 192.168.0.39 I would have to put the system at that address. I modified my network interface.conf file to look like this, but when I restarted the machine can no longer find the internet as it did before.

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.39
        netmask 255.255.255.0
        gateway 192.168.0.1

```

Overall what im trying to acheive is to host a simple site with apache on the office network at work. The site won't be accessible from the outside world.

any ideas, much appreciated,

alex ](*,)

---

### Post by Average Joe on 2006-11-22
I configured my apache 2 server like [this]("http://www.ubuntuforums.org/showthread.php?t=255464"). Although I only use it as localhost, maybe it can help you.

Also, I don't think the apache2 configuration file is httpd.conf. It is apache2.conf

---

### Post by a.d.gardiner on 2006-11-22
thanks, i'll go give that a blast now.

---

### Post by a.d.gardiner on 2006-11-24
got everything sorted now.. your article was dead useful! cheers :)

---

