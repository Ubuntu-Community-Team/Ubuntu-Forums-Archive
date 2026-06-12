---
title: "Cant Install Firefox 1.0.4"
date: 2005-07-03
forum: General Help
---

### Post by Zerileous on 2005-07-03
I always get an error when trying to install the 1.0.4 version of firefox.  Not only do I want the updates, but I really want the ability to  install extensions, as I use many of them.  So it would be accptable for me to use extensions with the current release rather than use 1.4.

I will just show you the code that I get when I try to install via apt-get.  This is the block of code with errors in it, if you need the whole thing just let me know.

```
Preconfiguring packages ...
(Reading database ... 78143 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
justin@ubuntu:~$
```

So, what gives? 
Thanks.

---

### Post by adwait on 2005-07-03
Hello,

One thing is, always use apt-get to install packages. That way you don't run a risk of messing up things.

Now to your problem, the problem is that the firefox which comes with Ubuntu is actually 1.0.4, but the people at Ubuntu forgot to incrememnt the version number. Now to download the extensions, here's what you do:

type about:config in the address bar and pres enter. You will be presented with a table. search for the key called general.useragent.vendorsub and edit to read 1.0.4 instead of the previous 1.0 or 1.0.2.

You should now be able to install extentions :)

---

### Post by Bandit on 2005-07-03
[QUOTE=Zerileous]I always get an error when trying to install the 1.0.4 version of firefox.  Not only do I want the updates, but I really want the ability to  install extensions, as I use many of them.  So it would be accptable for me to use extensions with the current release rather than use 1.4.

I will just show you the code that I get when I try to install via apt-get.  This is the block of code with errors in it, if you need the whole thing just let me know.

```
Preconfiguring packages ...
(Reading database ... 78143 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.0.4-1ubuntu3~5.04ubp5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
justin@ubuntu:~$
```

So, what gives? 
Thanks.[/QUOTE]

Uninstall the original FFox that comes with Ubuntu.
Then download the standard firefox1.0.4 for i686.
then ungzip and untar the file. 
Then run "sudo firefox-installer" <-- what ever the installer is...
Then choose /opt/ as the install dir. 
Everthing should install fine.
Cheers,
Joey

P.S. forgot to mention you need everything to point to the new FFox location and set the file associations to point to that version as well.

---

### Post by Zerileous on 2005-07-03
thanks adwait that did the trick.

---

