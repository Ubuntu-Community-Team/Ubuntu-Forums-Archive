---
title: "Why is my website down?"
date: 2006-09-11
forum: General Help
---

### Post by Hanj on 2006-09-11
This might not be the best place to ask this, so feel free to move it to a better suited area.

Anyway, I have a website which is hosted by a hosting company (it's running Apache) and everything was working fine until a few days ago. I was updating some files via FTP, and when I tried to check the site in Firefox I got a 403 Forbidden error, which still persists. Is it possible that I by mistake changed some important permission settings over FTP? Is there some easy way to change this back? Or is this something I have to contact the hosting company about?

---

### Post by Tomosaur on 2006-09-11
It is possible yes, but you should still be able to connect to the web-server via FTP even if you have messed up your file permissions, since the FTP protocol is not controlled by you. I would get in touch with your hosting company if you cannot connect to the server at all.

---

### Post by Hanj on 2006-09-11
Maybe I wasn't clear: I can still connect via FTP without problems. It's when I try to view the website in a browser that I get the 403 error.

---

### Post by toasterofirony on 2006-09-11
Check the permissions on your web pages, though I would think it was pretty difficult to accidently change them without realising.

---

### Post by Hanj on 2006-09-12
I've already tried changing the file permissions, but no luck. Thanks for the replies though. I'll contact the hosting company and see what they say.

---

