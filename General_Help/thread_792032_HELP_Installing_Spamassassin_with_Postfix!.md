---
title: "HELP: Installing Spamassassin with Postfix!"
date: 2008-05-12
forum: General Help
---

### Post by kj6eo on 2008-05-12
Hello All and thank you for reading my post!  I'm having trouble getting Spamassassin working with Postfix.  I installed Spamassassin and spamc via the following:

> $sudo apt-get install spamassassin spamc

I then created a specific user and group for spamassassin:

> groupadd -g 5001 spamd
useradd -u 5001 -g spamd -s /sbin/nologin -d /var/lib/spamassassin spamd
mkdir /var/lib/spamassassin
chown spamd:spamd /var/lib/spamassassin 

Changed some settings in /etc/default/spamassassin:

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

# Enable or disable network checks
skip_rbl_checks         0
use_razor2              0
use_dcc                 0
use_pyzor               0

Now start Spamassassin:

> /etc/init.d/spamassassin start

Now make Posfix Call Spamassassin (edit /etc/postfix/master.cf):

Change:

> smtp      inet  n       -       -       -       -       smtp


To:

> smtp      inet  n       -       -       -       -       smtpd
        -o content_filter=spamassassin

Then add the following at the end of /etc/postfix/master.cf):

> smtp      inet  n       -       -       -       -       smtpd
        -o content_filter=spamassassin

Then:

> /etc/init.d/postfix reload


IN CLOSING:

After reloading Postfix it no longer responds (not running).  If I "telnet localhost 25" the connection is rejected because Postfix isn't running.  I must be making a mistake here somewhere but I haven't found the answer to the problem yet.

Any guidance you might supply would be greatly appreciated!

Regards,

Bill - KJ6EO

---

### Post by Monicker on 2008-05-12
It looks like you told Postfix to use a content filter, but did not actually define the content filter itself.

Have a look here:

[http://www.debuntu.org/postfix-and-pamassassin-how-to-filter-spam-p2]("http://www.debuntu.org/postfix-and-pamassassin-how-to-filter-spam-p2")

---

### Post by kj6eo on 2008-05-12
Hello and thanks for your suggestion -

Looks like it's working now!  I uninstalled then reinstalled and did the HOWTO again.  This time I copied and pasted all the changes right into the corresponding files.  I must have been making a syntax error somewhere.

Your expert advice is always appreciated!

Regards,

Bill - KJ6EO

---

