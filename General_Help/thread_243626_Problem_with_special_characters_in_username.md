---
title: "Problem with special characters in username"
date: 2006-08-25
forum: General Help
---

### Post by vinodh on 2006-08-25
I created a user éâäåçêèïîìÄæôòû using the command useradd:

$ useradd -g éâäåçêèïîìÄæôòû -m éâäåçêèïîìÄæôòû -p éâäåçêèïîìÄæôòû -s /bin/bash éâäåçêèïîìÄæôòû

So when I viewed /etc/passwd, I can see it:

~$ cat /etc/passwd
admin_external_partner-itt:x:1009:1009:,,,:/home/admin_external_partner-itt:/bin/bash
admin_external_partner-ittbdv:x:1010:1010:,,,:/home/admin_external_partner-ittbdv:/bin/bash
admin_external_partner-ittbdv002:x:1011:1011:,,,:/home/admin_external_partner-ittbdv002:/bin/bash
éâäåçêèïîìÄæôòû:x:1012:1012::/home/éâäåçêèïîìÄæôòû:/bin/bash
snmp:x:110:65534::/var/lib/snmp:/bin/false
mysql:x:111:115:MySQL Server,,,:/var/lib/mysql:/bin/false
Debian-exim:x:116:116::/var/spool/exim4:/bin/false


but when I try to change to that user I get an error ] :
~$ su - éâäåçêèïîìÄæôòû
su: User not known to the underlying authentication module
Sorry.

:confused: 

Anybody encountered such a problem or know a workaround?!

Thanks,

V~

---

### Post by ajgreeny on 2006-08-25
I suspect this is due to the keyboard settings depending upon the desktop running, so when you are still at the logon screen you don't have gnome, kde or whichever desktop for keyboard and special characters to be available.  I think you will need to use lower case standard alphanumeric letters and numbers.

If this is your only user set up so far you will need to make a new one with a live CD, but I assume you must have another user, as I don't think you could use special characters during installation.

---

### Post by vinodh on 2006-08-28
Actually I am already logged in via gnome. I am just trying to 'su' via the gnome 'Terminal'. So since I am able to type it, and I see that the GUI 'Users and Groups' also has the username/password in the list, I should be theoretically able to 'su' without any problems. But this is not the case!! Any other ideas?!

---

