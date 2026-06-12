---
title: "mysql crashed after upgrade from 8.0.32 to 8.0.33 CRYPTO_SSL"
date: 2023-05-09
forum: General Help
---

### Post by mgieparda on 2023-05-09
Hello,

After automatic upgrade of mysql from 8032 to 8033 (Ubuntu 20.04.1). Mysql does not start with a message:
The SSL library function CRYPTO_set_mem_functions failed. This is typically caused by the SSL library already being used. As a result the SSL memory allocation will not be instrumented.

what can I do?

Attempting backtrace. You can use the following information to find out
where mysqld died. If you see no messages after this, something went
terribly wrong...
stack_bottom = 0 thread_stack 0x100000
/usr/sbin/mysqld(my_print_stacktrace(unsigned char const*, unsigned long)+0x41) [0x558afc4947b1]
/usr/sbin/mysqld(print_fatal_signal(int)+0x39b) [0x558afb311b5b]
/usr/sbin/mysqld(handle_fatal_signal+0xa5) [0x558afb311c15]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x14420) [0x7f9307ce6420]
/usr/lib/x86_64-linux-gnu/libssl.so.1.1(SSL_CTX_get_security_level+0x4) [0x7f93080e8554]
/usr/sbin/mysqld(security_level()+0x23) [0x558afb352be3]
/usr/sbin/mysqld(do_auto_cert_generation(ssl_artifacts_status, char const**, char const**, char const**)+0x57) [0x558afb359c87]
/usr/sbin/mysqld(Ssl_init_callback_server_main::provision_certs()+0x72) [0x558afb296ed2]
/usr/sbin/mysqld(TLS_channel::singleton_init(Ssl_acceptor_context_container**, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, bool, Ssl_init_callback*, bool)+0x265) [0x558a2953a5]

---

### Post by mgieparda on 2023-05-09
OK, solved by installing mariadb instead.

---

### Post by nhoeller2 on 2023-05-15
I'm running into a similar issue with my Ubunutu 20.04 server when upgrading to MySQL 8.0.33. Luckily, I had a snapshot that was taken right before the upgrade so I'm able to confirm that everything was working fine on 8.0.32, but as soon as I try to run
```
$ [FONT=Helvetica Neue][COLOR=#000000]sudo apt-get --only-upgrade install mysql-server-8.0
```[/COLOR][/FONT]
[FONT=Helvetica Neue][COLOR=#000000]It fails to load the MySQL server. I'm not sure if you have access to your logs prior to this upgrade, but for me I noticed that the message about the SSL library was appearing prior to the 8.0.33 upgrade, so I'm not sure if it's the actual cause of the crash (at least in my case).[/COLOR][/FONT]

[FONT=Helvetica Neue][COLOR=#000000]I'd still be interested to find out what's causing this crash. Unfortunately, a migration to MariaDB isn't an option for me at the moment. Is anyone else running into this issue?[/COLOR][/FONT]

---

### Post by nhoeller2 on 2023-06-05
[COLOR=#000000][FONT=&amp]I found out what was causing the crash in my situation. I'm not sure if this is the exact same for you, but maybe this will help.

This issue was occurring because FIPS was enabled on the Operating System using Ubuntu Pro, but was not enabled within MySQL.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]To enable FIPS in MySQL, go to /etc/mysql/my.cnf and add the following line:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp][mysqld][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]ssl_fips_mode = ON[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Restart MySQL:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp]sudo systemctl restart mysql[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]And then run another upgrade to fix the MySQL packages that didn't fully install:[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp]sudo apt upgrade[/FONT][/COLOR]
```

[COLOR=#000000][FONT=&amp]I'm still not sure why this issue didn't show up until version 8.0.33, but this is what fixed it for me.[/FONT][/COLOR]

---

