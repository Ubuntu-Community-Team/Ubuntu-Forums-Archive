---
title: "empty mysql.log"
date: 2005-05-23
forum: General Help
---

### Post by GOwin on 2005-05-23
Hi. Would anyone know why mysql.log is empty?

I'm trying to determine the errors in my apps and was surprised to find out that nothing is being logged by mysql.

---

### Post by GOwin on 2005-05-25
**bump**

anyone?

---

### Post by jcooper on 2005-05-26
Is logging enabled?

And is it the database having problems, or your apps?

---

### Post by GOwin on 2005-05-26
Logging is already enabled using the my.cnf settings.

I still don't see any logs

---

### Post by Ai1dRo0kNotBot on 2007-12-05
I've got the same thing on Ubu 7.10 (Gutsy).
IMHO log file should be defined in mysql.cnf byhand.

---

### Post by jrgns on 2008-04-10
I'm also seeing this, updated Ubuntu 7.10

The conf file says 

# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log            = /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)

So check /var/log/syslog for errors. I assume that the #log line should be uncommented for the normal logging to work.

J

---

