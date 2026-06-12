---
title: "cipher suites enabled even though disabled in ssl.conf"
date: 2018-03-20
forum: General Help
---

### Post by ImIntoTech on 2018-03-20
Hi smart people,

I don't know if this is the right forum to post this problem in. If not, please guide me to the right one.


I need to disable RC4 in SSL. I've done this many times before with success by disabling the cipher suite in /etc/apache2/mods-available/ssl.conf.

For some reason, doing this on a new server is ignored completely after restarting the apache2 service. When running 'openssl ciphers' command, RC4 cipher suites are displayed even though disabled in ssl.conf. Nothing changes after disabling the cipher suites in the configuration file :mad:

Does anyone know why?

---

### Post by HermanAB on 2018-03-21
Do you use this line?

```

SSLCipherSuite ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:EECDH+ECDSA+AESGCM:EECDH+aRSA+AESGCM:EECDH+ECDSA+SHA256:EECDH+aRSA+SHA256:EECDH+ECDSA+SHA384:EECDH+ECDSA+SHA256:EECDH+aRSA+SHA384:EDH+aRSA+AESGCM:EDH+aRSA+SHA256:EDH+aRSA:EECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA:!ECDHE-RSA-DES-CBC3-SHA:!DHE-RSA-AES256-SHA:!ECDHE-RSA-AES256-SHA:!DHE-RSA-AES256-SHA:!DHE-RSA-CAMELLIA256-SHA:!DHE-RSA-AES128-SHA:!DHE-RSA-SEED-SHA:!DHE-RSA-CAMELLIA128-SHA:!ECDHE-RSA-AES128-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH

```

I suspect that any typo or invalid character in there somewhere may break it.

It is also possible that you have more than one ssl.conf and Apache is not using the one you think it is.

---

### Post by ImIntoTech on 2018-03-21
> **HermanAB said:**
> Do you use this line?

```

SSLCipherSuite ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:EECDH+ECDSA+AESGCM:EECDH+aRSA+AESGCM:EECDH+ECDSA+SHA256:EECDH+aRSA+SHA256:EECDH+ECDSA+SHA384:EECDH+ECDSA+SHA256:EECDH+aRSA+SHA384:EDH+aRSA+AESGCM:EDH+aRSA+SHA256:EDH+aRSA:EECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA:!ECDHE-RSA-DES-CBC3-SHA:!DHE-RSA-AES256-SHA:!ECDHE-RSA-AES256-SHA:!DHE-RSA-AES256-SHA:!DHE-RSA-CAMELLIA256-SHA:!DHE-RSA-AES128-SHA:!DHE-RSA-SEED-SHA:!DHE-RSA-CAMELLIA128-SHA:!ECDHE-RSA-AES128-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH

```

I suspect that any typo or invalid character in there somewhere may break it.

It is also possible that you have more than one ssl.conf and Apache is not using the one you think it is.

I have copied a ssl.conf from a working server, and the problem persist. I use this config in the file (but it makes no difference what I type - openssl ignores it completely):
```
SSLCipherSuite ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:!DSS
        SSLHonorCipherOrder on
```
Also, I have only one ssl.conf on my server (the other one is a link), so I guess I only have one Apache (sudo find / -iname ssl.conf):
```
/etc/apache2/mods-enabled/ssl.conf
/etc/apache2/mods-available/ssl.conf
```

---

### Post by Holger_Gehrke on 2018-03-21
Why should the openssl program use the configuration of the Apache ssl-module ? They may use the same library but should otherwise be completely independent of each other. If the library can use the cyphers, openssl will show them as available, whether or not you tell Apache not to use them.

You can use openssl with the 's_client' command , the '-connect' option and the '-cipher' option to connect to Apache using the ciphers you want it to reject. If openssl can't connect unless you tell it to use one of the ciphers you've allowed Apache to use, then your configuration is okay.

Holger

---

### Post by ImIntoTech on 2018-03-21
> **Holger_Gehrke said:**
> Why should the openssl program use the configuration of the Apache ssl-module ? They may use the same library but should otherwise be completely independent of each other. If the library can use the cyphers, openssl will show them as available, whether or not you tell Apache not to use them.

You can use openssl with the 's_client' command , the '-connect' option and the '-cipher' option to connect to Apache using the ciphers you want it to reject. If openssl can't connect unless you tell it to use one of the ciphers you've allowed Apache to use, then your configuration is okay.

Holger

Hi Holger,

Thanks.

My issues is actually based on a vulnerability scan of the server saying that medium strength ciphers are supported. In the past I've solved this by changing the Apache config to not support weak ciphers, but this does not seem to work in this case.

Do you know of a way to make openssl NOT support weak ciphers?

Vulnerability reported by scanner:

"
**Description**

[FONT=inherit]The remote host supports the use of SSL ciphers that offer medium strength encryption. Nessus regards medium strength as any encryption that uses key lengths at least 64 bits and less than 112 bits, or else that uses the 3DES encryption suite.
Note that it is considerably easier to circumvent medium strength encryption if the attacker is on the same physical network.[/FONT]

**Solution**

[FONT=inherit]Reconfigure the affected application if possible to avoid use of medium strength ciphers.
```

Here is the list of medium strength SSL ciphers supported by the remote server :

  Medium Strength Ciphers (> 64-bit and < 112-bit key, or 3DES)

    EDH-RSA-DES-CBC3-SHA         Kx=DH          Au=RSA      Enc=3DES-CBC(168)        Mac=SHA1   
    ADH-DES-CBC3-SHA             Kx=DH          Au=None     Enc=3DES-CBC(168)        Mac=SHA1   
    ECDHE-RSA-DES-CBC3-SHA       Kx=ECDH        Au=RSA      Enc=3DES-CBC(168)        Mac=SHA1   
    AECDH-DES-CBC3-SHA           Kx=ECDH        Au=None     Enc=3DES-CBC(168)        Mac=SHA1   
    DES-CBC3-SHA                 Kx=RSA         Au=RSA      Enc=3DES-CBC(168)        Mac=SHA1   

The fields above are :

  {OpenSSL ciphername}
  Kx={key exchange}
  Au={authentication}
  Enc={symmetric encryption method}
  Mac={message authentication code}
  {export flag}

```"

[/FONT]

---

