---
title: "Hardy Heron 403 forbidden error with python cgi and error with mod_python"
date: 2008-04-25
forum: General Help
---

### Post by oliwynn on 2008-04-25
Hi,

I installed the new version of ubuntu, hardy heron yesterday and now my python cgi scripts and mod_python psp pages running on an apache2 server don't work.  I have checked all the permissions so that anyone can read them and that they are executable and changed the owners of the files to my username, but it still won't work.  I've asked a few others who are comfortable with ubuntu and they don't have any solutions as their upgrade did not affect any of this.  I desperately need a solution soon as I need it for work.  

Any ideas?

Thanks in advance

O

---

### Post by oliwynn on 2008-04-25
bump

---

### Post by oliwynn on 2008-04-25
I have solved the issue.  found the backup created by the upgrade.

---

### Post by boxingnun on 2008-12-20
How'd you fix it?

---

### Post by kristopolous on 2010-03-09
The magic directive is

```
AddHandler cgi-script .py
```Here's step by step way to do it
```

$ sudo su
# cd /etc/apache2/mods-available
# echo "AddHandler cgi-script .py" > python.conf
# cd /etc/apache2/mods-enabled
# ln -s ../mods-available/python.conf .
# apache2ctl restart
```Here's a few more things to check for:

[LIST]
[*]Make sure the line "#AddHandler cgi-script" is commented in /etc/apache2/mods-available/mime.conf.  For some unknown reason, having "AddHandler cgi-script .py" here will cause problems.  Maybe the directive needs to be stated after the module is loaded, I don't know.  I didn't believe this either --- but this is what testing has shown.
[*]If you are using an nginx gateway, make sure you have .py in your passthru sections
[*]Of course, make sure you aren't overriding the permissions with .htaccess or any silly nonsense like that.
[/LIST]
My sites-available lines look like this:
```

<Directory /var/www/%chris>
        AllowOverride None
        Options +ExecCGI
        Order allow,deny
        allow from all
</Directory>
```I was also able to put the "AddHandler cgi-script .py" with and without the python.conf existing and got the python code to emit.

Hopefully this helps.

---

### Post by wirelessmonkey on 2010-03-09
Why resurrect 2 year old threads?

---

### Post by cariboo on 2010-03-09
The op of this thread hasn't logged on since March 09, so he either solved his problem, or moved on. This thread is closed.

---

