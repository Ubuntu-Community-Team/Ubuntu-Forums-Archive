---
title: "evolution - broken pipe?"
date: 2005-10-26
forum: General Help
---

### Post by angelot on 2005-10-26
I get this errormessage when trying to send mail using sendmail:
```
Could not send message: Broken pipe.
```
I've just installed 5.10 and I had no problem using 5.04...

Please help!

angelot

---

### Post by angelot on 2005-10-26
Sorry!

Found out that I had no MTA installed....

Installed exim4, and it works!

5.10 have no MTA as default?

angelot

---

### Post by nomeat on 2006-07-25
Thanks for posting the solution here.

My Dapper was working fine but then I just suddenly had this problem too.

sudo apt-get install exim4

and all is OK now.

---

