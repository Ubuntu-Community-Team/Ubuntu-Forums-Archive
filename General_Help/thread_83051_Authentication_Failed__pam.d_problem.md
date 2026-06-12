---
title: "Authentication Failed / pam.d problem"
date: 2005-10-27
forum: General Help
---

### Post by daahli on 2005-10-27
Hey guys,

First off, I'm a foolish newbie... That said, I attempted to follow this HOWTO [http://www.ubuntuforums.org/showthread.php?t=5409](http://www.ubuntuforums.org/showthread.php?t=5409), but ended up in a situation where I can no longer login. Unfortunately I didn't make any backups of the PAM.d files (I truly am a fool, I wasn't kidding), so I went back and tried to change the files back to their original state from what I remembered them being originally. Yeah, didn't work... In fact, now when I try to log in it tells me "AUTHENTICATION FAILED" even before I get a chance to type in my password (i.e after I type in my username and press enter to get to the password promt).

Moral of this rather painful story is that I was able to activate the root account by using a live CD and then boot into recovery mode (I'm writing this from root). Could somebody please post what the pam.d files should look like?

Oh, I should also mention that I changed the permissions of /etc/shadow by using chmod 777, because I thought that might help, but of course it didn't. So I would appreciate if somebody could tell me how to change that back to what it should be as well.

Hoping to get through this... ](*,)

EDIT: FIXED!! I found the following site: [http://craige.mcwhirter.com.au/blog/archive/2005/01/17/making_a_debian_or_ubuntu_mach](http://craige.mcwhirter.com.au/blog/archive/2005/01/17/making_a_debian_or_ubuntu_mach) and compared the pam.d files there to mine and by doing so was able to figure out what the original must have been! PHEW ;)

---

