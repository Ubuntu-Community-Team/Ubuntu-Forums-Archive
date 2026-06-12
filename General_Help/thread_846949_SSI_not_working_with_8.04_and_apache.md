---
title: "SSI not working with 8.04 and apache"
date: 2008-07-02
forum: General Help
---

### Post by harikrishna_gp on 2008-07-02
Hi ,
  I am relatively new to the web programming world!
I am trying to get Server side includes working with apache on 8.04

I have followed the wiki at [https://help.ubuntu.com/community/ServerSideIncludes]("https://help.ubuntu.com/community/ServerSideIncludes")

I could not get it to work. Any help in this regard would be appreciated.

Here is the output of [B] apache2ctl fullstatus
[/B]
```
Apache Server Status for localhost
Server Version: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch
Server Built: May 29 2008 08:44:16

```

Thanks
Hari

---

### Post by mistycabal on 2008-10-27
I am trying to find a solution to the same problem. My SSI is not working, and I'm wondering if there is some different type of solution needed when you set up virtual hosts.

Basically, I configured according to the directions found here:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

Everything is running fine, but when I try to follow the directions from this page: 
[https://help.ubuntu.com/community/ServerSideIncludes](https://help.ubuntu.com/community/ServerSideIncludes)

My SSI test page doesn't work.

I'm wondering if it has to do with the /etc/apache2/sites-available/default settings where you have a directory listing at: <Directory /var/www/>

Perhaps because I set up virtual hosts I have to change all of those? I've tried changing just the one that the directions indicate to <Directory /home/nicole/public-html/> (which is where I have a virtual host set up). Doesn't work. Tried it with the normal /var/www/ - doesn't work either.

What I haven't done is change ALL of the /var/www/ calls in that file to reflect the virtual directory. But then, it doesn't seem to make sense that the base file would have to be edited to reflect the virtual directories anyway.

Any ideas on how to get this working so I can run SSI correctly?

~Nicole

---

### Post by rfulcher on 2008-10-29
Did you make the include call correctly.

1. Put the files in the same directory.
2. Use this line
<!--#include virtual="footer.html" -->

---

### Post by UnD3RsC0R3 on 2010-07-02
I had the same problem in 10.04, apache 2.2.x

This is how i fixed it:

Follow this manual: [https://help.ubuntu.com/community/ServerSideIncludes](https://help.ubuntu.com/community/ServerSideIncludes)

then, if you did like me and changed your main directory from "/var/www/" you also must edit the file "/etc/apache2/sites-enabled/mysite" and replace the same parts. I didnt use httpd.conf or .htaccess files.

I'm posting this because i've been searching around this forum and haven't found any answer that fixed my problem.

---

