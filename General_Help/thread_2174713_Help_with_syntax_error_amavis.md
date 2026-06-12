---
title: "Help with syntax error amavis"
date: 2013-09-15
forum: General Help
---

### Post by russ2 on 2013-09-15
Hi guys,

I am trying to set up a new server using a tutorial found on this site  and I am having an issue with spamassassin and amavis.  The tutorial  that I am using is located here: [http://www.howtoforge.com/virtual-us...untu-12.04-lts]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts")

In the tutorial it gives some information and reads as follows:

> First we must enable ClamAV and SpamAssassin in  /etc/amavis/conf.d/15-content_filter_mode by uncommenting the  @bypass_virus_checks_maps and the @bypass_spam_checks_maps lines:

vi /etc/amavis/conf.d/15-content_filter_mode

The file should look like this:

use strict;

# You can modify this file to re-enable SPAM checking through spamassassin
# and to re-enable antivirus checking.

#
# Default antivirus checking mode
# Please note, that anti-virus checking is DISABLED by
# default.
# If You wish to enable it, please uncomment the following lines:


@bypass_virus_checks_maps = (
   \%bypass_virus_checks, \@bypass_virus_checks_acl, \$bypass_virus_checks_re);


#
# Default SPAM checking mode
# Please note, that anti-spam checking is DISABLED by
# default.
# If You wish to enable it, please uncomment the following lines:


@bypass_spam_checks_maps = (
   \%bypass_spam_checks, \@bypass_spam_checks_acl, \$bypass_spam_checks_re);

1;  # ensure a defined return

And then you should take a look at the spam settings and the actions for  spam-/virus-mails in /etc/amavis/conf.d/20-debian_defaults. There's no  need to change anything if the default settings are ok for you. The file  contains many explanations so there's no need to explain the settings  here:

vi /etc/amavis/conf.d/20-debian_defaults

[...]
$QUARANTINEDIR = "$MYHOME/virusmails";
$quarantine_subdir_levels = 1; # enable quarantine dir hashing

$log_recip_templ = undef;    # disable by-recipient level-0 log entries
$DO_SYSLOG = 1;              # log via syslogd (preferred)
$syslog_ident = 'amavis';    # syslog ident tag, prepended to all messages
$syslog_facility = 'mail';
$syslog_priority = 'debug';  # switch to info to drop debug output, etc

$enable_db = 1;              # enable use of BerkeleyDB/libdb (SNMP and nanny)
$enable_global_cache = 1;    # enable use of libdb-based cache if $enable_db=1

$inet_socket_port = 10024;   # default listening socket

$sa_spam_subject_tag = '***SPAM*** ';
$sa_tag_level_deflt  = 2.0;  # add spam info headers if at, or above that level
$sa_tag2_level_deflt = 6.31; # add 'spam detected' headers at that level
$sa_kill_level_deflt = 6.31; # triggers spam evasive actions
$sa_dsn_cutoff_level = 10;   # spam level beyond which a DSN is not sent
[...]
$final_virus_destiny      = D_DISCARD;  # (data not lost, see virus quarantine)
$final_banned_destiny     = D_BOUNCE;   # D_REJECT when front-end MTA
$final_spam_destiny       = D_BOUNCE;
$final_bad_header_destiny = D_PASS;     # False-positive prone (for spam)
[...]

Finally, edit /etc/amavis/conf.d/50-user and add the line $pax='pax'; in the middle:

vi /etc/amavis/conf.d/50-user

use strict;

#
# Place your configuration directives here.  They will override those in
# earlier files.
#
# See /usr/share/doc/amavisd-new/ for documentation and examples of
# the directives you can use in this file
#
$pax='pax';

#------------ Do not modify anything below this line -------------
1;  # ensure a defined return

Afterwards, run these commands to add the clamav user to the amavis group and to restart amavisd-new and ClamAV:

adduser clamav amavis
/etc/init.d/amavis restart
/etc/init.d/clamav-freshclam restart
/etc/init.d/clamav-daemon restart 			 		 

When I attempt to restart using /etc/init.d/amavis restart, I get this error:

> Starting amavisd: Error in config file  "/etc/amavis/conf.d/15-content_filter_mode": syntax error at  /etc/amavis/conf.d/15-content_filter_mode line 27, near "1;" (failed). 

I cannot figure out what the syntax should be since all of the other  files within /etc/init.d/conf.d/... have the same ending of "1;".

Any ideas you guys may have would be appreciated.

---

### Post by steeldriver on 2013-09-15
Did you use vi to edit the /etc/amavis/conf.d/15-content_filter_mode file? if so (and you're unfamiliar with vi) it's possible you unintentionally added some extra characters to that file - if you need help figuring it out, then run

```
cat -net /etc/amavis/conf.d/15-content_filter_mode
```

and post the result here between [CODE]...[&#8725;CODE] tags

---

### Post by russ2 on 2013-09-15
No I did not use vi, I used nano to edit the file.  As I understood it vi and nano will both edit files the same.

here is the code:

> 1 use strict;$
2 $
3 # You can modify this file to re-enable SPAM checking through spammassassin$
4 # and to re-enable antivirus checking.$
5 $
 6  #$                                                                            
7  # Default antivirus checking mode$                                            
8  # Please note, that anti-virus checking is DISABLED by $ 
                     9  # default.$                                                                  
10  # If You wish to enable it, please uncomment the following lines:$           
11  $ 
12  $                                                                            
13  @bypass_virus_checks_maps = ($                                               
14  #   \%bypass_virus_checks, \@bypass_virus_checks_acl, \$bypass_virus_che cks_re);$                                                                            
15  $                                                                            
16  $                                                                            
17  #$                                                                           
18  # Default SPAM checking mode$                                                
19  # Please note, that anti-spam checking is DISABLED by $ 
                     20  # default.$ 
                                                                 21  # If You wish to enable it, please uncomment the following lines:$           
22  $ 
                                                                           23  $ 
                                                                           24  @bypass_spam_checks_maps = ($ 
                                               25  #   \%bypass_spam_checks, \@bypass_spam_checks_acl, \$bypass_spam_checks _re);$                                                                               
26  $ 
                                                                           27  1; # ensure a defined return$

---

### Post by steeldriver on 2013-09-15
it looks like you only uncommented the first lines of the @bypass_virus_checks_maps and @bypass_spam_checks_maps instructions

```

13  @bypass_virus_checks_maps = ($                                               
14  [COLOR=#ff0000]**#**[/COLOR]   \%bypass_virus_checks, \@bypass_virus_checks_acl,  \$bypass_virus_che cks_re);$                                                                             

```

```

24  @bypass_spam_checks_maps = ($ 
25  [COLOR=#ff0000]**#**[/COLOR]    \%bypass_spam_checks, \@bypass_spam_checks_acl, \$bypass_spam_checks  _re);$                                                                                

```

---

### Post by russ2 on 2013-09-15
You my friend were a great help.  I appreciate your very quick reply.  That was the answer.

---

