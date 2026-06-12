---
title: "Azureus trouble, problems. Simple solutions."
date: 2006-08-03
forum: General Help
---

### Post by skeff on 2006-08-03
Hey here are some problems I've had with Azureus:

·No close button on tabs
·No "health faces"
·Pop-ups will not close

The cause was a combination of Azureus using a 1.4 version of Java and a bug in Azureus 2.4.0.2.

So the first things you should do to fix a broken Azureus are:

·Get a fresh Java 1.5 and make sure Azureus uses it, type 'java -version' to check if the default client is 1.5. You can set the java path in the file azureusROOT/azureus if you prefer to have multiple versions

·Get a CVS (beta) version from [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)
This specifically fixed my pop-up problem. So this bug should be gone by version 2.4.0.3 or 2.5.0.0, whichever they're releasing next ;)

-skeff

---

### Post by anakin513 on 2006-08-04
The java upgrade and CVS build fixed a lot of problems.  Good post.

I did have to change a symlink in /etc/alternatives/java to point to the 1.5 install though.  Just so others know.

Unless there was an easier way to change the default Java.

---

### Post by numb401 on 2006-08-05
Possibly just uninstalling the old one?

---

