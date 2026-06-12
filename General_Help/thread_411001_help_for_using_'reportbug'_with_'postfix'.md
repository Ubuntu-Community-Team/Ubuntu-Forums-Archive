---
title: "help for using 'reportbug' with 'postfix'"
date: 2007-04-16
forum: General Help
---

### Post by ShirishAg75 on 2007-04-16
Hi guys,
     I want to set up so I can send bugs to debian.org (wish-list and usability bugs) for some of their packages. For an e.g. report bug itself :) . Now after installing reportbug, it drops to using editor & after the report is done it needs to send it. I do not wish to install an e-mail client as I am ok with reading mail on the net itself. 

Talking with people on irc.debian.org I came to know I need an MTA. The popular or only choices I came to know are sendmail & postfix with postfix supposedly the easy one to set which atleast for a newbie I would not recommend. [OT] (supposed to be something used by enterprises to send mail from workstation > mail server > outside network/internet & vice-versa with some authentication stuff). [/OT] But as my needs are simple , there should have been a better way. Anyway while installing postfix I came 
upon the config. screen. which asks the following questions :-

1. > General type of Configuration[LIST]
[*]No Configuration
[*]Internet Site
[*]Internet with smarthost
[*]Satellite System (checked)
[*]Local only[/LIST]( Action taken ) Satellite system  from people on IRC as I was not going to receive any messages on the system. 

2. Then it asks 

 > The user root (and any other users with a uid of 0) must have mail    
 redirected via an alias, or their mail may be delivered to        /var/mail/nobody.  This is by design:  mail is not delivered to external   
delivery agents as root.                                               
   
  If you already have a /etc/aliases file, then you may need to add this   
 entry.  (The entry will only be added if the file /etc/aliases is created.)   
 
  What address should be added to /etc/aliases, if the file is created?   
 (Leave this blank to not add one.)                                  

 Where should mail for root go? 

(Action taken) kept blank as I don't want to receive any mails. 

3. Then it asks for a mail name. 

  > Your `mail name' is the hostname portion of the address to be shown on  outgoing news and mail messages (following the username and @ sign). 

  This name will be used by other programs besides Postfix; it should be the single, full domain name (FQDN) from which mail will appear to originate.   

 Mail name? 

  (Action taken) shirish@

4. > Specify a domain, host, host : port, [address] or [address] : port. Use the form [destination] to turn off MX lookups.  Leave this blank for no relay host.
  
 The relayhost parameter specifies the default host to send mail to when  
no entry is matched in the optional transport(5) table. When no             
relayhost is given, mail is routed directly to the destination.     
   
  SMTP relay host? (blank for none)   

  (Action taken) kept blank (but perhaps something should be here) .[/QUOTE]

5.  > Give a comma-separated list of domains that this machine should consider itself the final destination for.  If this is a mail domain gateway, you  probably want to include the top-level domain.     

 Other destinations to accept mail for? (blank for none) 

 (Action taken) kept blank ( Again no idea here, perhaps something should be here). 

6.  > If synchronous updates are forced (yes), then mail is processed more  slowly. If not forced (no), then there is a remote chance of losing some mail if the system crashes at an inopportune time, and you are not using a journaled filesystem (such as ext3).  The default is  "no". 

Force synchronous updates on mail queue? 

Yes                No 

(Choice used)  No.  Guessing this is for both send as well as receive ( I don't want to receive mail here but at gmail.com) . Also have ext3 .

7.>   For what network blocks should this machine relay mail?  The default is  
 just the local host, which is needed by some mail user agents. 

If this is a smarthost for a block of machines, you need to specify the netblocks here, or mail will be rejected rather than relayed.  

To use the postfix default (which is based on connected networks), enter an empty  string.    

 Local networks?   

(Choice used) 127.0.0.0/8 that is what it gave by default hence used that. No idea.

8.  > What limit should Postfix place on mailbox files to prevent runaway   software errors.  A value of zero (0) means no limit.  (The upstream  default is 51200000.)     
   
   Mailbox size limit 

(Choice used) 0 . Doesn't matter I think. 

9.  > What character defines a local address extension? 

To not use address extensions, leave the string blank.    

 Local address extension character?

 (Choice used) blank although there was (-) minus sign there  no idea.

10. >   By default, whichever internet protocols are enabled on the system at     installation time will be used.  You may override this default with any  of the following:                                 
   
 all - use both ipv4 and ipv6 addresses                   
                                                                             
 ipv6 - listen only on ipv6 addresses                  
                                                                          
 ipv4 - listen only on ipv4 addresses                                
                                                                 
 Internet protocols to use?                                           
                                                                            
                                    all                                    
                                   ipv6                                     
                                   ipv4                                    
                                           
Choice used (ipv4)

After doing that it asks to do a```
 /etc/init.d/postfix
