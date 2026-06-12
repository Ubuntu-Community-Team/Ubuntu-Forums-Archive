---
title: "struggling with SASL via dovecot for authenticated SMTP"
date: 2022-07-06
forum: General Help
---

### Post by jpadie on 2022-07-06
Hi 
I'm not seeing the wood for the trees I fear. 
I am trying to extend a postfix installation with dovecot.  the imap server works ok and my messages get delivered to the mail client.
however the remote mail client cannot send email back through the server.  relaying prohibited, as you'd expect.
but the postfix config allows sasl authenticated connections.
As best I can see the server is not _requiring_ the mail client to authenticate and so it never does.  instead getting outbound mail denied (relay access denied).
I've followed countless guides but am getting nowhere.  If anyone can see where I am going wrong, I'd appreciate the pointers.
Of course all services are restarted after each change...

config follows
```
[COLOR=#000000][FONT=Menlo]
/etc/postfix/main.cf - relevant parts
[/FONT][/COLOR]
# TLS parameters
smtpd_tls_cert_file=/etc/letsencrypt/live/hannah.solutions/fullchain.pem
smtpd_tls_key_file=/etc/letsencrypt/live/hannah.solutions/privkey.pem
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


smtpd_sasl_security_options=noanonymous
smtpd_sasl_type=dovecot
smtpd_tls_security_level=may
smtpd_sasl_auth_enable=yes
smtpd_sasl_path=private/auth
smtpd_reject_unlisted_recipient=no
smtpd_recipient_restrictions=permit_sasl_authenticated,reject_non_fqdn_recipient,reject_unknown_recipient_domain,reject
smtpd_sasl_local_domain = hannah.solutions
smtpd_tls_security_level = may 
smtpd_tls_received_header = yes 
smtpd_tls_loglevel = 1 
smtpd_use_tls=yes 
smtp_tls_note_starttls_offer = yes 
smtpd_tls_session_cache_timeout = 3600s 


```
/etc/dovecot/config.d/10-auth.conf
```

auth_mechanisms = plain login
!include auth-system.conf.ext

```

/etc/dovecot/config.d/10-master.conf

```

service auth {
  unix_listener auth-userdb {
    #mode = 0666
    #user = 
    #group = 
  }


  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
    user = postfix
    group = postfix
  }
  user = root 
}

```

---

