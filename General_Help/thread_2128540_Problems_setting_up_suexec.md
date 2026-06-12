---
title: "Problems setting up suexec"
date: 2013-03-23
forum: General Help
---

### Post by ptmuldoon on 2013-03-23
I'm hoping someone can help me with getting suexec working correctly.  Although I am using Ubuntu 12.04 LTS 32-bit, I basically followed most of this.

[http://www.server-world.info/en/note?os=Ubuntu_11.04&p=httpd&f=7](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=httpd&f=7)

Here's some more background.

There are only 2 users on my system.  root and ptmuldoon (myself)

I am hosting on a Linode VPS, and my websites point to /home/ptmuldoon/public/SITENAME/public

I can access each website just fine.

I installed apache2-suexec-custom
I enabled the mod with a2enmod

When I go to the directory /etc/apache2/mods-enabled  I do see suexec.load shown

Also, I have to 2 config files set up in /etc/apache2/suxec.  One is labeled www-data and the other ptmuldoon

In both config files I have the following two top lines

/home/ptmuldoon/
public

I think everything above has been correct.  But I do not know how to confirm if suexec is working correctly.

Using sftp, and the username of ptmuldoon, I've upload the following test script

```

$processUser = posix_getpwuid(posix_geteuid());
print $processUser['name'];

```

However, the above returns the user name of www-data. Shouldn't it be returning ptmuldoon, the user who uploaded it?

---

