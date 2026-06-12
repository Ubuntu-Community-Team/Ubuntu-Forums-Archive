---
title: "really strange php problem - seems to loose data between apache and firefox"
date: 2005-10-29
forum: General Help
---

### Post by kerinin on 2005-10-29
i'm using apache2 and php4 to develop a CMS.  about two hours ago i restarted my system, and when it rebooted i couldn't load any of my php files any more.  

the strange thing is that it only occurs on certain files - i can run my phpinfo.php script, and some of my files will load OK.  Even the ones that don't load take a long time to not load - i try to go the the file, firefox thinks, the hard drive clicks, but then nothing happens.  i don't get a 404 error, i don't get a blank page, i don't get the page i'm supposed to be seeing - its just thinks for a minute or so and then does nothing.

has anyone ever seen anything like this?  i've tried reinstalling all the php and apache packages, restarting apache and rebooting.  nothing works.  

thanks!

---

### Post by suRoot on 2005-10-31
Try running it from a console next time it happens.

$php /path/to/file.php

See if it returns any output

Also, check the php manual for enabling error messages / debugging.

---

