---
title: "Problem setting up a LAMP server"
date: 2007-03-04
forum: General Help
---

### Post by mokojin on 2007-03-04
Hi all

Here`s my problem: I want to setup a LAMP server to try out some open source applications, like SugarCRM, PHPmyadmin, PHPldapadmin and Joomla, and I have installed via Synaptic apache2, php, mysql, and the required libraries.

I have placed my applications like sugarcrm and phpmyadmin in /var/www/<appname>

then started the service, when i try to get the pages via browser the result is:

```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at localhost Port 80
```

I tailed the apache error.log:

```
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] Premature end of script headers: index.php, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] SoftException in Application.cpp:193: Script "/var/www/phpmyadmin/index.php" resolving to "/usr/share/phpmyadmin/index.php" not within configured docroot, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] *** glibc detected *** /usr/lib/suphp/suphp: double free or corruption (fasttop): 0x0806fa60 ***, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] ======= Backtrace: =========, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /lib/tls/i686/cmov/libc.so.6[0xb7d3a8bd], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7d3aa44], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7eeafc1], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /usr/lib/suphp/suphp[0x804fecb], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /usr/lib/suphp/suphp[0x804ff4d], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /usr/lib/suphp/suphp[0x804ffd4], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /usr/lib/suphp/suphp[0x8050039], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /usr/lib/suphp/suphp[0x8050059], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /lib/tls/i686/cmov/libc.so.6(exit+0xe9)[0xb7d00299], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe4)[0xb7ce98d4], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] /usr/lib/suphp/suphp(__gxx_personality_v0+0xa1)[0x804a481], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] ======= Memory map: ========, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] 08048000-0806e000 r-xp 00000000 03:06 1199093    /usr/lib/suphp/suphp, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] 0806e000-0806f000 rw-p 00025000 03:06 1199093    /usr/lib/suphp/suphp, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] 0806f000-08090000 rw-p 0806f000 00:00 0          [heap], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7b00000-b7b21000 rw-p b7b00000 00:00 0 , referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7b21000-b7c00000 ---p b7b21000 00:00 0 , referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7c9f000-b7ca8000 r-xp 00000000 03:06 899623     /lib/tls/i686/cmov/libnss_files-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7ca8000-b7caa000 rw-p 00008000 03:06 899623     /lib/tls/i686/cmov/libnss_files-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7caa000-b7cb2000 r-xp 00000000 03:06 899625     /lib/tls/i686/cmov/libnss_nis-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cb2000-b7cb4000 rw-p 00007000 03:06 899625     /lib/tls/i686/cmov/libnss_nis-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cb4000-b7cc6000 r-xp 00000000 03:06 899620     /lib/tls/i686/cmov/libnsl-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cc6000-b7cc8000 rw-p 00011000 03:06 899620     /lib/tls/i686/cmov/libnsl-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cc8000-b7cca000 rw-p b7cc8000 00:00 0 , referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cca000-b7cd1000 r-xp 00000000 03:06 899621     /lib/tls/i686/cmov/libnss_compat-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cd1000-b7cd3000 rw-p 00006000 03:06 899621     /lib/tls/i686/cmov/libnss_compat-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cd3000-b7cd4000 rw-p b7cd3000 00:00 0 , referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7cd4000-b7e01000 r-xp 00000000 03:06 899614     /lib/tls/i686/cmov/libc-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e01000-b7e03000 r--p 0012c000 03:06 899614     /lib/tls/i686/cmov/libc-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e03000-b7e05000 rw-p 0012e000 03:06 899614     /lib/tls/i686/cmov/libc-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e05000-b7e09000 rw-p b7e05000 00:00 0 , referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e09000-b7e13000 r-xp 00000000 03:06 866723     /lib/libgcc_s.so.1, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e13000-b7e14000 rw-p 00009000 03:06 866723     /lib/libgcc_s.so.1, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e14000-b7e38000 r-xp 00000000 03:06 899618     /lib/tls/i686/cmov/libm-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e38000-b7e3a000 rw-p 00023000 03:06 899618     /lib/tls/i686/cmov/libm-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7e3a000-b7f0e000 r-xp 00000000 03:06 1602947    /usr/lib/libstdc++.so.6.0.8, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7f0e000-b7f11000 r--p 000d4000 03:06 1602947    /usr/lib/libstdc++.so.6.0.8, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7f11000-b7f13000 rw-p 000d7000 03:06 1602947    /usr/lib/libstdc++.so.6.0.8, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7f13000-b7f19000 rw-p b7f13000 00:00 0 , referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7f27000-b7f29000 rw-p b7f27000 00:00 0 , referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7f29000-b7f42000 r-xp 00000000 03:06 866660     /lib/ld-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] b7f42000-b7f44000 rw-p 00018000 03:06 866660     /lib/ld-2.4.so, referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] bff16000-bff2b000 rw-p bff16000 00:00 0          [stack], referer: http://localhost/
[Sun Mar 04 11:52:30 2007] [error] [client 127.0.0.1] ffffe000-fffff000 ---p 00000000 00:00 0          [vdso], referer: http://localhost/
```

I guess that it doesn't matter, but when I start apache2 it gives the following error:
```
 * Forcing reload of apache 2.0 web server...                                   apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                       [ ok ] 
``` 

Any help would by appreciated. Thank's in advance :)

---

