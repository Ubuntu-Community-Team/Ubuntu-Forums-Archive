---
title: "Squid User Details"
date: 2015-10-21
forum: General Help
---

### Post by Ullyndyss_Maloy on 2015-10-21
Good day all

I need some advice or assistance with my Squid Proxy server.

I am running Squid V3 on Ubuntu Server 14.04.1 

I have also installed webmin to manage and create squid users. Squid is also setup for Basic Authentication. 

I would like to know if there is a way that I can add descriptions to the squid users that I create for internet access?

Currently I am using the users employee number as his/her username and a random password.

I have three techs in different institutions that will log in via webmin to create internet users and would like to have descriptions added to the user so that I can see where these users reside.

Awaiting your positive responses :-)

Regards,

U Maloy

---

### Post by SeijiSensei on 2015-10-21
When you say they are going to log in with webmin, are they logging in as root? Logging in with their accounts that have sudo privileges?  Or can ordinary users create entries in the password file Squid uses for basic authentication?

The simplest solution is to give these three users more descriptive usernames rather than ID numbers.  However if they have regular Unix accounts with entries in /etc/passwd, you can use the comment field to add their information:

```
joe:x:1001:1001:Joe Admin from Chicago:/home/joe:/bin/bash
```

I think a better overall approach would be to create regular Unix users and have Squid authenticate with PAM: [http://linuxpoison.blogspot.com/2007/10/squid-password-authentication-using-pam.html](http://linuxpoison.blogspot.com/2007/10/squid-password-authentication-using-pam.html)

If you make the regular users default shell /bin/false rather than /bin/bash, they won't be able to log into the machine, but you can still authenticate them with PAM.  I use that technique on mail servers where I want to let users access their mailboxes but nothing else.  You might also want to create a separate group like "squidusers" and make that the default group for the users you create with this method.

---

