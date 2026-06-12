---
title: "Windows server or Samba"
date: 2013-11-04
forum: General Help
---

### Post by RH3dDbz on 2013-11-04
Hello, I'm taking a course about Linux, and the teacher ask me a question, please if somebody can help me to answer the question, this is the question:

[SIZE=3]Why not just use another Windows Server for Windows file sharing instead install samba on Linux?[/SIZE]

Thanks in advance.

---

### Post by Drenriza on 2013-11-04
My 2 cents, the brief "overview".

[LIST]
[*]Why purchase two servers if u can purchase one?
[LIST]
[*]And if you purchase one, install a viritulization platform such as VMware-EXSi. Then is the server "strong" enough to handle the load of the two servers?
[*]Also would you be able to handle the administrative overhead of the viritulization platform?
[/LIST]

[*]Weaker server ($ is a issue)
[LIST]
[*]Then you would want to consider a Linux platform since it is less resource hungry then the windows platform.
[/LIST]

[*]NTFS issues
[LIST]
[*]Windows save their files with NTFS permissions. Samba has a option to save the NTFS permissions when you upload a file to a Linux server (Linux does not use NTFS at all Windows only thing).
[/LIST]

[*]Time consumption
[LIST]
[*]It can take more time getting the Samba configuration for NTFS permissions right versus installing the windows way of file sharing.
Tho it takes way less time to install a Linux server versus a Windows server.
[/LIST]

[*]Conclusion :D
[LIST]
[*]If done correctly, then you can install a Linux server faster and cheaper then a Windows server.
And the users would not know the difference. Along with your system would have more resources to tasks since the Linux platform is less hungry for resources then the Windows platform is.
[/LIST]
[/LIST]
Kind regards
A IT-administrator.

---

### Post by RH3dDbz on 2013-11-04
Hello Drenriza, thank you for replying, yes, I totally agree Linux platform is less hungry for resources then the Windows platform is, Linux server is faster and cheaper than a Windows server.

---

