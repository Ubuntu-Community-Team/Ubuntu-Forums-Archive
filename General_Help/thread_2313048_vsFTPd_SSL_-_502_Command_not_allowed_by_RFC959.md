---
title: "vsFTPd SSL - 502 Command not allowed by RFC959"
date: 2016-02-09
forum: General Help
---

### Post by commifreak2 on 2016-02-09
Hi :)

I try to teach our vsftpd ssl/tls.

Config:

```
ssl_enable=YES

force_local_logins_ssl=YES
force_local_data_ssl=YES
allow_anon_ssl=NO

ssl_sslv2=NO
ssl_sslv3=No
ssl_tlsv1=YES

require_ssl_reuse=NO

#ssl_ciphers=HIGH

# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/vsftpd/vsftpd.pem

# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/vsftpd/vsftpd.key
```

restarted and got this if I try to connect via Filezilla:

```
Status:    Verbinde mit 192.168.205.69:21...
Status:    Verbindung hergestellt, warte auf Willkommensnachricht...
Antwort:    220 (vsFTPd 3.0.2)
Befehl:    AUTH TLS
Antwort:    502 Command not allowed by RFC959
Befehl:    AUTH SSL
Antwort:    502 Command not allowed by RFC959


```

Whats wrong with vsftpd? Why does it not allow AUTH SSL/TLS commands?

System is Ubuntu Server 14.04.3 amd64

Package detail:
```
ii  vsftpd     3.0.2-1ubuntu2.14.04.1      amd64
```

Would be great if someone could give me a hint ;)

Thanks in advance! :D

---

### Post by commifreak2 on 2016-03-16
Problem is still there - no one who configured vsftpd with ssl/tls?

---

