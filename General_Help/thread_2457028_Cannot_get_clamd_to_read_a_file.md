---
title: "Cannot get clamd to read a file?"
date: 2021-01-24
forum: General Help
---

### Post by pcla56 on 2021-01-24
Hi Team, I am running Ubuntu 20.04 LTS LAMP server with php7.4

Our web service uploads image files and I want to scan them before accepting them with clamav.

I installed the clamav-daemon package successfully; started the service and checked the LocalSocket was created and was world "rw".

I then use a small php library to talk to that socket (successfully). However, no matter where the file is located the "SCAN fullfilepath" command fails because it reports it cannot read the file or directory.

I have carefully checked the clamav users access (execute on each directory) and read on the file so simply cannot fathom what the problem is?

In (slight) desperation, I have posted this incase someone else has managed to get this working and is willing to share?

Thanks, Paul

---

### Post by &amp;KyT$0P# on 2021-01-25
Have you tried passing [FONT=Courier New]--fdpass[/FONT] option to clamdscan?

---

