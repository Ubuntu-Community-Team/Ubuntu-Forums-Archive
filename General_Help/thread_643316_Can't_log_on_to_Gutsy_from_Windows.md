---
title: "Can't log on to Gutsy from Windows"
date: 2007-12-17
forum: General Help
---

### Post by lift_test on 2007-12-17
When I try to access Gutsy from a windows machine it asks for name and password, my Gutsy name and PW don't work.  What the hell am I supposed to type in?  I've never set any other PW.

---

### Post by Pumalite on 2007-12-17
What are you using to access the other machine?

---

### Post by lift_test on 2007-12-17
Ethernet and I presume Samba

---

### Post by Pumalite on 2007-12-17
You are using the right tools. Weird.

---

### Post by Pumalite on 2007-12-17
[http://www.troubleshooters.com/linux/presentations/samtroub.htm](http://www.troubleshooters.com/linux/presentations/samtroub.htm)

---

### Post by eapache on 2007-12-17
The default samba config file has been all messed up since Edgy I believe. It's on the to-do list for Hardy. In the meantime try this site:

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)

I know it's complex, and I remember seeing a better guide around somewhere, but it's a place to start. I'll post the better guide when I find it.

---

### Post by eapache on 2007-12-17
Here it is:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by lift_test on 2007-12-17
Too advanced for me this time of night!  I'll have another look when I have more time to spare.  It's strange because I can look at anything I've shared on the win machine but Gutsy wants a name and PW.
Thanks for trying to help.

---

### Post by Pumalite on 2007-12-17
Good luck!

---

### Post by lift_test on 2007-12-23
Tried that and totalled, had to reinstal and still got same problem!

---

### Post by lift_test on 2007-12-23
Found the answer on the net!
Log on as root.
   sudo smbpasswd -a [username]

Then prompts for PW &PW confirm (you don't see any input on screen)
Can then log in using above name & PW.  Don't forget to share required areas first.

---

