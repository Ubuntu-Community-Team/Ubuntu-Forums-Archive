---
title: "Sending email with MUTT"
date: 2020-11-26
forum: General Help
---

### Post by Superdude_123 on 2020-11-26
I'm following the mutt configuration that's listed [HTML]https://medium.com/@mritunjaysharma394/how-to-set-up-mutt-text-based-mail-client-with-gmail-993ae40b0003[/HTML] and it seems that the imap side of the configuration is working, but the smtp side is not. 

When I try to send an email, I get a the SMTP error ```
SMTP session failed: 501 5.5.4 https://support.google.com/mail/?p=helo
```. Is there something I am doing wrong in the SMTP configuration or missing?

muttrc file:

```
# ================  IMAP ====================
set imap_user = yourusername@gmail.com
set imap_pass = yourpassword
set spoolfile = imaps://imap.gmail.com/INBOX
set folder = imaps://imap.gmail.com/
set record="imaps://imap.gmail.com/[Gmail]/Sent Mail"
set postponed="imaps://imap.gmail.com/[Gmail]/Drafts"
set mbox="imaps://imap.gmail.com/[Gmail]/All Mail"
set header_cache = "~/.mutt/cache/headers"
set message_cachedir = "~/.mutt/cache/bodies"
set certificate_file = "~/.mutt/certificates"
# ================  SMTP  ====================
set smtp_url = "smtp://yourusername@smtp.gmail.com:587/"
set smtp_pass = $imap_pass
set ssl_force_tls = yes # Require encrypted connection
# ================  Composition  ====================
set editor = "vim"      # Set your favourite editor.
set edit_headers = yes  # See the headers when editing
set charset = UTF-8     # value of $LANG; also fallback for send_charset
# Sender, email address, and sign-off line must match
unset use_domain        # because joe@localhost is just embarrassing
set realname = "Your Name"
set from = "yourusername@gmail.com"
set use_from = yes
```

---

### Post by Superdude_123 on 2020-11-26
So the resolution to this for anyone in the future is to set a set hostname="gmail.com" at the bottom.

Also, I had to make sure that my postfix configurations were updated and I followed this guide:
[https://help.skysilk.com/support/solutions/articles/9000151194-how-to-use-postfix-to-send-outbound-email-as-gmail-relay](https://help.skysilk.com/support/solutions/articles/9000151194-how-to-use-postfix-to-send-outbound-email-as-gmail-relay)

---

