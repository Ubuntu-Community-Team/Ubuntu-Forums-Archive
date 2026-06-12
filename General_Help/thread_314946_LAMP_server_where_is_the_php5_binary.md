---
title: "LAMP server: where is the php5 binary?"
date: 2006-12-08
forum: General Help
---

### Post by andrewjo on 2006-12-08
I have successfully downloaded and installed the LAMP server version of 6.06 (Dapper Drake).  I want to use it for website development purposes.  I am fairly new to Linux.

Everything is fine so far, apache2 and php5 are working as expected.  However, I need to find the path to the php5 binary.  I have searched everywhere but cannot find it!  Really, I did a "find" across the entire system for all files named "*php*" but none of the results looked like the php5 binary!

Can anybody tell me what gives with this?  I believe most Linux systems have the php5 binary in /usr/local/bin, but this is not the case on the Dapper LAMP server.

Any info appreciated.

---

### Post by brt on 2006-12-08
have you installed the package php5-cli ?

if not use: sudo apt-get install php5-cli

it contains the commandline-php, after install you will find it using the command: whereis php

---

### Post by andrewjo on 2006-12-08
Thanks very much for the reply brt.

I am still a little mystified as to why I can currently run php scripts when I don't appear to have a php binary.  I am much confused!  So do I currently have a php binary?  If so, I assume it is called "php" or similar so why can I not find it with "find"?

The reason I need the path to the binary is because I want to install a 3rd-party php script, and the installation procedure for this php script is asking me for the path to the php binary.

In light of this, do you still think I need to install php5-cli?

Thank you

---

### Post by PriceChild on 2006-12-08
Is it maybe because you have php installed as an apache module?

ie. apache2-module-php5 or something like that?

---

### Post by brt on 2006-12-08
you will only need the php binary if you want to execute a php file from command line without having it served by apache through its mod_php.

if you only use php through your webbrowser you do not need the php binary at all, because php is parsed by the apache module.

---

### Post by andrewjo on 2006-12-08
Ok, I think I get it now.  Thanks for your replies.

I guess I need the cli then!  Hopefully it won't "mess up" any of my existing set-up ...

---

