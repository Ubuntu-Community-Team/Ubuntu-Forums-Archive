---
title: "Problem/Bug with Edgy's coreutils package?"
date: 2006-10-26
forum: General Help
---

### Post by falko on 2006-10-26
I'm getting this error during ISPConfig installation on Ubuntu 6.10 (when it tries to compile Apache with mod_ssl):

```
Configuring for Apache, Version 1.3.37
 + Warning: Your 'echo' command is slightly broken.
 + It interprets escape sequences per default. We already
 + tried 'echo -E' but had no real success. If errors occur
 + please set the SEO variable in 'configure' manually to
 + the required 'echo' options, i.e. those which force your
 + 'echo' to not interpret escape sequences per default.
 + using installation path layout: Apache (config.layout)
Creating Makefile
Creating Configuration.apaci in src
Syntax error --- The configuration file is used only to
define the list of included modules or to set Makefile in src
options or Configure rules, and I don't see that at all:
/root/ispconfig/openssl
yes
default
no
no
no
 `$(SRCDIR)/apaci`
no
default
default
no
no
no
yes
no
default
no
default
default



















./configure:Error: APACI failed
ERROR: Could not configure Apache
cd: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
mv: cannot stat `binaries/aps.tar.gz': No such file or directory
mv: cannot stat `binaries/spamassassin.tar.gz': No such file or directory
mv: cannot stat `binaries/uudeview.tar.gz': No such file or directory
mv: cannot stat `binaries/clamav.tar.gz': No such file or directory
mv: cannot stat `binaries/cronolog': No such file or directory
mv: cannot stat `binaries/cronosplit': No such file or directory
mv: cannot stat `binaries/ispconfig_tcpserver': No such file or directory
mv: cannot stat `binaries/zip': No such file or directory
mv: cannot stat `binaries/unzip': No such file or directory
tar: spamassassin.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `spamassassin': No such file or directory
tar: uudeview.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `uudeview': No such file or directory
tar: clamav.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `clamav': No such file or directory
tar: aps.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./setup2: line 849: ispconfig_tmp/php/bin/php: No such file or directory
ERROR: The PHP binary coming with ISPConfig does not work properly on your system! The installation routine stops here!
root@server1:/tmp/install_ispconfig#
```

Something seems to be wrong with the echo command, so I replaced the coreutils package with older ones from 6.06 and 5.10 which didn't help. Afterwards I compiled the coreutils package from the sources, but it also didn't help...  :( :(

If someone knows how to fix it, please let me know.

---

### Post by falko on 2006-10-27
Found the solution: [http://www.howtoforge.com/forums/showthread.php?t=7716](http://www.howtoforge.com/forums/showthread.php?t=7716) :-D

---

