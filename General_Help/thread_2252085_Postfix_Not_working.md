---
title: "Postfix Not working"
date: 2014-11-08
forum: General Help
---

### Post by mrkirby153 on 2014-11-08
I have been trying for the last two days to get postfix to work. It can send emails fine, but when I want to set up Mozilla Thunderbird, it always says that it can't find my credentials. I will provide any missing information upon request.

---

### Post by lisati on 2014-11-08
Are you using a helper such as Dovecot or Courier?

---

### Post by mrkirby153 on 2014-11-08
> **lisati said:**
> Are you using a helper such as Dovecot or Courier?
Yes. I am using dovecot. Trying to telnet to 143 works then the connection is immediately closed.

---

### Post by mrkirby153 on 2014-11-09
I made some progress on this issue. The telnet to 143 is still immediately closed and the log states that
```
Nov  9 00:35:16 mrkirby153 dovecot: imap-login: Fatal: Can't load ssl_cert: There is no valid PEM certificate. (You probably forgot '<' from ssl_cert=</etc/ssl/certs/mailcert.pem)Nov  9 00:35:16 mrkirby153 dovecot: master: Error: service(imap-login): command startup failed, throttling

```

My config file:
```

disable_plaintext_auth = no
mail_privileged_group = mail
mail_location = mbox:~/mail:INBOX=/var/mail/%u
userdb {
  driver = passwd
}
passdb {
  args = %s
  driver = pam
}
protocols = " imap"


protocol imap {
  mail_plugins = " autocreate"
}
plugin {
  autocreate = Trash
  autocreate2 = Sent
  autosubscribe = Trash
  autosubscribe2 = Sent
}


service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0660
    user = postfix
  }
}


ssl=required
ssl_cert = /etc/ssl/certs/mailcert.pem
ssl_key = /etc/ssl/private/mailcert.key

```

---

### Post by HereInOz on 2014-11-09
You can get a free Class one certificate from startssl.com which will cover your main domain and one subdomain (for instance mymail.net and mail.mymail.net).  It is not a completely intuitive process but it is not all that difficult.  Just generate the certificates and save them to the locations listed above and see how you go.  Make sure that you do not forget the encryption password like I did.  Makes things very difficult :-(

---

### Post by mrkirby153 on 2014-11-09
> **HereInOz said:**
> You can get a free Class one certificate from startssl.com which will cover your main domain and one subdomain (for instance mymail.net and mail.mymail.net).  It is not a completely intuitive process but it is not all that difficult.  Just generate the certificates and save them to the locations listed above and see how you go.  Make sure that you do not forget the encryption password like I did.  Makes things very difficult :-(
So, the issue is that StartSSL's validation wizard doesn't have the TLD I'm using (.tk) Is that an issue?

---

