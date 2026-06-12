---
title: "Apache2 using 100% CPU in dapper"
date: 2007-02-05
forum: General Help
---

### Post by young_dazza on 2007-02-05
Hi

Recently my apache2 process has been using 100% cpu, as soon as apache is started, even before there are entries in /var/log/apache2/access.log or error.log. Accessing the website becomes really sluggish, and sometimes times out.

I have not changed my apache configuration lately. I have done a upgrade of the packages to the latest security releases in the last few weeks but I am not sure whether this was the trigger. I found bug#56220 which sounds very similar to my problem, however I tried downgrading apache2-mpm-prefork (and related packages) to 2.0.55-4ubuntu2 which didnt solve the problem.

On my webserver i have squirrelmail, gallery2 and virtualhosts set up. "apache2ctl status" reports "The requested URL /server-status was not found on this server." On startup, error.log reports: "[notice] Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 configured -- resuming normal operations"

Any help or suggestions appreciated.

Cheers
- young_dazza

---

### Post by young_dazza on 2007-02-05
UPDATE: For about the tenth time today I did a "apache2ctl stop" followed at some time later by a "apache2ctl start" but this time the problem has actually gone away (at least for now!). Maybe apache was doing some kind of indexing or something similar? The logs in /var/logs/apache2 didnt suggest that anything was going on. If this happens again, how can I find out what apache is doing? As I said above, "apache2ctl status" returns an error.

UPDATE2: its happening again - 100% CPU usage. A stop/start didnt fix the problem.

Cheers
- young_dazza

---

### Post by young_dazza on 2007-02-07
This problem seems to have gone away. The only thing I changed was robots.txt (so that slideshows and resized images arent downloaded by yahoo & google). However I am sceptical as to whether this actually fixed the problem because CPU load would go to 100% even before yahoo or google tried to download any pages (ie before any new entries in access.log or error.log)

---

