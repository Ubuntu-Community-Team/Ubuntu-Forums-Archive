---
title: "Running script at startup"
date: 2013-02-13
forum: General Help
---

### Post by bchurchill on 2013-02-13
I'm setting up an image for a webserver.   I have a script on the server that fetches the latest source code for an application from a repository and does all the configuration necessary for deployment.  This script is to be run by the unprivileged user for deployment.  

Right now:
1. System boots
2. Apache starts
3. I log in, run my script, and restart apache

What I want:
1. System boots, starting all services *except* apache
2. my script runs, with only the permission of the 'deployment' user
3. start the apache services

I haven't really been following upstart or how it works at all.  I see apache still starts from System V-style init scripts.  What's the right way to set this up cleanly?

Thanks folks!

---

### Post by schragge on 2013-02-13
I guess you can have a look at
*/usr/share/doc/apache2.2-common/examples/secondary-init-script* on your system

Try to invoke your script from it like
```

[ start = "$1" ] && su -c name_of_your_script deployment
. /etc/init.d/apache2

```[COLOR=blue]**Edit.**[/COLOR]
Sorry, it's not the right way you're looking for. The simplest would be probably to put command invoking your script into */etc/init.d/apache2*:
```

...
case $1 in
     start)
         [COLOR=green]su -c name_of_your_script deployment[/COLOR]
         log_daemon_msg "Starting web server" "apache2"
...

```

---

### Post by bchurchill on 2013-02-13
> **schragge said:**
> 
[/code][COLOR=blue]**Edit.**[/COLOR]
Sorry, it's not the right way you're looking for. The simplest would be probably to put command invoking your script into */etc/init.d/apache2*:
```

...
case $1 in
     start)
         [COLOR=green]su -c name_of_your_script deployment[/COLOR]
         log_daemon_msg "Starting web server" "apache2"
...

```

This worked well, thanks!  I also like now that 'sudo service apache2 restart' also runs my script and redeploys the application.  Pretty slick.

---

