---
title: "Do you need Ad-Aware for Ubuntu+Firefox?"
date: 2007-08-12
forum: General Help
---

### Post by sarc on 2007-08-12
I would like to know if there is a need for an app like Ad-Aware - including removal of tracking cookies and such.  Or is restricting the right privileges from users enough to prevent the setup of unwanted cookies?

---

### Post by Steve1961 on 2007-08-12
Hi there, you don't need anything like ad-aware in Linux, and you can control cookies from the preferences menu in firefox

---

### Post by sarc on 2007-08-12
OK thanks!

---

### Post by strabes on 2007-08-12
The most important thing in security is the user. In linux, the only thing you really need to do is install noscript in firefox. You don't need anti-spyware and antivirus programs.

---

### Post by por100pre1 on 2007-08-12
> **sarc said:**
> I would like to know if there is a need for an app like Ad-Aware - including removal of tracking cookies and such.  Or is restricting the right privileges from users enough to prevent the setup of unwanted cookies?

Spyware are mostly malicious ActiveX controls. ActiveX is a Microsoft technology. [No Script]("http://noscript.net/") addon for Firefox will disable scripts, use it and you'll have even more security.

---

### Post by euler_fan on 2007-08-12
[Ubuntu Security Guide]("http://ubuntuforums.org/showthread.php?t=510812")

Also, you can run SafeCache extension, CookieSafe extension, and Stealther/Distrust for some additional privacy online. The first defeats certain attacks against you cache, the second lets you have very granular control over your cookies, and either of the third let you be more anonymous.

Otherwise, there is no need for anything like Ad-aware. If you still feel like you need to be running some kind of AV, then I suggest ClamAV which you can download and install from source to get the latest version. A good (but a touch dated) guide is [here]("http://ubuntuforums.org/showthread.php?t=318091&highlight=install+clamav").

FYI: a quick search of these forums for threads about anti-virus, firewalls, etc. tends to either drop you into threads about using them on a server (usually a VERY good idea) or where people will argue for pages about whether or not they are needed. It's good to ask, but just be aware that it is controversial in the desktop environment.

I encourage you to read all you can and make up your own mind on the issue.

---

