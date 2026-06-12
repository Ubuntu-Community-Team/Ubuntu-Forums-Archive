---
title: "install firefox 32-bit on Ubuntu 14.04-64 bit"
date: 2015-01-23
forum: General Help
---

### Post by ric_Poirier on 2015-01-23
Hi, I'm trying to install firefox 32-bit on my 64-bit Ubuntu 14.04 OS. I have downloaded the firefox binaries. Here is what I get when I list what's in this folder:

```

eric@Gide:~/Downloads/Browser downloads/firefox$ ll
total 75M
-rwxr-xr-x 1 eric eric 8.8K Jan  8 23:35 run-mozilla.sh*
-rw-r--r-- 1 eric eric 4.0K Jan  8 23:35 crashreporter.ini
-rw-r--r-- 1 eric eric  825 Jan  8 23:35 Throbber-small.gif
-rw-r--r-- 1 eric eric  659 Jan  9 01:16 application.ini
-rw-r--r-- 1 eric eric  132 Jan  9 02:22 update-settings.ini
-rw-r--r-- 1 eric eric  136 Jan  9 02:23 platform.ini
-rw-r--r-- 1 eric eric  144 Jan  9 02:24 dependentlibs.list
-rw-r--r-- 1 eric eric  681 Jan  9 02:24 updater.ini
drwxr-xr-x 3 eric eric 4.0K Jan  9 02:34 defaults/
-rw-r--r-- 1 eric eric  11M Jan  9 02:34 omni.ja
-rwxr-xr-x 1 eric eric  14K Jan  9 02:34 libplds4.so*
-rwxr-xr-x 1 eric eric  16K Jan  9 02:34 libplc4.so*
-rwxr-xr-x 1 eric eric 230K Jan  9 02:34 libnspr4.so*
-rwxr-xr-x 1 eric eric  19K Jan  9 02:34 libmozalloc.so*
drwxr-xr-x 2 eric eric 4.0K Jan  9 02:34 dictionaries/
-rw-r--r-- 1 eric eric   40 Jan  9 02:34 chrome.manifest
-rwxr-xr-x 1 eric eric  60M Jan  9 02:34 libxul.so*
-rwxr-xr-x 1 eric eric 136K Jan  9 02:35 plugin-container*
-rwxr-xr-x 1 eric eric 155K Jan  9 02:35 firefox-bin*
-rwxr-xr-x 1 eric eric 155K Jan  9 02:35 firefox*
-rwxr-xr-x 1 eric eric 188K Jan  9 02:35 webapprt-stub*
drwxr-xr-x 2 eric eric 4.0K Jan  9 02:35 webapprt/
-rwxr-xr-x 1 eric eric 174K Jan  9 02:35 updater*
-rw-r--r-- 1 eric eric  682 Jan  9 02:35 removed-files
-rw-r--r-- 1 eric eric 2.4K Jan  9 02:35 precomplete
-rwxr-xr-x 1 eric eric 147K Jan  9 02:35 mozilla-xremote-client*
-rwxr-xr-x 1 eric eric 200K Jan  9 02:35 libssl3.so*
-rwxr-xr-x 1 eric eric 205K Jan  9 02:35 libsoftokn3.so*
-rw-r--r-- 1 eric eric  899 Jan  9 02:35 libsoftokn3.chk
-rwxr-xr-x 1 eric eric 123K Jan  9 02:35 libsmime3.so*
-rwxr-xr-x 1 eric eric 126K Jan  9 02:35 libnssutil3.so*
-rwxr-xr-x 1 eric eric 113K Jan  9 02:35 libnssdbm3.so*
-rw-r--r-- 1 eric eric  899 Jan  9 02:35 libnssdbm3.chk
-rwxr-xr-x 1 eric eric 447K Jan  9 02:35 libnssckbi.so*
-rwxr-xr-x 1 eric eric 892K Jan  9 02:35 libnss3.so*
-rwxr-xr-x 1 eric eric 761K Jan  9 02:35 libmozsqlite3.so*
-rwxr-xr-x 1 eric eric  46K Jan  9 02:35 libmozsandbox.so*
-rwxr-xr-x 1 eric eric 413K Jan  9 02:35 libfreebl3.so*
-rw-r--r-- 1 eric eric  899 Jan  9 02:35 libfreebl3.chk
drwxr-xr-x 2 eric eric 4.0K Jan  9 02:35 icons/
-rwxr-xr-x 1 eric eric 124K Jan  9 02:35 crashreporter*
drwxr-xr-x 2 eric eric 4.0K Jan  9 02:35 components/
drwxr-xr-x 7 eric eric 4.0K Jan  9 02:35 browser/

```

How can I install it from here? There seems to be no installer, nor a configure file...

Thanks

---

### Post by Dennis N on 2015-01-23
I am wondering why you are trying to use the 32 bit version on a 64 bit OS. Is it usable? That aside, if you downloaded from Mozilla.org, it ready to run and started by the file 'firefox' in the firefox folder. First move the firefox folder to a suitable location, such as the /opt folder. You would also need to make an appropriate launcher yourself.

---

### Post by ric_Poirier on 2015-01-23
Ok, thank you, I will try that. I want to do so because the Webex plateform does not work on 64-bit firefox. I have heard it does on 32 bit with some manipulations and I want to try it.

---

