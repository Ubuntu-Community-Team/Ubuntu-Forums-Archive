---
title: "how do i get a cgi-bin?"
date: 2007-04-28
forum: General Help
---

### Post by heyo on 2007-04-28
Hi, I'm trying to setup a local webserver on my old PC using Ubuntu Server Edition 6.06.

Got everything working apart from the cgi-bin directory doesn't execute my .pl scripts? It simply prompts the download box.

Also phpinfo() doesn't show a CGI section either. Is this what I have to install? Or do I have to install PHP as a CGI? 

I've been searching everywhere on the net and can't find answers. Waaahhh :( 

Thx
Louis

---

### Post by UbuntuniX on 2007-04-28
Are you sure Perl is correctly configured?

Also, I assume you're using Apache?
If so, have you installed the Perl modules?

---

### Post by heyo on 2007-04-28
wow thx for the quick reply.. 

Yup im using Apache and I think perl is installed already. It's there in my Synaptic Manager.
I'm not sure if it's configured correctly though.. I'll go find some guides to follow through and  report back here

---

### Post by heyo on 2007-04-28
ok I'm stuck.

How do i check perl is installed and configured properly?

Do I need mod_perl installed? Because thats another wrist slitting headache as I'm missing apache apxs.

On my Synaptic Manager, it does say that perl is installed. And I've set on my WebMin>Apache WebServer>CGI Programs>CGI directory aliases:
From: /cgi-bin/
To:/usr/lib/cgi-bin/

Still my cgi-bin does not execute .pl files! It gives me the prompt download. 

I think I'm gona sit and cry for while...

---

### Post by fragos on 2007-04-28
Just covering the bases, is the first line of your Perl script "#!/usr/bin/perl" and is permissions for the script set to execute.  Also you havn't told us if you have apache or apache2.  There are configuration differences between them.

---

### Post by x1a4 on 2007-04-28
Hi,

Everything you need to know about Apache is in the manual.  Just point your favourite browser to [http://localhost/manual/](http://localhost/manual/)

---

### Post by outofnicks on 2007-04-29
You might need to edit /etc/apache/httpd.conf to enable ExecCGI in the options. (or the apache2 directory if applicable). It's the last line in this code block:
```
 #
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#

#
# This should be changed to whatever you set DocumentRoot to.
#
<Directory /var/www/>

#
# This may also be "None", "All", or any combination of "Indexes",
# "Includes", "FollowSymLinks", "ExecCGI", or "MultiViews".
#
# Note that "MultiViews" must be named *explicitly* --- "Options All"
# doesn't give it to you.
#
    Options Indexes Includes ExecCGI FollowSymLinks MultiViews
```

Just make sure the word "ExecCGI" is included in that last line, which is on line 316 in my httpd.conf (running Dapper, same as you).

Then you  have to restart Apache each time you edit this file.I forgot what the terminal command is for that, but I just go to the System>Services menu and turn it off then back on.

---

