---
title: "Guide to get ZFS ZED on ubuntu to send Email alerts"
date: 2018-10-27
forum: General Help
---

### Post by Chrismallia on 2018-10-27
Here is a way to get ZFS on Ubuntu to send you Email alerts 

Install 

[FONT=&amp]mailutils msmtp msmtp-mta s-nail

create a config file for msmtp at /etc/msmtprc and put in this info with your own details

[/FONT]```
# Set default values for all following accounts.
defaults
auth           on
tls            on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
logfile        ~/.msmtp.log


account alerts
host smtp.gmail.com
port 587
from serverexample@gmail.com
user serverexample@gmail.com
password server218


# Set a default account
account default : alerts

```

Now save and go to [FONT=&amp]/etc/zfs/zed.d/zed.rc and follow this example

[/FONT]```
##
# zed.rc
#
# This file should be owned by root and permissioned 0600.
##


##
# Absolute path to the debug output file.
#
#ZED_DEBUG_LOG="/tmp/zed.debug.log"


##
# Email address of the zpool administrator for receipt of notifications;
#   multiple addresses can be specified if they are delimited by whitespace.
# Email will only be sent if ZED_EMAIL_ADDR is defined.
# Disabled by default; uncomment to enable.
#
ZED_EMAIL_ADDR="email you want to receive alerts on"


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
ZED_EMAIL_OPTS="-s '@SUBJECT@' @ADDRESS@ -r serverexample@gmail.com"


##
# Default directory for zed lock files.
#
#ZED_LOCKDIR="/var/lock"


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
#ZED_SYSLOG_PRIORITY="daemon.notice"


##
# The syslog tag for marking zed events.
#
#ZED_SYSLOG_TAG="zed"

```

Now sudo zpool scrub pool and you will receive the email event alert.

I am not really good in writing up Guides so please anyone feel free to correct anything 



[FONT=&amp]

[/FONT]

---

