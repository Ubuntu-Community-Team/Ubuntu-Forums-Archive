---
title: "authentication for Windows to connect to CUPS-PDF"
date: 2007-11-08
forum: General Help
---

### Post by baosheng on 2007-11-08
Hi guys,

I had a strange problem that I have never encountered before. I installed cups-pdf and configured the PDF printer on my computer. It works fine if I send printing instructions to it and I can get desired PDF file. 

Now I am trying to configure an Windows machine that I can generate PDF file from the Windows machine by networking to the PDF printer running on CUPS of my Linux machine. When I configured the printer on Windows, I set the printer URL as [http://hostname.domainname:631/printers/PDF](http://hostname.domainname:631/printers/PDF). Tthen there is a pop-up window says "Security options" and three radios: 1. Use anonymous account; 2. Automatically use the Windows login name and password 3. Use the specified user account

I tried both option 1 and option 3(which is my own username and password on the Linux machine). But none of them works. A warning windows jumped out and said "You don't have access to the printer, please try a different username or password."

How should I configure my CUPS-PDF printer to allow anonymous connect to the PDF printer? Or, how can I set the username and passwd?

Thanks.

Cheers,
Forrest

---

