---
title: "Enable curl sftp"
date: 2014-12-17
forum: General Help
---

### Post by guillaume9 on 2014-12-17
Hi,


Enable sftp protocol dont work for curl.
I have compile with :

```
./configure --with-libssh2=/usr/local
make
make install
```

When i do ./configure i have :

```
  curl version:     7.39.0
  Host setup:       x86_64-unknown-linux-gnu
  Install prefix:   /usr/local
  Compiler:         gcc
  SSL support:      enabled (OpenSSL)
  SSH support:      enabled (libSSH2)
  zlib support:     enabled
  GSS-API support:  no      (--with-gssapi)
  TLS-SRP support:  enabled
  resolver:         default (--enable-ares / --enable-threaded-resolver)
  ipv6 support:     enabled
  IDN support:      enabled
  Build libcurl:    Shared=yes, Static=yes
  Built-in manual:  enabled
  --libcurl option: enabled (--disable-libcurl-option)
  Verbose errors:   enabled (--disable-verbose)
  SSPI support:     no      (--enable-sspi)
  ca cert bundle:   /etc/ssl/certs/ca-certificates.crt
  ca cert path:     no
  LDAP support:     enabled (OpenLDAP)
  LDAPS support:    enabled
  RTSP support:     enabled
  RTMP support:     enabled (librtmp)
  metalink support: no      (--with-libmetalink)
  HTTP2 support:    disabled (--with-nghttp2)
  Protocols:        DICT FILE FTP FTPS GOPHER HTTP HTTPS IMAP IMAPS LDAP LDAPS POP3 POP3S RTMP RTSP SCP **SFTP** SMTP SMTPS TELNET TFTP

```

and curl -V :

```
curl 7.39.0 (x86_64-unknown-linux-gnu) libcurl/7.35.0 OpenSSL/1.0.1f zlib/1.2.8 libidn/1.28 librtmp/2.3
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp smtp smtps telnet tftp 
Features: AsynchDNS IDN IPv6 Largefile NTLM NTLM_WB SSL libz TLS-SRP 

```

If you have suggest... Thank you !

---

### Post by nerdtron on 2014-12-17
What are you trying to achieve? Can you elaborate so we can think if there are better alternatives.

---

### Post by guillaume9 on 2014-12-18
thank you for your reply.
I try to use git-ftp on my server (i have only sftp on it), but for this i need curl with sftp enable.

---

