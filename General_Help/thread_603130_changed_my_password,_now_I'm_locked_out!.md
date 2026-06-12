---
title: "changed my password, now I'm locked out!"
date: 2007-11-04
forum: General Help
---

### Post by hodad on 2007-11-04
I have 2 pcs; desktop and laptop.  Both had same UID/PW, so I first changed the uid's and kept the same pw.  I was trying to connect one to the other thru ssh to transfer files.   Everything worked fine, I logged in several times, but thought that the pw's should be different on the two machines.  On the desktop, I changed the pw (Admin-Users), and tried to log back in, and it doesn't recognize my UID/PW.   I can log into my wife's account, but she has no admin priviledges.  Anyone know how I can get into my root login??

---

### Post by steveneddy on 2007-11-04
Hoo-wee. I accidentally did that on my file server last month and had to totally reinstall. At least I was able to install an actual version of Ubuntu's LAMP server. I'm glad that I did because it runs much better now.

I hope that you don't have to reinstall.

---

### Post by hodad on 2007-11-04
I don't mind reinstalling, as long as I can retrieve my files; will I have that option, or will it wipe everything?

---

### Post by hodad on 2007-11-04
Found solution in a posting from April of this year from Merlinus:

Boot up in Retrieval mode.
type passwd <username>
you'll be prompted to enter the new pw (twice)
then reboot

It worked!

---

