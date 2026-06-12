---
title: "Apache2 - Modal Logon page"
date: 2015-02-28
forum: General Help
---

### Post by ylafont on 2015-02-28
Ubunutu 14.04
Apache 2.4.7

I began to create a modal logon page on Apache to secure a site and notice some differences in installation that i need some clarification before proceeding.

I followed this procedures, which may be outdated and before messing anything up I wanted to check
[http://melandri.net/2012/04/29/using-apache-mod-auth-form/](http://melandri.net/2012/04/29/using-apache-mod-auth-form/)

For the modal logon page to function the following modules entries are needed in the /etc/apache2/apache2.conf file.  

LoadModule auth_form_module modules/mod_auth_form.so
LoadModule session_module modules/mod_session.so
LoadModule request_module modules/mod_request.so
LoadModule session_cookie_modules/mod_session_cookie.so

However, there is not modules folder in /etc/apache2 with this installation.

I did located these modules in /usr/lib/apache2/modules

I tried to load them from the folder, but not sure if it worked or not, I checked to see what modules were loaded with **apache2ctl -M **and they were not listed. 

Can this folder just be copied over?

or do i need to re-compile Apache with those modules?  Which i read somewhere was not a good thing.

Thank you for the assistance.

---

