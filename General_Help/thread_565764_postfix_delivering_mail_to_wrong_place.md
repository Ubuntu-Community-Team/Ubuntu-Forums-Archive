---
title: "postfix delivering mail to wrong place"
date: 2007-10-02
forum: General Help
---

### Post by Yoyko on 2007-10-02
Hello

I've set up  a email service on my server by following this [guide]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy").

Recently, my server's mail service stopped working suddenly and after going thru
the configuration and doing it from the scratch, I still have a problem.

Instead of forwarding the mail to /mail/vmail (virtual mailbox),
it get's delivered to /var/mail/<username>.

Here's the my main.cf file for postfix.

-----------------------------------------------------------

```

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
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = <cencored>.com
mydestination = <cencored>.com, localhost, localhost.localdomain
mynetworks = 127.0.0.0/8
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota"
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_ali
as_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailb
ox_domains $relay_recipient_maps $relay_domains $canonical_maps $se
nder_canonical_maps $recipient_canonical_maps $relocated_maps $tran
sport_maps $mynetworks $virtual_mailbox_limit_maps
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

```

NOTE: It' might appear that some lines that are supposed to be on one, to be on several, that is not the case. Limitation of the forum system. The lines in question are: proxy_read_maps, virtual_alias_maps and smtpd_recipient_restrictions.

I'm pretty much clueless here. :(

Any help you can offer is HIGHLY appriciated. :)

---

### Post by Yoyko on 2007-10-03
Anyone? :(

---

### Post by dcstar on 2007-10-03
> **Yoyko said:**
> Hello

I've set up  a email service on my server by following this [guide]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy").

Recently, my server's mail service stopped working suddenly and after going thru
the configuration and doing it from the scratch, I still have a problem.

Instead of forwarding the mail to /mail/vmail (virtual mailbox),
it get's delivered to /var/mail/<username>.
.........
Any help you can offer is HIGHLY appriciated. :)

Check the DNS resolution of your domains that postfix is supposed to process, and also look in your mail log files to see how things are being processed.

---

