---
title: "insserv returning errors about converted upstart jobs"
date: 2013-07-05
forum: General Help
---

### Post by antiartist on 2013-07-05
Attempting to install the server version of Calibre on a headless Ubuntu 10.04 LTS box following instructions found [here]("http://linuxserver2011.wordpress.com/2011/03/26/calibre-ebook-server-setup-ubuntu-10-10/")


Issuing the following command:
```
[COLOR=#00FF00][FONT=Helvetica]*sudo insserv calibre*[/FONT][/COLOR]
```

Returns the following error:
```
tom@HouseMedia:/etc/init.d$ sudo insserv calibre
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'K20avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'K20dropbox' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: Service network has to be enabled to start service calibre
insserv: exiting now! 
```

Is insserv attempting to start/stop a job using the /etc/init.d/ method?  I don't understand why this error is happening?  Any help you can offer would be appreciated

---

### Post by aedmunds on 2013-08-01
Did you ever find a solution to this? I am running into the same issue.

---

### Post by antiartist on 2013-08-01
Nope, I never did find a solution for this.  I'm a little surprised that this hasn't generated any responses at all.

---

