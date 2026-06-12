---
title: "Apache starting issue"
date: 2013-11-26
forum: General Help
---

### Post by thewillbowles on 2013-11-26
Hi all,

I am having a few issues getting Apache to start after installation. Everything resides in the /usr/local/apache2/ directory but when I try and start the apachectl service, nothing happens, I don't get any errors. Running netstat doesn't show anything on port 80. It's only when I try apachectl restart I get the message 'httpd not running, trying to start', but still nothing.

I followed the installation guidelines to the letter and had no issues compiling and installing Apache or OpenSSL from source but as to why I can't get it to start I don't know.

Any help would be greatly appreciated.

Thanks

Will

---

### Post by Lars Noodén on 2013-11-26
That sounds like the wrong directory.  Can you explain a little how you tried to install Apache?   If you did it correctly, you went via the Software Center, Synaptic or APT.  If you used another method, you may have to back up a step and uninstall it and try again using the repositories.  Also, if you did use another method, what problem are you trying to solve?

---

### Post by thewillbowles on 2013-11-26
Thanks for the reply.

I downloaded Apache Source from here - [http://httpd.apache.org/download.cgi](http://httpd.apache.org/download.cgi)

I extracted it to /opt/httpd-2.4.6/, ran through the configuration by running ./configure --prefix=/usr/local/apache2 --enable-ssl --with-ssl=/usr/local/ssl --with-include-apr --with-pcre=/usr/local/pcre. After that I ran make and make install which all went through fine and the directories were created in /usr/local/apache2.

I'm trying to start Apache by running /usr/local/apache2/bin/apachectl start. It doesn't work as my normal user or as root. The reason for using the source installation method is I'm trying to update a very old Apache integration guide I have to use the latest versions of Apache and OpenSSL on Ubuntu 12.04.

---

### Post by thewillbowles on 2013-11-28
I have pinpointed it down to the FQDN configuration but haven't managed to figure out exactly how to get that working properly.

---

