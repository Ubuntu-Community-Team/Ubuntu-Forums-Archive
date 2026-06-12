---
title: "PHPsysinfo error?"
date: 2007-06-24
forum: General Help
---

### Post by drifting on 2007-06-24
I just installed PHPsysinfo with synaptic, no idea what this error means, has anyone any idea?

Warning: gethostbyaddr() [function.gethostbyaddr]: Address is not a valid IPv4 or IPv6 address in /usr/share/phpsysinfo/includes/os/class.Linux.inc.php on line 82

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/phpsysinfo/includes/os/class.Linux.inc.php:82) in /usr/share/phpsysinfo/includes/system_header.php on line 31

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/phpsysinfo/includes/os/class.Linux.inc.php:82) in /usr/share/phpsysinfo/includes/system_header.php on line 35

Did a quick scan on Google and searched here, but nothing seemed to jump out as being the same?

Paul.

---

### Post by drifting on 2007-07-30
Bump

Anyone?

---

### Post by hardkaare on 2007-08-08
Same problem her im running ubuntu-server 7.4 and phpsysinfo 2.5.2

---

### Post by foom on 2007-10-31
Don't know if this will help but it did for me.  At least it was a work around.

You will need to edit a file.

cd /var/www/html/phpsysinfo/includes/os/

vi class.Linux.inc.php

then comment out line 82

//      $result = gethostbyname($this->chostname());

save the file and then try to get back into phpsysinfo.


Best regards,

Foom

---

