---
title: "Upstart &quot;unknown job&quot; issue"
date: 2013-12-28
forum: General Help
---

### Post by zeynel2 on 2013-12-28
I set up nginx according to instructions here [https://groups.google.com/d/msg/clojure/lnGvHyRzX7w/N8eDnwJPXuAJ](https://groups.google.com/d/msg/clojure/lnGvHyRzX7w/N8eDnwJPXuAJ) and it all went well but I am unable to start with

    ```
$ start <my app name>

```
I created `/etc/init/nomilkfor.me.conf` and this is what is in the file:

    ```
description "ubuntu 13.10 on Samsung laptop"
    author "zeynel"
                                                       
    start on startup
    stop on shutdown
                                                       
    setuid deploy
    chdir /deploy
    console log
                                                       
    env PORT=4000
    exec java -jar my-webapp-0.1.0-standalone.jar

```
I reload nginx with

    ```
$ sudo nginx -s reload

```
and I try

    ```
$ start nomilkfor.me

```
but I get 

    ```
start: Unknown job: nomilkfor.me

```
What am I doing wrong?

I also tried to open the log files in `/var/log/upstart` but I could not open them with nano.

I also tried (as suggested here [http://serverfault.com/questions/448833/upstart-does-not-see-my-job](http://serverfault.com/questions/448833/upstart-does-not-see-my-job))

```
z@ubuntu:/etc/init$ init-checkconf /etc/init/nomilkforme.conf
ERROR: failed to ask Upstart to check conf file

```

What does "ERROR: failed to ask Upstart to check conf file" mean?

[B]Edit
[/B]
For some reason, the blank lines in the nomilkforme.conf was throwing an "Unknown stanza" error. I deleted those blank lines and when I try to run the job with $ start nomilkforme I get
```

z@ubuntu:/$ start nomilkforme
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.86" (uid=1000 pid=17258 comm="start nomilkforme ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```
Can you help understanding this?

---

### Post by ian-weisser on 2013-12-28
What happens if you use sudo with those commands?
Upstart runs as root.

---

### Post by zeynel2 on 2013-12-28
I get "Job failed to start". I also include the permissions in the /deploy, if that's helpful:
```

z@ubuntu:/tmp$ sudo start nomilkforme
start: Job failed to start
z@ubuntu:/tmp$ cd /deploy
z@ubuntu:/deploy$ ll
total 8164
drwxr-xr-x  2 z    z       4096 Dec 27 08:20 ./
drwxr-xr-x 24 root root    4096 Dec 27 08:09 ../
-rw-r--r--  1 z    z    8351715 Dec 27 08:20 my-webapp-0.1.0-standalone.jar

```

---

### Post by zeynel2 on 2013-12-28
I tried this too:
```

z@ubuntu:/deploy$ init-checkconf -d /etc/init/nomilkforme.conf
DEBUG: upstart_path=/sbin/init
DEBUG: initctl_path=/sbin/initctl
DEBUG: confdir=/tmp/init-checkconf.fS7LRafn7i
DEBUG: file=/etc/init/nomilkforme.conf
DEBUG: job=nomilkforme
DEBUG: ok - no other running instances detected
DEBUG: upstart_out=/tmp/init-checkconf-upstart-output.UQ8JfJbG7n
DEBUG: upstart_cmd=/sbin/init --session --no-sessions --no-startup-event --verbose --confdir /tmp/init-checkconf.fS7LRafn7i
DEBUG: Waiting for Upstart to reply over D-Bus (attempt 1)
DEBUG: Waiting for Upstart to reply over D-Bus (attempt 2)
DEBUG: Waiting for Upstart to reply over D-Bus (attempt 3)
DEBUG: Waiting for Upstart to reply over D-Bus (attempt 4)
DEBUG: Waiting for Upstart to reply over D-Bus (attempt 5)
ERROR: failed to ask Upstart to check conf file
DEBUG: stopping secondary Upstart (running with PID 17391)

```

---

### Post by zeynel2 on 2013-12-28
The problem appears to be related to this issue explained here [http://scriptogr.am/mwhiteley/post/dbus-init-checkconf](http://scriptogr.am/mwhiteley/post/dbus-init-checkconf)
> 
[COLOR=#444444][FONT=Proxima Nova Regular]The problem is that [/FONT][/COLOR]init-checkconf[COLOR=#444444][FONT=Proxima Nova Regular] is assuming you have a [/FONT][/COLOR]dbus-daemon[COLOR=#444444][FONT=Proxima Nova Regular] running and the related environment variables set to find it. A graphical login session generally will start a dbus session for the user, but on a server install you are most likely running without one.
[/FONT][/COLOR][COLOR=#444444][FONT=Proxima Nova Regular]

Do you know how I can run the script that he mentions?[/FONT][/COLOR]

---

