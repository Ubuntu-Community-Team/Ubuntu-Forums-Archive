---
title: "Apache Question"
date: 2016-03-03
forum: General Help
---

### Post by SchnappiJedi on 2016-03-03
Hi,

Using Apache Version 2.4. I realize this question might be better posted on an Apache forum but I do not feel like registering for yet another forum so will try asking here first.
Apache options like "SSLProtocol", "SSLCipherSuite", and "HonorCipherOrder" among others can be put in both /etc/apache2/apache2.conf or etc/apache2/mods-available/ssl.conf

Which location are these settings conventionally placed in and edited? Further more and more importantly if the settings conflict in these two files/ locations which setting/file takes precedence?

---

### Post by SeijiSensei on 2016-03-03
Those directives appear in mods-available/ssl.conf in my copy of Ubuntu 14.04, so I'd put any changes there.  Generally speaking you should leave apache2.conf alone.

---

### Post by SchnappiJedi on 2016-03-03
Am going to post this in the Apache forum. I edit apache2.conf alot so that I do not have to make security changes for individual virtual hosts.

---

### Post by dragonfly41 on 2016-03-03
As explained above apache2.conf *includes* the following and changes should be in the includes ...

See at bottom of apache2.conf ...
```

# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf


# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

```

If you have many virtualhosts to manage you could try installing mod_macro module.
This works well across multiple virtual hosts.

---

