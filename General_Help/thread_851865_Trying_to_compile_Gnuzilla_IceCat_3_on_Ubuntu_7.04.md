---
title: "Trying to compile Gnuzilla IceCat 3 on Ubuntu 7.04"
date: 2008-07-07
forum: General Help
---

### Post by s3a on 2008-07-07
Here is what I did in the terminal:

[B]deniz@deniz-desktop:~$ cd ~/Desktop/icecat-3.0-g1
deniz@deniz-desktop:~/Desktop/icecat-3.0-g1$ ./configure
bash: ./configure: No such file or directory
deniz@deniz-desktop:~/Desktop/icecat-3.0-g1$ ls
application.ini           libjemalloc.so   libxpcom_core.so
blocklist.xml             libmozjs.so      libxpcom.so
browserconfig.properties  libnspr4.so      modules
chrome                    libnss3.so       mozilla-xremote-client
components                libnssckbi.so    platform.ini
defaults                  libnssdbm3.so    plugins
dictionaries              libnssutil3.so   README.txt
extensions                libplc4.so       removed-files
greprefs                  libplds4.so      res
icecat                    libsmime3.so     run-icecat.sh
icecat-bin                libsoftokn3.chk  searchplugins
icons                     libsoftokn3.so   updates
libfreebl3.chk            libsqlite3.so
libfreebl3.so             libssl3.so
deniz@deniz-desktop:~/Desktop/icecat-3.0-g1$ 
deniz@deniz-desktop:~/Desktop/icecat-3.0-g1$ ./run-icecat.sh
find: /home/deniz/.gnuzilla/: No such file or directory

(Gecko:12800): GLib-CRITICAL **: g_hash_table_unref: assertion `hash_table != NULL' failed
./icecat-bin: symbol lookup error: ./icecat-bin: undefined symbol: g_once_init_enter_impl
deniz@deniz-desktop:~/Desktop/icecat-3.0-g1$ ./run-icecat.sh
./icecat-bin: symbol lookup error: ./icecat-bin: undefined symbol: g_once_init_enter_impl
deniz@deniz-desktop:~/Desktop/icecat-3.0-g1$ icecat
bash: icecat: command not found
deniz@deniz-desktop:~/Desktop/icecat-3.0-g1$[/B]

After typing in "./run-icecat.sh", IceCat 3 launched, asked me if I wanted to import settings (I chose no) then it crashed. I typed the command again, and it launched then crashed immediately.

P.S.
Don't tell me to upgrade my Ubuntu version because my laptop doesn't work with any version other than Ubuntu 7.04.

Thanks in advance!

---

