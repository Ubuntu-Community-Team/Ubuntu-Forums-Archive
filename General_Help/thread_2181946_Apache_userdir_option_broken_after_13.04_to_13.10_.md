---
title: "Apache userdir option broken after 13.04 to 13.10 upgrade"
date: 2013-10-19
forum: General Help
---

### Post by apollothethird on 2013-10-19
After upgrading from 13.04 to 13.10 my apache2 userdir links stopped working.  The error log shows:

```

[Sat Oct 19 14:44:02.296120 2013] [authz_core:error] [pid 1658] [client 50.75.184.39:54912] AH01630: client denied by server configuration: /home/users/l/j/ljames/public_html

```

I had something similar with my regular site and had to add the following option line:
(Require all granted)

```

<Directory /home/web/ubunzeus/www>
    Options +Indexes +FollowSymLinks +MultiViews +ExecCGI +Includes
    AllowOverride all
    Order allow,deny
    allow from all
    # New directive needed in Apache 2.4.3: 
    Require all granted
</Directory>

```

I can't figure out what I have to do for my userdir configuration to work.

By the way, I'd also like to know what the entries “authz_core:error” and “AH01630” in the error.log mean.

Thanks in advance for anyone who has insight on this.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by wind_racer on 2013-10-21
I'm having the same problem ... none of my custom <Directory> directives seem to be working. I guess I should have done more research about the 2.2 to 2.4 upgrade before proceeding.

---

### Post by wind_racer on 2013-10-21
Ah, I figured out my problem! 2.4 wants the config files to end in .conf so the sites-enabled list in apache2.conf shows *.conf and my server file didn't end in .conf. I renamed it and restarted apache and now all my user sites are working properly.

---

### Post by boxrec on 2013-10-26
ignore post, fixed now :-)

---

### Post by apollothethird on 2013-10-26
> **boxrec said:**
> I'm also having this problem, would you mind explaining the solution in more detail please

This is an email that I got from one of our users:

  [quote=PabloArias-EmailMessage]
>
> Hello L. D. James:
>
> I think you can solve the problem of your post in Ubuntuforums.org ([http://ubuntuforums.org/showthread.php?t=2181946](http://ubuntuforums.org/showthread.php?t=2181946)) removing the following 2 lines from your Apache site configuration:
>
> Order allow,deny
> allow from all
>
> Apache documentation:
> [http://httpd.apache.org/docs/2.4/upgrading.html#access](http://httpd.apache.org/docs/2.4/upgrading.html#access)
>
> I've read it here:
> [http://stackoverflow.com/questions/19445686/ubuntu-server-apache-2-4-6-client-denied-by-server-configuration-php-fpm](http://stackoverflow.com/questions/19445686/ubuntu-server-apache-2-4-6-client-denied-by-server-configuration-php-fpm)
>
> If you want, please, publish it in the forum. I can't do it because my login account does not work.
>
> Thank you and best regards
>
> -- 
> Pablo Arias
> [www.PabloArias.eu]("http://www.PabloArias.eu")
> Telf: ###-###-####

Thanks, Arias for being so concerned to help the Ubuntu users.  I really wish the developers of the best OS version would use their expertise to fix the broken website.  I highly recommend Ubuntu to all my friends and clients, but I'm embarrassed that the website hard to use after the introduction of the "SSO" replacement over the easy to use (and secure) login features built into vBulletin.

([ http://ubuntuforums.org/showthread.php?t=2165623&page=8&p=12768680#post12768680]("http://ubuntuforums.org/showthread.php?t=2165623&page=8&p=12768680#post12768680") )

While the support mechanism suffers because of the cumbersome login procedure (lack of the remember-me option) I'm glad we have a lot of die-hards (such as you and me) go through the loops needed to give support in spite of the inherent web access problem.

I'll post my reply to your message in the forums.  I'll include your full message minus your phone number.  I'm sure you don't mind the inclusion of your website address.
 [/quote]

If you continue to have problems after replacing:

Change from:
```

# Apache version 2.2 configuration:
Order allow,deny
Allow from all

```

Change to:
```

# Apacheversion 2.4 configuration:
Require all granted

```

Post your error log and I'll see what else is giving you problems.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/@ljames]("http://www.apollo3.com/@ljames")

---

