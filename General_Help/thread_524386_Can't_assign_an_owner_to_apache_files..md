---
title: "Can't assign an owner to apache files."
date: 2007-08-13
forum: General Help
---

### Post by wikityler on 2007-08-13
When I right click any of the files in the apache2 directory, the properties window says that the owner and group are unknown.  When I do *egrep "^User|^Group" /etc/apache2/httpd.conf * I get no response.

I want to assign ownership to my account (tyler). I've tried: 
*sudo chown -R tyler /etc/apache2/*,
*sudo chown -R tyler /etc/apache2*,
*sudo chown -R tyler: /etc/apache2/*,
*sudo chown -R tyler: /etc/apache2*,
*sudo chown -R tyler:tyler /etc/apache2/*,
*sudo chown -R tyler:tyler /etc/apache2*,
All of which don't work. I don't get any errors, but when I check the ownership, it still says unknown.

What am I doing wrong?

---

### Post by heimo on 2007-08-13
I'd rather add my account to www-data group than change owner of www-root(*.

EDIT: Misread. You're not changing /var/www, but still I don't see why you're doing that. Try checking the owner on command line. 
```

ls -dl /etc/apache2
```

---

### Post by wikityler on 2007-08-13
Ok. That works. It says that i now own that. I got that other egrep command from the moinmoin installation guide. 

I'll contine to install moinmoin and see if it works now. Thanks!

---

