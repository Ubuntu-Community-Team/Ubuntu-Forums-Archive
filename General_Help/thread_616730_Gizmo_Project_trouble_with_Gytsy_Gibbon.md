---
title: "Gizmo Project trouble with Gytsy Gibbon"
date: 2007-11-18
forum: General Help
---

### Post by 4k1r4 on 2007-11-18
Hello everyone
I used to use Gizmo on windows and now when i completely moved to Linux i have a little troubles with it.

I runing gizmo well, can call, recieve calls, send ims and so on but, when im trying to add a new contact it's quits by itself

it says
> Segmentation fault (core dumped)

or 

> 
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6ffbd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6fff800]
/usr/lib/libsipphoneapi.so.1.7.07.72(CRYPTO_free+0x29)[0xb7923c53]
/usr/lib/libsipphoneapi.so.1.7.07.72(ERR_clear_error+0x68)[0xb79485d6]
/usr/lib/libsipphoneapi.so.1.7.07.72(ssl23_connect+0x40)[0xb791273c]
/usr/lib/libsipphoneapi.so.1.7.07.72(Curl_ossl_connect+0xadc)[0xb78ec15f]
/usr/lib/libsipphoneapi.so.1.7.07.72(Curl_http_connect+0x92)[0xb78fb582]
/usr/lib/libsipphoneapi.so.1.7.07.72(Curl_protocol_connect+0x5d)[0xb78e712a]
/usr/lib/libsipphoneapi.so.1.7.07.72[0xb78e750e]
/usr/lib/libsipphoneapi.so.1.7.07.72(Curl_connect+0xd6b)[0xb78e89e7]
/usr/lib/libsipphoneapi.so.1.7.07.72[0xb78ef11e]
/usr/lib/libsipphoneapi.so.1.7.07.72(Curl_perform+0xc4)[0xb78f11a7]
/usr/lib/libsipphoneapi.so.1.7.07.72(_ZN8sipphone12SslOpsHelper16getHttpsRespons
eEPbRKSsbPKcl+0x827)[0xb74a4d03]
/usr/lib/libsipphoneapi.so.1.7.07.72(_ZN8sipphone17SIPphoneSslOpsAPI14getRawResp
onseESsPbPcPKcl+0x61)[0xb7491a0b]
/usr/lib/libsipphoneapi.so.1.7.07.72(_ZN8sipphone17SIPphoneSslOpsAPI9getRawURLEP
KcPiS2_l+0x95)[0xb749eaaf]
/usr/lib/libsipphoneapi.so.1.7.07.72(_ZN8sipphone11SipphoneXML11DownloadURLESs+0
x55)[0xb760dc5b]
/usr/lib/libsipphoneapi.so.1.7.07.72(_ZN8sipphone11SipphoneXML15DownloadBalanceE
v+0x9f)[0xb765415d]
/usr/lib/libsipphoneapi.so.1.7.07.72(sapicpp_xml_download_balance+0x3a)[0xb7684e
50]
gizmo[0x808e91e]
gizmo[0x8085107]
/usr/lib/libglib-2.0.so.0[0xb6cff5af]
/lib/tls/i686/cmov/libpthread.so.0[0xb6c9546b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb70656de]


help plz :)

---

### Post by RavanH on 2008-01-22
Hi,

Trying to install Gizmo on Gutsy AMD64, using [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to solve 32bit dependencies,  I ran into an error about this **libsipphoneapi** too ...

Have you ever found a solution? Where to find libsipphoneapi? It is not in the default Gutsy repo's :(

---

### Post by radiobuzzer on 2008-02-06
bump. Same problem here. Maybe we could submit a ticket to the Gizmo project website

---

### Post by Cappy on 2008-02-09
The "missing library" problem has been solved here: [http://ubuntuforums.org/showpost.php?p=4185776&postcount=116](http://ubuntuforums.org/showpost.php?p=4185776&postcount=116)

---

