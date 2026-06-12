---
title: "The requested URL was not found on this server."
date: 2022-09-11
forum: General Help
---

### Post by iitywygms on 2022-09-11
Hi All.

I am running unbuntu 22.04 with mythtv installed.
I installed mythweb and can access it using my local ip address.  xxx.xxx.x.xxx/mythweb works as expected.

But when I try to access it outside my network i get        The requested URL was not found on this server.

I can access my server just fine.  [www.myservier.com](www.myservier.com) shows       Success! The your_domain virtual host is working!

I'm almost positive that it is something simple.  But honestly I have no idea where to look or even what information I should be providing to help figure this out.
Help?

---

### Post by #&amp;thj^% on 2022-09-11
It might be worth providing your **webhub.network.conf** file. That's the first place I would look.

---

### Post by iitywygms on 2022-09-11
I dont have a webhub.network.conf. ?

kevin@MP67:/etc/apache2/sites-available$ ls
000-default.conf  000-default-mythbuntu.conf  default-ssl.conf  mythweb.conf  springding.ddns.net.conf  springding.ddns.net.conf,kej

Should I look elsewhere for that file?

Or is this info useful?

  GNU nano 6.2                                                               000-default.conf                                                                         
<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName [www.example.com](www.example.com)

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

---

### Post by iitywygms on 2022-09-12
If someone could tell me what to post to provide more info I'll be happy to. Or maybe I should post this question elsewhere? Thanks

---

### Post by #&amp;thj^% on 2022-09-13
> **iitywygms said:**
>  Or maybe I should post this question elsewhere? Thanks

Lets see it took you one day to reply, and I have a job to do so time is a commodity to me. ;)
But anyway you will not be able to remotely access your MythTV machine until you open the port to your PC 
Have a look here: [https://www.mythtv.org/wiki/Restricting_Access_to_MythWeb:_Apache_Access_Controls](https://www.mythtv.org/wiki/Restricting_Access_to_MythWeb:_Apache_Access_Controls)

---

### Post by iitywygms on 2022-09-13
That was not directed toward you.  I was asking if there was possibly a more specifc forum I should post too other than here under general help.
Sorry you took it personally.

I can access my servier remotely.  If I go to [https://myserverdns.net](https://myserverdns.net), I get "Success! The your_domain virtual host is working!
If I go to [Https://myserverdns.net/mythweb](Https://myserverdns.net/mythweb) I get The requested URL was not found on this server.

If I am using my lan and got to xxx.xxx.x.x/mythweb, mythweb page opens and works as expected.

I just cant get mythweb to load when trying to access it outside my lan.
Thank you for the link on securing mythweb.  I have done so and it works as expected, when using lan.

---

### Post by #&amp;thj^% on 2022-09-13
No worries, I did not take it personal, just relaying my time now is short here in the forums.
The link I provided is the forums for Myth but just one more link to read or ask directly there: [https://forum.mythtv.org/viewtopic.php?f=36&t=3919](https://forum.mythtv.org/viewtopic.php?f=36&t=3919)

---

### Post by iitywygms on 2022-09-14
Finally got it fixed.  In case anyone sees this the fix for me was.
$ sudo ufw allow https
$ sudo a2enmod ssl
$ sudo a2enmod headers
$ sudo a2ensite default-ssl
$ sudo systemctl restart apache2

---

### Post by #&amp;thj^% on 2022-09-14
Nice, Good Job.
Thanks for posting your solution as well, it was just a myth away....LOL

---

