---
title: "Controlling print jobs using CUPS API"
date: 2022-02-21
forum: General Help
---

### Post by chaimaznaidi7 on 2022-02-21
[FONT=Arial]Hello everyone ![/FONT]
[FONT=Arial]
So I am using CUPS installed on a Ubuntu/Linux machine as a printer server in a local network of a samall company.
**The problems is that, before directly sending the Print job to the network printer, I want to store it in the server itself for a moment.**
I’ve actually searched in the CUPS APIS’ function but without any result !

**So If you have any idea or hint that can help me just mention it please, note that I am using <cups/cups.h> library for programming**[/FONT]
[FONT=Arial]
Thank you in advance ^^ [/FONT]

---

### Post by TheFu on 2022-02-21
If it were me, I'd setup an **inotify** on the print spool directory that kicked off a file copy action when the file copy in was complete. This won't delay the actual print, but you will have a copy of the queued file to process as you like.

---

