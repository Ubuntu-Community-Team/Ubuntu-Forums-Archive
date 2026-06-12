---
title: "System/Admin/Users and groups - not working"
date: 2007-06-14
forum: General Help
---

### Post by Hadron Quark on 2007-06-14
if I try to open Users & Groups from my Gnome menu I get

"The configuration could not be loaded - you are not allowed access to the system configutation".

My user is, of course, a sudoer and I regularly use the same userid to edit root files using sudo.

I have googled this up and editing menu option to have "gksu" is already done. Still does not work.

If I try

"sudo users-admin" from the command line I get:

(users-admin:7346): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(users-admin:7346): Liboobs-WARNING **: There was an unknown error communicating with the backends: The name org.freedesktop.SystemToolsBackends.UsersConfig was not provided by any .service files

(users-admin:7346): Liboobs-WARNING **: There was an unknown error communicating with the backends: The name org.freedesktop.SystemToolsBackends.GroupsConfig was not provided by any .service files
- using device default
- using device default

This appears to be quite a common problem although I see one developer closed it because the poster decided not to bother pursuing it anymore.

Does anyone have any insight into this?

I tried reinstalling dbus and gnome-system-tools but it made no difference.

---

### Post by minoas on 2007-07-06
Same Here.After working without glitches without modifying the system I noticed the Service-admin and User-admin are just not working.They are displaying empty lists.Also tried reinstalling dbus gnome-system-tools from synaptic with no luck.Any help is aprreciated..

And the following command works ok but still I get the errors described above when trying to terminal the users/services

sudo /etc/init.d/dbus start

---

### Post by mcook2 on 2007-07-26
I am also having this problem affecting:

gksu network-admin
gksu users-admin
gksu services-admin.

See post at  [http://ubuntuforums.org/showthread.php?p=3086753#post3086753]("http://ubuntuforums.org/showthread.php?p=3086753#post3086753")

Michael Cook

---

