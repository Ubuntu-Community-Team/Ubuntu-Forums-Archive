---
title: "Segfault in pthreads by php process, then computer freeze"
date: 2017-03-11
forum: General Help
---

### Post by flight89 on 2017-03-11
Dear all,
I am having an issue with Ubuntu 16.04 LTS based computers. About the setup: we are running a local lighttpd with php7 installed to serve content to a local browser to run a web-application even when the computer is offline in a remote location.

However, we are experiencing "random" freezes of the systems. The last time I encountered one, I then found the following information in kern.log just before the freeze. The box was reported freezing around 18:40, but that is +/- 5 minutes accurate - I wasn't there personally.
```
Mar  8 18:37:03 ##hostname## kernel: [26485.582691] php[3689]: segfault at ffffffffffffffff ip 00007f50b4f45fc0 sp 00007ffe58a7fce8 error 7 in libpthread-2.23.so[7f50b4f3a000+18000]Mar  8 18:38:02 ##hostname## kernel: [26544.560026] php[3735]: segfault at ffffffffffffffff ip 00007f7c8633efc0 sp 00007fff27c2e468 error 7 in libpthread-2.23.so[7f7c86333000+18000]
Mar  8 18:39:03 ##hostname## kernel: [26605.805414] php7.0[3786]: segfault at ffffffffffffffff ip 00007f083119cfc0 sp 00007ffd12d0f208 error 7 in libpthread-2.23.so[7f0831191000+18000]
Mar  8 18:39:03 ##hostname## kernel: [26605.811565] php[3779]: segfault at ffffffffffffffff ip 00007f3766e2cfc0 sp 00007ffe4fc8bc58 error 7 in libpthread-2.23.so[7f3766e21000+18000]
Mar  8 18:41:15 ##hostname## kernel: [26737.728367] php[3827]: segfault at ffffffffffffffff ip 00007f055ef19fc0 sp 00007ffd9c7ddfe8 error 7 in libpthread-2.23.so[7f055ef0e000+18000]
Mar  8 18:41:15 ##hostname## kernel: [26737.728431] php[3826]: segfault at ffffffffffffffff ip 00007f91ae317fc0 sp 00007ffc729bc5f8 error 7 in libpthread-2.23.so[7f91ae30c000+18000]

```

The interesting part is that although libpthread is installed, we arent using it in any of our php code.

Any clues onto why this is happening? How can php segfault in libpthread? And why did the whole computer freeze when php failed?

I am using the following script to install and configure this part: 
```
apt-get install -y php7.0 lighttpd php7.0-cgi php7.0-cli php-apculighty-enable-mod fastcgi
lighty-enable-mod fastcgi-php
service lighttpd force-reload


cat > /etc/php/7.0/mods-available/apcu.ini << EOF
extension=apcu.so
apc.enabled=1
apc.file_update_protection=2
apc.optimization=0
apc.shm_size=64M
apc.include_once_override=0
apc.shm_segments=1
apc.gc_ttl=7200
apc.ttl=7200
apc.num_files_hint=1024
apc.enable_cli=1
EOF

service lighttpd force-reload
```

Thanks for the help!

---

