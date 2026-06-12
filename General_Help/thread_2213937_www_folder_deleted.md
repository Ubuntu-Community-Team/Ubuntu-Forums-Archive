---
title: "www folder deleted"
date: 2014-03-29
forum: General Help
---

### Post by starhunter2 on 2014-03-29
I was installing LAMP in ubuntu12.04 .Mysql couldn't install properly so i uninstalled everything ,and started installing apache again.but it showed that apache was already installed.so i deleted www folder thinking that it will be reinstalled if apache is reinstalled.But now on trying to install apache it says 'Index of/' message in local host.and www folder is not present.Is there any way I can fix this without reinstalling OS again.Expecting reply in simple(jargon less)english.

---

### Post by Lars Noodén on 2014-03-29
You could try resintalling Apache2

```

sudo apt-get --reinstall install apache2

```

The shell is not only the most powerful, flexible and (eventually) easiest.  It is also the fastest and clearest way to provide instructions on a forum or describe which actions have been taken.  ;)

---

### Post by starhunter2 on 2014-03-30
@Lars thats the problem.Apache2 is already installed (it says).

---

### Post by Lars Noodén on 2014-03-30
Strange, that re-installed the /var/www folder when I tried it.  

What you might have to do then is manually recreate the /var/www folder.  The permissions and ownership mostly do no matter as long as o=rx

---

### Post by steeldriver on 2014-03-30
> **starhunter2 said:**
> I was installing LAMP in ubuntu12.04 .Mysql couldn't install properly so i uninstalled everything ,and started installing apache again.but it showed that apache was already installed.so i deleted www folder thinking that it will be reinstalled if apache is reinstalled.But now on trying to install apache **it says 'Index of/' message in local host.and www folder is not present**.Is there any way I can fix this without reinstalling OS again.Expecting reply in simple(jargon less)english.

Can you post the exact error you are getting? Copy and paste the terminal output (between [CODE] tags please)

---

### Post by starhunter2 on 2014-03-31
sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libcglib-java libsvnclientadapter-java libcommons-collections3-java
  libjna-java libswing-layout-java jsvc junit4 libnb-org-openide-util-java
  liboro-java libdb5.1-java libnetx-java libasm3-java libgcj-bc
  gcj-4.6-jre-lib libnb-platform-devel-java libpg-java libjvyamlb-java bsh-gcj
  libfreemarker-java libcommons-compress-java libregexp-java libdb-java
  libjemmy2-java libswingx1-java libflute-java libpostgresql-jdbc-java
  libdb5.1-java-gcj javahelp2 libantlr-java libganymed-ssh2-java
  libosgi-foundation-ee-java jetty liblucene2-java libslf4j-java
  libsimple-validation-java libgcj12 libbindex-java libbytelist-java
  libmysql-java libsvn1 libxml-commons-external-java libnb-platform13-java ant
  gcj-4.6-base libosgi-compendium-java libeasymock-java libstringtemplate-java
  libcommons-logging-java aspectj libsvn-java bsh libcommons-codec-java
  libemma-java libgcj-common libjcodings-java libsac-java
  libnb-org-openide-util-lookup-java libapache-pom-java libfelix-main-java
  libini4j-java libjetty-java libjline-java libxerces2-java libnb-java5-java
  libnb-org-openide-modules-java libcommons-daemon-java libnb-apisupport3-java
  libcommons-beanutils-java libaspectj-java libdb-je-java libsac-java-gcj
  libosgi-core-java libcommons-digester-java libcommons-parent-java
  libgeronimo-osgi-support-java libdb4.8 libhamcrest-java libjtidy-java
  libfelix-framework-java libjzlib-java libxml-commons-resolver1.1-java
  libservlet2.5-java libicu4j-java libjsch-java libjoda-time-java
  libnb-javaparser-java libcommons-net1-java ant-optional libnb-ide14-java
  antlr3 libtrilead-ssh2-java libbeansbinding-java libsvnkit-java
  libgeronimo-jpa-2.0-spec-java libbetter-appframework-java
  libnb-absolutelayout-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 655 not upgraded.


....This is what is happening when i am tying to install apache.
    Also I find apache2 directory in other locked folders of var(like cache,log )

---

