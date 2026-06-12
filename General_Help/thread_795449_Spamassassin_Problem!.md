---
title: "Spamassassin Problem!"
date: 2008-05-15
forum: General Help
---

### Post by kj6eo on 2008-05-15
Hello and thanks for reading my post!  I'm having a weird problem with Spamassassin.  There is allot of chatter about this problem on the WEB but I haven't found a solution yet that would work for me.  Here is the error message I'm getting:

> kj6eo@ub:/etc/init.d$ sudo ./spamassassin start
Starting SpamAssassin Mail Filter Daemon: [5532] warn: server socket setup failed, retry 1: spamd: could not create INET socket on 127.0.0.1:783: Address already in use
[5532] warn: server socket setup failed, retry 2: spamd: could not create INET socket on 127.0.0.1:783: Address already in use
[5532] error: spamd: could not create INET socket on 127.0.0.1:783: Address already in use
spamd: could not create INET socket on 127.0.0.1:783: Address already in use

I can resolve this problem by uninstalling SPAMASSASSIN and SPAMC and reinstalling them over again.  However if I have to reboot my machine for any reason SPAMASSASSIN doesn't start back up.  When I try to start it manually I get the error message above.

Here is how SPAMASSASSIN is set up:

I created a specific user and group for SPAMASSASSIN:

> #groupadd -g 5001 spamd
#useradd -u 5001 -g spamd -s /sbin/nologin -d /var/lib/spamassassin spamd
#mkdir /var/lib/spamassassin
#chown spamd:spamd /var/lib/spamassassin 

Changes made to /etc/default/spamassassin:

> ENABLED=1
SAHOME="/var/lib/spamassassin/"
OPTIONS="--create-prefs --max-children 5 --username spamd --helper-home-dir ${SAHOME} -s ${SAHOME}spamd.log"
PIDFILE="${SAHOME}spamd.pid"

Changes made to /etc/spamassassin/local.cf:

> rewrite_header Subject [***** SPAM _SCORE_ *****]
required_score           2.0
#to be able to use _SCORE_ we need report_safe set to 0
#If this option is set to 0, incoming spam is only modified by adding some "X-Spam-" headers and no changes will be made to the body.
report_safe     0

# Enable the Bayes system
use_bayes               1
use_bayes_rules         1
# Enable Bayes auto-learning
bayes_auto_learn        1

And finally complete copies of:

/etc/default/spamassassin

> # /etc/default/spamassassin
# Duncan Findlay

# WARNING: please read README.spamd before using.
# There may be security risks.

# Change to one to enable spamd
ENABLED=1

# Options
# See man spamd for possible options. The -d option is automatically added.

# SpamAssassin uses a preforking model, so be careful! You need to
# make sure --max-children is not set to anything higher than 5,
# unless you know what you're doing.

OPTIONS="--create-prefs --max-children 5 --username spamd --helper-home-dir ${SAHOME} -s ${SAHOME}spamd.log"

# Pid file
# Where should spamd write its PID to file? If you use the -u or
# --username option above, this needs to be writable by that user.
# Otherwise, the init script will not be able to shut spamd down.
PIDFILE="${SAHOME}spamd.pid"

# Set nice level of spamd
#NICE="--nicelevel 15"

# Cronjob
# Set to anything but 0 to enable the cron job to automatically update
# spamassassin's rules on a nightly basis
CRON=0



And /etc/spamassassin/local.cf

> # This is the right place to customize your installation of SpamAssassin.
#
# See 'perldoc Mail::SpamAssassin::Conf' for details of what can be
# tweaked.
#
# Only a small subset of options are listed below
#
###########################################################################

#   Add *****SPAM***** to the Subject header of spam e-mails
#
# rewrite_header Subject *****SPAM*****
rewrite_header Subject [***** SPAM _SCORE_ *****]

#   Save spam messages as a message/rfc822 MIME attachment instead of
#   modifying the original message (0: off, 2: use text/plain instead)
#
report_safe 0


#   Set which networks or hosts are considered 'trusted' by your mail
#   server (i.e. not spammers)
#
# trusted_networks 212.17.35.


#   Set file-locking method (flock is not safe over NFS, but is faster)
#
# lock_method flock


#   Set the threshold at which a message is considered spam (default: 5.0)
#
required_score 2.0


#   Use Bayesian classifier (default: 1)
#
use_bayes 1


#   Bayesian classifier auto-learning (default: 1)
#
bayes_auto_learn 1


#   Set headers which may provide inappropriate cues to the Bayesian
#   classifier
#
# bayes_ignore_header X-Bogosity
# bayes_ignore_header X-Spam-Flag
# bayes_ignore_header X-Spam-Status


Spamd runs as long as I don't restart the machine.  However if I have to restart then I have to uninstall SPAMASSASSIN, SPAMC, and install them over again to get Spamd to work without the error mentioned at the top of this post.

Any suggestions you might have would be greatly appreciated!

Regards,

Bill KJ6EO

---

### Post by danwood76 on 2008-05-15
Are you sure its not running on startup?
That would explain the port being in use on startup.
Check your running processes for it.

---

### Post by kj6eo on 2008-05-17
danwood76 -

Yes this was something that I was suspecting to.  Also it looks like both postfix and postgrey are trying to be started twice.  Here is a snip from /var/log/mail.warn:

> May 17 08:43:45 ub postfix/postfix-script[5532]: fatal: the Postfix mail system is already running
May 17 08:44:03 ub postgrey[5536]: 2008/05/17-08:44:03 Pid_file already exists for running process (4566)... aborting    at line 298 in file /usr/share/perl5/Net/Server.pm 

I haven't wrote any scripts of my own to start Postfix or Postgrey.  And I haven't put anything in "rc.local" to start them.

I guess the main question now is to figure out where each of them are started and where the "double" start up commands are being issued from.

I installed both of these packages with "apt-get install" so I have no idea why they both would try to be started twice.

Any suggestions?

Regards,

KJ6EO

---

