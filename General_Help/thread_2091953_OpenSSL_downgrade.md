---
title: "OpenSSL downgrade"
date: 2012-12-06
forum: General Help
---

### Post by Featalene on 2012-12-06
I'm running 12.04 with the current version of SSL. I am having issues validating the credentials from some websites I am monitoring with Zabbix. Zabbix uses the curl library which in tern uses the OpenSSL library. After some research I found the issue is a problem in OpenSSL 1.0.1. The suggestion is to downgrade to OpenSSL 1.0.0. 

How do I do that? 

It looks to me that there is not a version of OpenSSL 1.0.0 for Precise. I would prefer not to install from source. I'm hoping there will be a fix for OpenSSL 1.0.1 soon and I don't want to be here asking the right way to switch back from source to package but.....

---

