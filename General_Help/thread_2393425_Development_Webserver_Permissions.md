---
title: "Development Webserver Permissions"
date: 2018-06-03
forum: General Help
---

### Post by Gottier on 2018-06-03
In the past I've set up my development webserver by adding myself to the www-data group:

```
sudo usermod -a -G www-data gottier
sudo chown -R gottier:www-data /var/www
find /var/www -type d -print0 | xargs -0 chmod 2775
```

So, this is mostly fine, but when I create directories and files through php (www-data), php can not delete the directories it created:

```
<?php
mkdir('example',0775); // Creates just fine
exec('rm -rf ./example'); // Does not remove
```

So then I was reading that I could perhaps create a new group, add myself to it, and chown /var/www like this:

```
sudo addgroup webdevs
sudo usermod -a -G webdevs gottier
sudo chown -R www-data:webdevs /var/www
```

Now what happens is that php(www-data) can create and remove the directories, but when I try to create or edit files in my text editor, It barks at me, saying I don't have permission to do such things. I've even tried adding www-data to the new webdevs group.

So, I read that perhaps I could use setfacl:

```
sudo setfacl -d -R -m u:gottier:rwx /var/www
```

But that didn't do anything. No change.

I did also go to /etc/apache2/envvars and added:

```
umask 002
```

I've done all the suggestions I could find. I just want to be able to have php/apache run normally, create and edit files/directories without problems, and also have permission to use my text editor to do the same. What am I missing? **Please correct me if I'm wrong, but it is my understanding that if I am a member of a group that has full permissions for files and directories, I would be able to do anything the owner does, or at least read/write/delete.**

---

### Post by TheFu on 2018-06-03
Did you logout and login after modifying groups?   Each session (or process) needs to restart from a session that picks up the new group membership for those changes to be seen.

For a daemon account to pick up membership changes, I think a reboot might be needed, but you can try restarting all the processes first.

---

### Post by Gottier on 2018-06-03
> **TheFu said:**
> Did you logout and login after modifying groups?   Each session (or process) needs to restart from a session that picks up the new group membership for those changes to be seen.

For a daemon account to pick up membership changes, I think a reboot might be needed, but you can try restarting all the processes first.


Yes! A quick log out and back in, and now everything works! I had closed the terminal and started a new one, thinking that was all I needed to do for the group to be applied, but the log out/in made it happen. Thank you very much. I appreciate the help.

---

### Post by TheFu on 2018-06-03
> **Gottier said:**
> Yes! A quick log out and back in, and now everything works! I had closed the terminal and started a new one, thinking that was all I needed to do for the group to be applied, but the log out/in made it happen. Thank you very much. I appreciate the help.

At login, a session is made that is the parent for all others to inherit for that specific userid. Logout and login again is the easy way to make it effective for a single userid.

However, you can modify groups, then use "newgrp" inside a shell and all sub-shells will inherit the new settings, but other terminals or launched programs will not until the session is restarted.  

For programs running as services, the inheritance comes from PID #1 ... and that gets loaded at boot, so getting it recognized, while possible using different userids and terminals, really is easiest thanks to systemd by a reboot.  Pre-systemd, it was trivial, but progress moves forward and sometimes we loose capabilities for something "new".

Anyway, if this is solved, please mark the thread as solved in the Thread Tools button near the top to help other community members.  If not solved, please clarify the issue.

---

