---
title: "tomcat install problem: tomcat5.5-admin not in /usr/share/tomcat5.5-webapps"
date: 2008-02-03
forum: General Help
---

### Post by mwk88 on 2008-02-03
Hi folks, I've done a fresh install of tomcat5.5, tomcat5.5-webapps and tomcat5.5-admin from the Packgage Manager on a fresh 7.10 install running sun jvm. I'm hitting three problems, my guess is they are related but I'm stumped:

Problem 1) tomcat5.5-webapps installs to /usr/share/tomcat5.5-webapps, but tomcat5.5-admin installs to a different location /usr/share/tomcat5.5/server/webapps. Is this correct? Seems weird to me...

[http://localhost:8180](http://localhost:8180) shows the webapps fine but does not see the admin app, i.e. localhost:8180/admin shows the "admin tools no longer automatically installed" page that is included with the webapps. So looks like /usr/share/tomcat5.5-webapps is the path that works (but see problem 2 also).

So, why does admin install to a different path?

Problem 2) Although the webapps work fine after installation, I cannot deploy any new apps. If I copy a .war to /usr/share/tomcat5.5-webapps I just get a blank page.

Even weirder, if I move one of the tomcat5.5-webapps out of webapps (e.g. mv ROOT* somewhere else) and then immediately move it back again completely unchanged, it no longer runs, I just get blank pages from tomcat for that app. At first I thought autodeploy was not working, but even if I restart tomcat it does not come back. However, if I uninstall and reinstall the tomcat5.5-webapps package it works again.

Problem 3) there are *three* webapps directories scattered around, which seems odd: 
  /usr/share/tomcat5.5/webapps -> /var/lib/tomcat5.5/webapps
  /usr/share/tomcat5.5/server/webapps
  /usr/share/tomcat5.5-webapps

Reading some other postings it sounds like the third version may be a newer configuration change. Did that change break something?

Thanks, any advice would be appreciated!

---