``` reload I guess to take the new settings. Dutifully do that. So for better or lesser postfix is configured till what I know now.

   Then running reportbug again, filling in everything & asking it to send the mail it gives this error. 

```
Connecting to bugs.debian.org via SMTP...
SMTP send failure: {'ubuntu-users@lists.ubuntu.com': (550, 'relay not permitted')}
``` 

Please guide me where am I going wrong?

---

### Post by ShirishAg75 on 2007-04-16
Giving below the the three configuration files namely :-

/etc/postfix/main.cf.

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ubuntu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = 
relayhost = 
mailbox_size_limit = 0
recipient_delimiter = 
inet_interfaces = loopback-only
inet_protocols = ipv4
mynetworks = 127.0.0.0/8

```

/etc/reportbug.conf

```
# Example configuration file for reportbug(1)
# Options can be specified in any order
# usually, no-OPTION will disable OPTION if OPTION is boolean

# Default severity level; will bypass prompt in reportbug, so disabled
# severity normal

# BTS to use
bts ubuntu
# See 'reportbug --bts help' for a current list of supported BTSes

# Submission address: default is 'submit'
submit
# Can also be 'quiet' or 'maintonly'; see --report-quiet and --maintonly
# entries on man page

# Mailer to use (default is empty, to use internal mailer). One of:
# mutt
# af
# mh
# nmh

# You can also use 'mua'; it takes an argument like that to --mua
# mua 'mutt -H'

# Additional headers to add:
# header "X-Debbugs-CC: debian-qa@lists.debian.org"
# header "X-Silly-Header: I haven't edited my /etc/reportbug.conf"
# header "X-Debbugs-No-Ack: please" # to suppress acknowledgments

# The following boolean options can be disabled by adding 'no-'
# Should I query the BTS?
query-bts

# Should I CC the reporter?
cc

# Should I ever include modified config files?
config-files

# Should I strip down modified config files?
compress

# Specify one of the following to digitally sign bug reports automatically.
# sign gpg
# sign pgp

# Default "from" email address and real name (override with env. vars.)
# email "humberto@example.com"
# realname "Humberto Flores III"

# Default REPLYTO (override with env. variables)
# replyto "Humberto Flores <humflores@example.org>"

# Default HTTP Proxy (override with the env. variable)
# http_proxy http://proxy.example.com:3128/

# Use this to enable the internal MTA (bypassing /usr/sbin/sendmail)
# smtphost localhost
#
# You can also specify a port other than 25
# smtphost mail.example.com:2525

# Username and password for SMTP
# smtpuser bob
# smtppasswd XXX

# Use TLS encryption.
# smtptls

# Use this to specify the path of your MTA; any SMTP server on Debian
# should be OK with the default.
# mta /usr/sbin/sendmail

# User interface: text or newt
# querybts and reportbug will use this setting
# ui text

# Editor
# editor "emacs -nw"

# Always use template mode (bypass all prompts, output to stdout)
# template

# Don't query source packages
# no-query-source

# Disable debconf-show output
# no-debconf

# Automatically verify package installation before reporting using
# debsums, if available
verify

# Disable all external queries
# offline

# Default operating mode (novice, standard, advanced, expert)
# mode novice

# Don't check whether user IDs are outside admin range - root is still checked
# no-check-uid
```

~/,reportbugrc

```
# reportbug preferences file
# character encoding: UTF-8
# Version of reportbug this preferences file was written by
reportbug_version "3.31ubuntu1"
# default operating mode: one of: novice, standard, advanced, expert
mode novice
# default user interface
ui urwid
# offline setting - comment out to be online
#offline
# name and email setting (if non-default)
# realname "shirish"
email "shirishag75@gmail.com"
# Disable fallback mode by commenting out the following:
no-cc
header "X-Debbugs-CC: shirishag75@gmail.com"
smtphost bugs.debian.org
# You can add other settings after this line.  See
# /etc/reportbug.conf for a full listing of options.
```

 Hopefully can help me set things right & also learn with this process. Thanx for your all patience all :)

---

