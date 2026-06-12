---
title: "Notification when a service stops"
date: 2013-05-02
forum: General Help
---

### Post by bullet333 on 2013-05-02
I'm trying to figure out if I could get an email notification when a specific service stops on my Ubuntu server?  The server is used as a Proxy and Web Filter using both Squid3 and Dansguardian which are the two services I'd like to monitor.

My concern is that I have a service (Dansguardian) that likes to stop randomly.  I created another thread [here trying to resolve that]("http://ubuntuforums.org/showthread.php?t=2141420").

---

### Post by bullet333 on 2013-05-03
Anyone got any ideas?  Still cannot figure this out!

---

### Post by slickymaster on 2013-05-03
You can check [Monit]("http://mmonit.com/monit/"). It's open source and you can manage and monitor, processes, programs, files, directories and filesystems on a UNIX system.

---

### Post by bullet333 on 2013-05-03
> **slickymaster said:**
> You can check [Monit]("http://mmonit.com/monit/"). It's open source and you can manage and monitor, processes, programs, files, directories and filesystems on a UNIX system.

Thank you!  I will try that out.

---

### Post by bullet333 on 2013-05-03
OK I got Monit running and it works great!  I set it up to monitor Squid3, Dansguardian and some other services.  **Although I still don't seem to be getting emails **when there's an issue (a service goes down/offline).  I've tried altering my config a lot per what other online users suggested but I just cannot figure out what I'm doing wrong!  Here is my current MONITRC config:

```

set daemon 5 # in seconds
set logfile /var/log/monit.log
set idfile /var/lib/monit/id
set statefile /var/lib/monit/state
  set eventqueue
      basedir /var/lib/monit/events # set the base directory where events will be stored
      slots 100                     # optionally limit the queue size


set httpd port 2812 and
allow localhost # allow localhost to connect to the server
allow 10.0.0.0/255.255.255.0 # allow any host on 10.0.0.* subnet


##MAIL SETTINGS
set mailserver mail.domain.com
username "user" password "password"


# You can define your mail-notification format.
# --8<--
 set mail-format {
      from: monit@$HOST
   subject: monit alert --  $EVENT $SERVICE
   message: $EVENT Service $SERVICE
                 Date:        $DATE
                 Action:      $ACTION
                 Host:        $HOST
                 Description: $DESCRIPTION


            Your faithful employee,
            Monit
 }
# --8<--


# Set a default mail from-address for all alert messages emitted by monit.
# All alert mail will be sent to below mail address.
#set mail-format { from: bullet@squid }
set alert myemail@domain.com

##CHECK DANSGUARDIAN SERVICE
check process dansguardian with pidfile /var/run/dansguardian.pid
   start program = "/etc/init.d/dansguardian start"
   stop program  = "/etc/init.d/dansguardian stop"
   if failed host 10.0.0.7 port 8080 then restart
   if 5 restarts within 5 cycles then timeout

```
NOTE: I removed the usernames/password and domains from the above code for security reasons!

Please help!

---

### Post by slickymaster on 2013-05-06
Accordingly to the [Monit documentation]("http://www.mmonit.com/monit/documentation/monit.html#setting_a_mail_server_for_alert_messages") > ... the mail server Monit should use to send alert messages is defined with a global set statement (keywords are in capital and optional statements in [brackets]):
```
SET MAILSERVER {hostname|ip-address [PORT port]
                [USERNAME username] [PASSWORD password]
                [using SSLV2|SSLV3|TLSV1] [CERTMD5 checksum]}+ 
                [with TIMEOUT X SECONDS]
                [using HOSTNAME hostname]
```

In your's MONITRC config file, that doesn't seem to happen. One more thing, check if the port the mail server uses is being blocked.

---

### Post by bullet333 on 2013-05-06
It works!!!

I changed it to 

```

SET MAILSERVER mail.domain.com, ip-address

```

and my inbox got filled with all the queue'd messages from the other day!  I manually stopped a service, got an email alert and it restarted it with another email notification!  Thank you so much!

---

### Post by slickymaster on 2013-05-06
Glad you got it fixed.

Please, mark the thread as solved so other people searching the forums know that this thread provides a working solution for the problem. See my signature on how to do it.

---

