---
title: "/var/log permission"
date: 2014-09-16
forum: General Help
---

### Post by ELMIT on 2014-09-16
What is the best way to solve this:

/var/log is owned by root:syslog

A user should also write log files into this directory and log rotate should handle this file.
I am not sure if adding a user to the syslog group would be good, like adding peter:

syslog:x:103:peter

---

### Post by Lars Noodén on 2014-09-16
I'd make a subdirectory for that user or group and then (e.g. /var/log/peter/ ) set the write permissions for that directory only.  That keeps things as boxed in as possible.  

For log rotation, I'd create a new configuration file inside /etc/logrotate.d/ for that user's log file.  The manual page for logrotate.conf will have all your options but you can use some of the existing files as examples.  What you are looking for to set user and group ownership would be 'create' with your choice of mode, user and group.  

```

        create 640 peter adm

```

Other options like 'delaycompress' can be useful.  Depending on how much volume the logs are, you might want to keep a larger number of old, compressed logs around.

---

### Post by ian-weisser on 2014-09-16
You shouldn't need to add a user if you are using the existing log-writing tools.
You may need to edit /etc/rsyslogd.conf to add a new logfile filter.

rsyslogd accepts input from many existing log-writing tools, most of which are just sockets - rsyslogd listens for socket input, too.

---

### Post by SeijiSensei on 2014-09-16
Users should write log files to their home directories, not to /var/log.  Logrotate will rotate files anywhere, not just in /var/log.  I use it to rotate files in my home directory every day.  Add a file to /etc/logrotate.d/ like this:

```

/home/username/mylog { 
    daily
    rotate 31
}

```

There are good reasons why permissions are set up the way they are in *nix.  Work with them, not around them.

---

