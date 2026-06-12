---
title: "ZFS ZED Email  what am I doing wrong?"
date: 2018-10-26
forum: General Help
---

### Post by Chrismallia on 2018-10-26
Hi all.

I have ssmtp installed and working fine as I send test emails and also NETDATA is using the ssmtp to send emails so i know SSMTP is working fine. The problem is I cant get ZFS to send the emails I have edit ZED.RC, could anyone see if there is something wrong with the config file?
Thanks 




```
# zed.rc
#
# This file should be owned by root and permissioned 0600.
##


##
# Absolute path to the debug output file.
#
ZED_DEBUG_LOG="/tmp/zed.debug.log"


##
# Email address of the zpool administrator for receipt of notifications;
#   multiple addresses can be specified if they are delimited by whitespace.
# Email will only be sent if ZED_EMAIL_ADDR is defined.
# Disabled by default; uncomment to enable.


ZED_EMAIL_ADDR="myemail@gmail.com"


##
# Name or path of executable responsible for sending notifications via email;
#   the mail program must be capable of reading a message body from stdin.
# Email will only be sent if ZED_EMAIL_ADDR is defined.
#
ZED_EMAIL_PROG="mail"


##
# Command-line options for ZED_EMAIL_PROG.
# The string @ADDRESS@ will be replaced with the recipient email address(es).
# The string @SUBJECT@ will be replaced with the notification subject;
#   this should be protected with quotes to prevent word-splitting.
# Email will only be sent if ZED_EMAIL_ADDR is defined.
#
ZED_EMAIL_OPTS="-s '@SUBJECT@' @ADDRESS@"


##
# Default directory for zed lock files.
#
ZED_LOCKDIR="/var/lock"


##
# Minimum number of seconds between notifications for a similar event.
#
ZED_NOTIFY_INTERVAL_SECS=3600


##
# Notification verbosity.
#   If set to 0, suppress notification if the pool is healthy.
#   If set to 1, send notification regardless of pool health.
#
ZED_NOTIFY_VERBOSE=1


##
# Send notifications for 'ereport.fs.zfs.data' events.
# Disabled by default
#
#ZED_NOTIFY_DATA=1


##
# Pushbullet access token.
# This grants full access to your account -- protect it accordingly!
#   <https://www.pushbullet.com/get-started>
#   <https://www.pushbullet.com/account>
# Disabled by default; uncomment to enable.
#
#ZED_PUSHBULLET_ACCESS_TOKEN=""


##
# Pushbullet channel tag for push notification feeds that can be subscribed to.
#   <https://www.pushbullet.com/my-channel>
# If not defined, push notifications will instead be sent to all devices
#   associated with the account specified by the access token.
# Disabled by default; uncomment to enable.
#
#ZED_PUSHBULLET_CHANNEL_TAG=""


##
# Default directory for zed state files.
#
#ZED_RUNDIR="/var/run"


##
# Turn on/off enclosure LEDs when drives get DEGRADED/FAULTED.  This works for
# device mapper and multipath devices as well.  Your enclosure must be
# supported by the Linux SES driver for this to work.
#
ZED_USE_ENCLOSURE_LEDS=1




##
# The syslog priority (e.g., specified as a "facility.level" pair).
#
ZED_SYSLOG_PRIORITY="daemon.notice"


##
# The syslog tag for marking zed events.
#
ZED_SYSLOG_TAG="zed"





```

---

### Post by Chrismallia on 2018-10-27
Solved it and did a little writeup here  [https://ubuntuforums.org/showthread.php?t=2404713&p=13811934#post13811934](https://ubuntuforums.org/showthread.php?t=2404713&p=13811934#post13811934)

---

