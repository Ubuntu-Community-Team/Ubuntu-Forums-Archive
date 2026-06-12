---
title: "openoffice error while trying to open files"
date: 2007-01-26
forum: General Help
---

### Post by banditti on 2007-01-26
I have 6.10 and when I try to open any doc, xls, ppt files from my companies I get a "General Internet error has occurred"

I did a little googe'ing and found some stuff about fonts, tried it and no luck.


Thoughts?

---

### Post by lyceum on 2007-01-26
Where are you geting the docs? From the internet? Are you having this problem with other doc files?

---

### Post by banditti on 2007-01-26
I meant to say from my companies file server.  Pretty much any file.

---

### Post by lyceum on 2007-01-26
Do you know the server format?

---

### Post by banditti on 2007-01-26
The format of the files?  .doc xls and ppt in Win 2003

---

### Post by lyceum on 2007-01-26
Ubuntu has trouble reading some windows formants, like NTFS. If your network server is Unix or Linux, there should be not probs but if the server is running Windows, there may be an issue. To be honest, I am not sure what other problem it could be.

---

### Post by banditti on 2007-02-01
As I follow-up, I figured it out. It was a issue between ubuntu and NetApp. I had NetApp 7.04, which didn't work. Upgraded to 7.1.1 on the filer, all is well.

---

### Post by lyceum on 2007-02-01
awesome

---

### Post by banditti on 2007-02-06
Thank you for the assistance.

---

