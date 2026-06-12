---
title: "LAMP install no longer working"
date: 2022-08-10
forum: General Help
---

### Post by cearlp on 2022-08-10
Installed LAMP on 20.04 and it worked for many months.
Suddenly there is no response from the server,,,remotely from a Mac system using Safari or input locally as localhost with Firefox.
Going through the install steps again shows everything as already installed and the most current versions of each component.
What can I do to isolate the problem?

---

### Post by TheFu on 2022-08-11
Look at the log files for each component and the OS.

---

### Post by cearlp2 on 2022-08-15
Error log states:
[Mon Aug 15 00:00:01.210722 2022] [mpm_prefork:notice] [pid 1107] AH00163: Apache/2.4.41 (Ubuntu) OpenSSL/1.1.1f configured -- resuming normal operations
[Mon Aug 15 00:00:01.210733 2022] [core:notice] [pid 1107] AH00094: Command line: '/usr/sbin/apache2'
[Mon Aug 15 15:19:31.588520 2022] [authz_core:error] [pid 33145] [client 195.96.137.4:63687] AH01630: client denied by server configuration: /var/www/html/server-status

Where can one find the /var/www/html/server

[COLOR=#232629][FONT=-apple-system]Apachectl status gives an error 113: www-browser : not found. Maybe you need to install a package providing www-browser or you need to adjust APACHE_LYNX variable in apache2.envvars.
[/FONT][/COLOR][COLOR=#232629][FONT=var(--theme-post-body-font-family)][FONT=-apple-system]The APACHE_LYNX variable has always been commented out in envvars. Uncommenting it and even changing -dump to --dump has no effect. What am I missing?[/FONT]
update-alternatives --display x-www-browser returns the following:

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]x-www-browser - auto mode link best version is /usr/bin/firefox link x-www-browser is /usr/bin/x-www-browser/usr/bin/firefox - priority 40

What am I missing?[/FONT][/COLOR]

---

