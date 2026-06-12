---
title: "libapache2_mod_log_sql breaking CGI in Hardy"
date: 2008-07-01
forum: General Help
---

### Post by msouth on 2008-07-01
Hello,

I have recently installed libapache2_mod_log_sql on hardy via synaptic and after several long hours managed to get the conf file to where the module is logging, when I discovered that my previously working perl scripts started generating "premature end of script headers".  Thinking something went wrong with the perl mod, I disabled it and then tried running a bash cgi script like this:

#!/bin/bash

echo "Content-Type: text/plain"
echo
echo "Bash is working."

I found that it also generated "premature end of script headers".

I commented out the conf directives for mod_log_sql and removed it via synaptic.  Both my perl scripts and the bash script started running again in my cgi-bin.

Thinking maybe there was an install problem with mod_log_sql I tried reinstalling it with synaptic (without uncommenting the directives for it) and CGI goes down again. Removed it, CGI is back up.  It's not something I have in the conf since mod_log_sql directives are still commented out - I am just loading the module.  I have the standard Apache 2.2 (mpm prefork) server installed, desktop version of Ubuntu Hardy.  I have looked all over the web and it appears others have both mod_log_sql and CGI functionality... Where is this going wrong? I really need to use the logging function and was testing it for production use on another box.  Is this a bug in Hardy only?

I am using Hardy, 32 bit platform, desktop.  I am standing by with Apache conf files if needed.

Please help.

---

