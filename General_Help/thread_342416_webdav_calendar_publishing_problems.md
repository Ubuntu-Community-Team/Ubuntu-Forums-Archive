---
title: "webdav calendar publishing problems"
date: 2007-01-20
forum: General Help
---

### Post by tr333 on 2007-01-20
i'm having trouble publishing a calendar from iCal in OSX to a webdav server running on apache2 in ubuntu.

i followed the how-to at [http://ubuntuforums.org/showthread.php?t=119228]("http://ubuntuforums.org/showthread.php?t=119228") to setup the webdav server, but iCal is giving an "access forbidden by server" message when trying to publish.

the apache access log seems to show a 405 error, but im not sure what that means.
```
xxx.xxx.xxx.xxx - - [20/Jan/2007:18:38:07 +1100] "PUT /davhome/test.ics HTTP/1.1" 405 342 "-" "DAVKit/0.1"
```
note: xxx.xxx.xxx.xxx is my public ip address.

the output of /etc/apache2/mods-enabled/dav_fs.conf:
```
DAVLockDB /var/lock/apache2/DAVLock

#DAVLockDB /tmp/DAVLock
#DAVMinTimeout 600

<Location /davhome/>
        Dav On

        AuthType Basic
        AuthName username
        AuthUserFile /var/www/davhome/.DAVlogin

        <LimitExcept OPTIONS>
                Require user username
        </LimitExcept>
</Location>
```

i'm running this server behind a router, but i can access the webserver part of the server from outside the router.

EDIT:  I installed cadaver and i can connect to the webdav server.  could this just be a problem from osx end, or is it a config problem with apache/webdav?

---

### Post by tr333 on 2007-01-21
Problem solved!!!!!

To fix the permission errors, I had to chown www-data:www-data the webdav directory on the server.  I should have realised this earlier since apache services are running as www-data and they need to write to the directory ](*,)

---

