---
title: "How to turn OFF Apache2 logging?"
date: 2016-02-07
forum: General Help
---

### Post by josh77 on 2016-02-07
Some guides reference a file called "/etc/apache2/conf.d/other-vhosts-access-log"which does not exist.

I cannot seems to find any instructions for disabling logging on 14.04,




If possible, it would be great to do it all in one place , thanks.

---

### Post by dragonfly41 on 2016-02-07
Surely the answer is found very easily by searching "disable apache logging"?

[http://superuser.com/questions/916726/disable-apache-logging-completely](http://superuser.com/questions/916726/disable-apache-logging-completely)

So you can turn off apache2 logging .. globally .. by editing  /etc/apache2/apache2.conf

comment out the ErrorLog line and replace with ..
ErrorLog /dev/null

Another thought.
Finer control over multiple virtualhost config files might be achieved by enabling the apache2  mod_macro module. 
Then you can control virtualhost configurations (including logging) through a macro definition for all virtualhosts.

---

### Post by haplorrhine on 2016-02-07
Could you edit the AppArmor profile?  Alas, it might log whenever the boundary is enforced.  Anyway, if I understand AppArmor exactly, which I don't.

ls -l /etc/apparmor.d/ | grep apache

The syntax (roughly)  [https://activedoc.opensuse.org/book/opensuse-security-guide/chapter-19-profile-components-and-syntax](https://activedoc.opensuse.org/book/opensuse-security-guide/chapter-19-profile-components-and-syntax)
Add something like

```
deny /var/log/[...]/** w
```

sudo apparmor_parser -r /etc/apparmor.d/[...]
sudo aa-enforce /etc/appparmor.d/[...]

---

### Post by josh77 on 2016-02-07
> 
Surely the answer is found very easily by searching "disable apache logging"?

Huh, I went back to check, and wouldn't know know it. I had followed the guide you linked years ago when first setting the server up, yet am still now swamped with log files.

ErrorLog /dev/null

Already set.

---

### Post by dragonfly41 on 2016-02-08
> If possible, it would be great to do it all in one place , thanks.

If you're managing a sizeable server with multiple virtualhosts
my suggestion is to install webmin (it is in Ubuntu Software Centre).
Latest information here ... [http://www.webmin.com/](http://www.webmin.com/)

On my localhost I'm looking at Webmin Dashboard > Servers > Apache Webserver
and all apache2 config files can be selected for editing .. in "one place" as you request.

Then you might go to Webmin Dashboard > System > Log File Rotation to set logging rules
such as maximum size of log files.

Or Webmin Dashboard > System > System Logs.
this includes > View > File /var/log/apache2/error.log


[Added note]

Webmin Dashboard > Webmin > Webmin Configuration > Logging
has these further options ...

enable/disable logging
periodically clear log files every n hours
specify users to log
specify modules to log
etc.

---

