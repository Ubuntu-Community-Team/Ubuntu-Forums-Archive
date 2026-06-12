---
title: "Multiple postfix issues"
date: 2014-05-19
forum: General Help
---

### Post by antony7 on 2014-05-19
I am having a number of problems with postfix:
  1) If I set mydestination = mydomain then I receive emails on [email]anaccount@domain.com[/email]
  2) The minute I change this to the configuration below although  [email]anaccount@domain.com[/email] is received it does not end up in my mail account
  3) If I send an email to [email]anything@domain.com[/email] I end up with an unknown user
  But running postmap successfully returns the domain and  [email]anything@domain.com[/email] is matched to [email]anaccount@domain.com[/email] with postmap - so  it *appears* to be working.
  4) I cannot send OUT through Windows Mail because of an NTLM status not sent by client
  I have tried endless things but don't seem to be fully getting there! Here is my postfix main.cf:
  smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
myhostname = mail.mydomain.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost.$mydomain
relayhost =
mynetworks = 192.168.1.0/28 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = subnet
home_mailbox = Maildir/
virtual_alias_domains =

virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-    virtual_forwardings.cf, mysql:/etc/postfix/mysql-    virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-    virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-    virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions =permit_mynetworks,     permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-    virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes

  postconf -n
  alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mailbox_command =
mailbox_size_limit = 0
mydestination = localhost.$mydomain
myhostname = mail.MYDOMAIN.co.uk
mynetworks = 192.168.1.0/28 127.0.0.0/8
mynetworks_style = subnet
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = private/auth
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000
postconf: warning: /etc/postfix/main.cf: unused parameter: virtual_overquota_bounce=yes
postconf: warning: /etc/postfix/main.cf: unused parameter: virtual_maildir_limit_message="The user you are trying to reach is over quota."
postconf: warning: /etc/postfix/main.cf: unused parameter: virtual_maildir_extended=yes
postconf: warning: /etc/postfix/main.cf: unused parameter: virtual_mailbox_limit_override=yes
  [h=1][SIZE=3]postmap that works[/SIZE][/h]  postmap -q [email]anything@MYDOMAIN.co.uk[/email] mysql:/etc/postfix/mysql-virtual_forwardings.cf
  [h=1][SIZE=3]anything@MYDOMAIN which fails from the logs[/SIZE][/h]  May 18 18:05:53 ubuntu postfix/smtpd[13623]: connect from dub0-omc3-s27.dub0.hotmail.com[157.55.2.36]
May 18 18:05:53 ubuntu postfix/smtpd[13623]: B496650047D: client=dub0-omc3-s27.dub0.hotmail.com[157.55.2.36]
May 18 18:05:53 ubuntu postfix/cleanup[13628]: B496650047D: message-id=<DUB118-W17CE9F712819209D8FE0ABEA330@phx.gbl>
May 18 18:05:53 ubuntu postfix/qmgr[11821]: B496650047D: from=<MEEE>, size=1566, nrcpt=1 (queue active)
May 18 18:05:53 ubuntu postfix/smtpd[13623]: disconnect from dub0-omc3-s27.dub0.hotmail.com[157.55.2.36]
May 18 18:05:53 ubuntu postfix/virtual[13629]: B496650047D: to=<anything@MYDOMAIN>, relay=virtual, delay=0.23, delays=0.16/0.01/0/0.06, dsn=5.1.1, status=bounced (unknown user: "anything@MYDOMAIN")
May 18 18:05:53 ubuntu postfix/cleanup[13628]: E22D3500491: message-id=<20140518170553.E22D3500491@mail.MYDOMAIN>
May 18 18:05:53 ubuntu postfix/qmgr[11821]: E22D3500491: from=<>, size=3500, nrcpt=1 (queue active)
May 18 18:05:53 ubuntu postfix/bounce[13631]: B496650047D: sender non-delivery notification: E22D3500491
May 18 18:05:53 ubuntu postfix/qmgr[11821]: B496650047D: removed
May 18 18:05:55 ubuntu postfix/smtp[13634]: E22D3500491: to=<MEEEE>, relay=mx1.hotmail.com[65.55.37.120]:25, delay=1.7, delays=0.06/0.01/0.76/0.85, dsn=2.0.0, status=sent (250  <20140518170553.E22D3500491@mail.MYDOMAIN> Queued mail for delivery)
May 18 18:05:55 ubuntu postfix/qmgr[11821]: E22D3500491: removed
  [h=1][SIZE=3]This is successful but does NOT get through to my email even though it is "received"??[/SIZE][/h]  May 18 18:08:09 ubuntu postfix/smtpd[13636]: 3B93750047D: client=dub0-omc2-s16.dub0.hotmail.com[157.55.1.155]
May 18 18:08:09 ubuntu postfix/cleanup[13640]: 3B93750047D: message-id=<DUB118-W42F503B2DD7CF476C97228EA330@phx.gbl>
May 18 18:08:09 ubuntu postfix/qmgr[11821]: 3B93750047D: from=<MEEE>, size=1594, nrcpt=1 (queue active)
May 18 18:08:09 ubuntu postfix/smtpd[13636]: disconnect from dub0-omc2-s16.dub0.hotmail.com[157.55.1.155]
May 18 18:08:09 ubuntu postfix/virtual[13641]: 3B93750047D: to=<MYEMAIL>, relay=virtual, delay=0.23, delays=0.16/0.01/0/0.06, dsn=2.0.0, status=sent (delivered to maildir)
May 18 18:08:09 ubuntu postfix/qmgr[11821]: 3B93750047D: removed
      

Thanks

  Antony

---

