---
title: "oem configuration manager"
date: 2007-02-22
forum: General Help
---

### Post by eclectica on 2007-02-22
I recently installed the OEM version of Ubuntu 6.10 from the alternate CD.  It all went well and I was able to login  as username "oem" several times after starting up or rebooting.  I never got around to running 'sudo oem-config-prepare' to set up the regular user account.

I was exploring around the System-->Services menu and one of the items I selected there was "oem configuration manager".  As soon as I did that it rebooted or went into a command line mode, and I got errors about the X server.  Eventually it gave me the root prompt.

So rather than deal with that I restarted the computer and tried to login with user "oem".  I was told that directory /home/oem/ did not exist.  And I ended up with the root prompt again.  So I created a new username, as the instructions told me to do, and after rebooting tried to login with that.  The new username and login worked, but again after logging in I ended up with the root prompt.  

So how do get my Ubuntu to boot up normally rather than into a command line mode?  It seems I need to be able unselect what originally caused it, and turn off the oem configuration manager.

---

### Post by mcduck on 2007-02-22
I recommend trying to run the 'sudo oem-config-prepare' now. And if that doesn't help, do a new install and this time don't use the OEM install. It's kind of useless if you are not planning to sell or give away the machine after pre-installing Ubuntu ;)

---

