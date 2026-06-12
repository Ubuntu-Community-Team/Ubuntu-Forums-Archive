---
title: "Konqueror Woes May Be Due to Partial Install of Kubuntu"
date: 2008-01-09
forum: General Help
---

### Post by sageb1 on 2008-01-09
Konqueror has crashed about three times now.

Here is part of the .xsession-errors:

kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kio (KIOConnection): ERROR: Could not write data
kio (KIOConnection): ERROR: Could not write data
kio (KIOConnection): ERROR: Could not write data
kio (KIOConnection): ERROR: Could not write data
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
KCrash: Application 'konqueror' crashing...
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0

...Too much output, ignoring rest...
(END)                                

Specifically Konqueror complains of some parts it need being missing, see next post.

---

### Post by sageb1 on 2008-01-09
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.2/./libkonq/konq_pixmapprovider.cc (81)
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/x-activex-handler not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/x-activex-handler not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype application/x-activex-handler not found
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free

---

### Post by doorknob60 on 2008-01-09
EIther use a different browser, or try ```
sudo aptitude reinstall konqueror
```

---

### Post by sageb1 on 2008-01-09
my guess is, kde and gnome see these errors and handle them, but only a bit of it gets into .xsession-errors

for the openssl error, you have to put the path /usr/share/apps/kssl in the openssl directory window in the security menu.

the application/x-activex-handler isn't set. there isn't an appropriate handler available. so on ASP webpages, konqueror may crash.

also konqueror appears to choke when a favicon is not provided by the host.

apart from that I like konqueror.

---

### Post by sageb1 on 2008-01-24
i'm surprised no one else is experiencing konqueror errors.

in firefox, i get 100% CPU cycles occurring every 5-10 minutes; ditto for opera. at first i thought it was due to java. now i think it's probably kde interacting with gnome or xfce4.

dillo never crashes but it does not use cookies and jscript isn't enabled.

my "fix" for the 100% cpu cycles used is to quit firefox and wait 30 minutes and try again.

my "fix" for konqueror crashing is to use another browser, quit  when the cpu cycles problem happens and switch back to konqueror.  to avoid having to start my browsing from scratch i have saved my tabs in my bookmark in each browser.

---

