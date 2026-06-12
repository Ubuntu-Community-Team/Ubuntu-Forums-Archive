---
title: "PHP &amp; MySQL"
date: 2007-10-19
forum: General Help
---

### Post by nami on 2007-10-19
Hello.

Does anyone know if I can start coding in php locally and view it on the firefox browser?  Does ubuntu have php built in by default?

---

### Post by Aikon- on 2007-10-19
> **nami said:**
> Hello.

Does anyone know if I can start coding in php locally and view it on the firefox browser?  Does ubuntu have php built in by default?

I don't think it comes installed by default, but you should be able to install it via Synaptic.

Just do a search for "php". On my system (Dapper 6.06) this is "php5-cgi". You will also need the packages "apache2" and "mysql-server". You may need to activate Apache from System->Administration->Services; the default root for web files is "/var/www"; just start putting stuff in there (start with HTML to make sure Apache is working then switch to PHP).

You should then be able to point your browser to [http://localhost](http://localhost) and have it show up.

Sorry for not being more detailed.. Its fairly simple to do, you shouldn't need any guides or anything. I would give you a fuller description but its 4:30am here and I'm currently procrastinating from my Spacesystems Design assignment that is due at 1:00pm =P

-Aikon

---

### Post by nami on 2007-10-19
no worries, i wont be able to try it yet anyway for another 8ish hours.

---

### Post by nami on 2007-10-20
ok i tried installing it but it does not work.  the html works but the php code does not work...

help

---