### Post by steeldriver on 2014-03-31
OK I've just realized that you are referring to this message, right?

```

****** Index of / ******
[[ICO]] Name Last_modified Size Description
===========================================================================
===========================================================================
     Apache/2.2.22 (Ubuntu) Server at localhost Port 80


```

That basically means your apache2 server is up and running - but there is no /var/www/index.html file. The default index file would originally have been copied over from  /usr/share/apache2/default-site by the apache2.2-common post-install  script.

Reinstalling apache2.2-common should re-create the /var/www directory (or you can re-create it manually - make sure it has the correct ownership and permissions if you do)

```

sudo apt-get update
sudo apt-get install --reinstall apache2 apache2.2-common

$ ls -ld /var/www
drwxr-xr-x 2 root root 4096 Mar 31 18:13 /var/www

```

If you want the default ("****** It works! ******") index file, you could copy it over manually (but it's just a placeholder - which you will presumably be replacing anyway):

```

sudo cp /usr/share/apache2/default-site/index.html /var/www/

```

```

****** It works! ******
This is the default web page for this server.
The web server software is running but no content has been added, yet.

```

---

### Post by jfolsom2 on 2014-03-31
You need to pay a bit more attention to the details of the advice you are getting. 

Following Lars' instructions, you need to use the "--reinstall" option, not just "install" again.  You should attempt to enclose your long outputs into CODE tags, so they are easier to read.

My secondary advice is to update your system, 655 not upgraded implies you are way out of date.

---

### Post by starhunter2 on 2014-04-01
@steeldriver,@jfolsom2,@Lars...thanks for the incredible help.
apache is runnung,so is php
but i am stuck with mysql installation.
```

sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
The following packages were automatically installed and are no longer required:
  libcglib-java libsvnclientadapter-java libcommons-collections3-java
  libjna-java libswing-layout-java jsvc junit4 libnb-org-openide-util-java
  liboro-java libdb5.1-java libnetx-java libasm3-java libgcj-bc
  gcj-4.6-jre-lib libnb-platform-devel-java libpg-java libjvyamlb-java bsh-gcj
  libfreemarker-java libcommons-compress-java libregexp-java libdb-java
  libjemmy2-java libswingx1-java libflute-java libpostgresql-jdbc-java
  libdb5.1-java-gcj javahelp2 libantlr-java libganymed-ssh2-java
  libosgi-foundation-ee-java jetty liblucene2-java libslf4j-java
  libsimple-validation-java libgcj12 libbindex-java libbytelist-java
  libmysql-java libsvn1 libxml-commons-external-java libnb-platform13-java ant
  gcj-4.6-base libosgi-compendium-java libeasymock-java libstringtemplate-java
  libcommons-logging-java aspectj libsvn-java bsh libcommons-codec-java
  libemma-java libgcj-common libjcodings-java libsac-java
  libnb-org-openide-util-lookup-java libapache-pom-java libfelix-main-java
  libini4j-java libjetty-java libjline-java libxerces2-java libnb-java5-java
  libnb-org-openide-modules-java libcommons-daemon-java libnb-apisupport3-java
  libcommons-beanutils-java libaspectj-java libdb-je-java libsac-java-gcj
  libosgi-core-java libcommons-digester-java libcommons-parent-java
  libgeronimo-osgi-support-java libdb4.8 libhamcrest-java libjtidy-java
  libfelix-framework-java libjzlib-java libxml-commons-resolver1.1-java
  libservlet2.5-java libicu4j-java libjsch-java libjoda-time-java
  libnb-javaparser-java libcommons-net1-java ant-optional libnb-ide14-java
  antlr3 libtrilead-ssh2-java libbeansbinding-java libsvnkit-java
  libgeronimo-jpa-2.0-spec-java libbetter-appframework-java
  libnb-absolutelayout-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 655 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.5 (5.5.35-0ubuntu0.12.04.2) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
This is what i get on trying to install mysql-server.

---

### Post by Valerian-webuzo on 2014-04-01
Try to purge all  dependencies and re-install mysql-server. 
  sudo apt-get purge mysql-server mysql-client mysql-common mysql-server-5.5
sudo apt-get install mysql-server

---

### Post by starhunter2 on 2014-04-04
its done.thanks all...

---

