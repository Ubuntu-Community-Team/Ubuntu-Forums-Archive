---
title: "Apache2 + Subversion"
date: 2005-03-30
forum: General Help
---

### Post by tucanoj on 2005-03-30
I'm trying to set up a subversion server with apache2.  Whenever I try to view my repository directory I get the following error```
Could not open the requested SVN filesystem
``` .  I'm not sure whats going on, but I've read the wiki and other resources and can't figure it out.  

Here is my http.conf:
```
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
#LoadModule dav_module  /usr/lib/apache2/modules/mod_dav.so
#LoadModule dav_svn_module   /usr/lib/apache2/modules/mod_dav_svn.so

<IfModule mod_dav_svn.c>
Include /home/jstaley/svn/conf/mod_dav_svn.conf
</IfModule>
``` 




and my mod_dav_svn.conf file:
```
Include /home/jstaley/svn/conf/public_default_policy.conf
#Include /home/jstaley/svn/conf/private_default_policy.conf
``` 


and the public_default_policy.conf is:
```
<Location /svn>
    DAV svn
    SVNPath /home/jstaley/svn
    AuthType Basic
    AuthName "SVN repos"
    AuthUserFile /home/jstaley/svn/conf/svnpasswd
    <LimitExcept GET PROPFIND OPTIONS REPORT>
      Require valid-user
    </LimitExcept>
</Location>
```                   


I have also done the following:
```
sudo chown -R www-data.www-data /home/jstaley/svn
``` 


I can access apache just fine with [http://localhost](http://localhost) but if I enter
[http://localhost/svn](http://localhost/svn) I get the error message I was talking about earlier.
Anyone know whats going on?

---

### Post by tucanoj on 2005-03-31
bump

---

### Post by amaterasu on 2005-04-19
[http://wiki.debian.net/?SubversionApache2SSLHowto](http://wiki.debian.net/?SubversionApache2SSLHowto)

---

