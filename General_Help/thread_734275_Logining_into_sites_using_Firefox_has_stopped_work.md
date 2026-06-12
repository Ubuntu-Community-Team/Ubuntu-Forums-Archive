---
title: "Logining into sites using Firefox has stopped working"
date: 2008-03-24
forum: General Help
---

### Post by Robbyx on 2008-03-24
Is there a problem with Java 6? I have upgraded to it and also installed  a load of dependencies for Beagle. Since then I can go to sites but not log in. After entering the password and login name, it says it is done but I am not taken to the post login page. The login page stays as it was. I have tried loading Firefox in safe mode. It made no difference. Anyone had a similar problem and been able to solve it?

Robin

---

### Post by Robbyx on 2008-03-24
I have just realised that I was able to login into the Ubuntu forum so it must be certain sites using particular protocols, I guess. Does this help solve my problem?

Robin

---

### Post by Robbyx on 2008-03-24
The cause is not Sun Java 6. I have just removed it and installed 5. I still have the problem.

---

### Post by dbera on 2008-03-24
> **Robbyx said:**
> The cause is not Sun Java 6. I have just removed it and installed 5. I still have the problem.

Did you install the firefox beagle extension ? Maybe that one is doing something ? Disable it from the extensions window and see if it improves anything.

---

### Post by Robbyx on 2008-03-24
I have found the cause. 

I have installed an addon called stealth. It switches off the acceptance of cookies and other records of where I have been surfing. Unfortunately it does not seem to turn it back on when I untick it.

The sites  I have been visiting require cookies set on.

---

### Post by Robbyx on 2008-03-24
I removed stealther and reinstalled it and it is now working properly. It must have been corrupted. Safe mode made no difference because the settings were defaulting to no cookies.

---

