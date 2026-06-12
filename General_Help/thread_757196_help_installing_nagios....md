---
title: "help installing nagios..."
date: 2008-04-16
forum: General Help
---

### Post by Mia_tech on 2008-04-16
I've been trying to install nagios on my ubuntu box, but after compiling it, I do /etc/init.d/nagios start and I get error there's no such file.. any help appreciated

thanks

---

### Post by DarkWater on 2008-04-16
Look through the results of:
sudo find / -name nagios*

And see if it installed it somewhere else.  And do 'ls /etc/init.d' to see if maybe they put nagios(something here) as the filename.

---

### Post by Mia_tech on 2008-04-16
no there's nothing under /etc/init.d that relates to nagios

---

### Post by Mia_tech on 2008-04-16
this is the output of the ./configure command
*** Configuration summary for nagios 3.0 03-13-2008 ***:

 General Options:
 -------------------------
        Nagios executable:  nagios
        Nagios user/group:  nagios,nagios
       Command user/group:  nagios,nagcmd
            Embedded Perl:  no
             Event Broker:  yes
        Install ${prefix}:  /usr/local/nagios
                Lock file:  ${prefix}/var/nagios.lock
   Check result directory:  ${prefix}/var/spool/checkresults
           Init directory:  /etc/init.d
  Apache conf.d directory:  /etc/apache2/conf.d
             Mail program:  /bin/mail
                  Host OS:  linux-gnu

 Web Interface Options:
 ------------------------
                 HTML URL:  [http://localhost/nagios/](http://localhost/nagios/)
                  CGI URL:  [http://localhost/nagios/cgi-bin/](http://localhost/nagios/cgi-bin/)

---

### Post by Mia_tech on 2008-04-16
reinstlled again and worked... hate when I don't know what didn't work the first tiem :)

---

### Post by DarkWater on 2008-04-16
I wonder what the problem was, lol.

---

### Post by HermanAB on 2008-04-16
Glad you got it going.  You should also check out Zabbix.

Cheers,

Herman

---

### Post by Mia_tech on 2008-04-19
well I was able to install it, but after following the documentation and installing the client NSclient++ on the windows machine I get an error on the Service Details giving me a status of UNKNOWN and a status information of "Server port must be an integer" .... any help appreciated

thanks

---

