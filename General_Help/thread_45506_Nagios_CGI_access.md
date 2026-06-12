---
title: "Nagios CGI access"
date: 2005-06-30
forum: General Help
---

### Post by Krank on 2005-06-30
Sooooo... I finally managed to not only install, but also setup Nagios.

For the record, I use Apache2.


I have managed to make [http://127.0.0.1/nagios](http://127.0.0.1/nagios) (and equivalents related to my .com adress and internal network IP) work. I can even log in, since I changed the password of the "nagiosadmin" user via htpasswd.

My problem now is that Nagios says this:

"It appears as though you do not have permission to view information for any of the hosts you requested...
If you believe this is an error, check the HTTP server authentication requirements for accessing this CGI
and check the authorization options in your CGI configuration file."

I can log in just fine, but I cannot access the CGIs?

Well, according to the documentation, I should add a .htaccess file in /usr/lib/cgi-bin/nagios (chich is where the CGI's reside). In this file, I should enter the following:

The second step is to create a file named .htaccess in the root your CGI directory (and optionally also you HTML directory) for Nagios (usually /usr/lib/cgi-bin/nagios and /usr/share/nagios/htdocs, respectively). The file(s) should have contents similiar to the following...

AuthName "Nagios Access"
AuthType Basic
AuthUserFile /etc/nagios/htpasswd.users
require valid-user


I did this. Restarted Nagios. restarted Apache. No change, same error.



So, Oh thou mightiful residents of this fora ("forum" in singular is "fora" - did you know that?") - what, oh what, can I do to fix this?

---

### Post by bugmenot on 2005-07-26
[QUOTE=Krank]("forum" in singular is "fora" - did you know that?")[/QUOTE]
 [-X  "forum" in singular is "forum" -  "forum" in plural is "fora".  (next time you're trying to be pedantic and condescending, please try also to be accurate.   :razz: )

Make sure the username you're using is referenced in the "authorized_for" declarations in cgi.cfg:

authorized_for_system_information=nagadm
authorized_for_system_commands=nagadm
authorized_for_configuration_information=nagadm
authorized_for_all_services=nagadm
authorized_for_all_hosts=nagadm
authorized_for_all_host_commands=nagadm
authorized_for_all_service_commands=nagadm

---

