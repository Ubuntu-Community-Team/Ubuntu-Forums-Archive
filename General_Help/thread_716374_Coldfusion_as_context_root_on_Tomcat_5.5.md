---
title: "Coldfusion as context root on Tomcat 5.5"
date: 2008-03-05
forum: General Help
---

### Post by hebetude on 2008-03-05
It can be done!  Google will lead you to 50 dead ends though.  Here is the simple and dirty way to serve Coldfusion as the root Tomcat application instead of the lame ROOT.war.

Stop Tomcat
** /etc/init.d/tomcat55 stop**

Open up tomcat configuration:
** gedit /etc/tomcat5.5/server.xml**

Change:
```

<Host name="localhost" appBase="webapps"
       unpackWARs="true" autoDeploy="true"
       xmlValidation="false" xmlNamespaceAware="false">
    <Context path="" docBase="webapps" />

```to
```

      <Host name="localhost" appBase="/var/lib/tomcat5.5/webapps"
       unpackWARs="true" autoDeploy="true"
       xmlValidation="false" xmlNamespaceAware="false">
    <Context path="" docBase="cfusion" />

```start Tomcat.  
** /etc/init.d/tomcat55 start**

One warning it won't tell you if it fails to start.  If you want to be super rigorous you can study the logs in /var/log/tomcat55.  A quicker way is to restart Tomcat a couple of times.  If it takes ~6-8seconds to stop Tomcat then it is starting correctly.

Somehow this didn't break my links to the manager, so assuming you got it up and running go to [http://localhost:8180/manager/html](http://localhost:8180/manager/html)

Mine shows Adobe Coldfusion 8 sitting in /cfusion & /.  You can verify this by going to [http://localhost:8180/CFIDE/administrator/](http://localhost:8180/CFIDE/administrator/) or put a .cfm page in your cfusion root.

This isn't the most ideal setup, but your fusebox apps won't break just because Tomcat hijacks ROOT.  Let me know if there is a way I can drop .cfm pages in /var/www and coldfusion loads them.

---

### Post by hebetude on 2008-03-05
BTW, coldfusion will also claim /cfusion as its root.  So you won't be able to use /cfusion as a sub-directory.  A small price to pay for 10minutes to converting tomcat into a usable Application Server.

This is fully compatible with Apache httpd hook-in.  I didn't have to change anything in my mod_jk setup.

---

