---
title: "Accidently Deleted /etc/init.d/samba!"
date: 2005-04-15
forum: General Help
---

### Post by eleqtriq on 2005-04-15
Can someone please tell me which package to reinstall to get the samba script back?  I've reinstalled all packages named *samba* to no avail.  Thanks.

---

### Post by andvaranaut on 2005-04-15
The package 'samba' should do the trick. How are you reinstalling the package? Use synaptic if unsure.

I have attached a copy of /etc/init.d/samba, anyways ;) (from samba 3.0.10-1ubuntu3)

Cheers

---

### Post by geekgod on 2005-04-15
[http://www.faqs.org/docs/securing/chap29sec292.html](http://www.faqs.org/docs/securing/chap29sec292.html) <<maybe has a  SMB script and how to, maybe it will help

never underestimate a man with alot of time and google.....
~james

---

### Post by az on 2005-04-15
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=%2Fetc%2Finit.d%2Fsamba&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=%2Fetc%2Finit.d%2Fsamba&searchmode=searchfiles&case=insensitive&version=hoary&arch=i386)

Look there.


Packages.ubuntu.com is your friend.

---

### Post by eleqtriq on 2005-04-16
Thanks for the script!

I've reinstalled Samba countless times, the /etc/init.d doesn't regenerate.  I go into aptitude, find "samba" and hit "L" (for reinstall).  It works, except for the script.  I even uninstalled it completely, and installed it fresh.  Nothing.  I'm not sure why. 

Thanks for the help guys. ^^ that page above will be useful in the future.

---

