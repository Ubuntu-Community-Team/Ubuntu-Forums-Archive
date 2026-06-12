---
title: "How do I see the jobs waiting to print in the print que?"
date: 2008-01-17
forum: General Help
---

### Post by tc101 on 2008-01-17
How do I see the jobs waiting to print in the print que?  I go to system/admin/printing, but I don't see a print que.

---

### Post by ronmarley1 on 2008-01-17
When I print something, a printer icon appears on my top panel near the clock.  I can then click on this to see the print jobs.  Once I print something, the icon remains unless I hide it.  Unfortunately, I'm not sure how to open this app. without printing something first.

---

### Post by geirha on 2008-01-17
typing "lpq" in a terminal should display the queue for the default printer

---

### Post by fwojciec on 2008-01-17
Or you can enter "localhost:631" as the address in your browser and get the full access to cups server where you can get this and other info, configure printers, manage jobs, etc.

---

### Post by ronmarley1 on 2008-01-17
> **geirha said:**
> typing "lpq" in a terminal should display the queue for the default printer

Cool.  Did not know that.

---

### Post by tc101 on 2008-01-17
> you can enter "localhost:631" as the address in your browser and get the full access to cups server

Very cool.  There is so much I have to learn about linux and ubuntu.  

OTOH it seems like that should be available from System/admin/printers where a person would normally look for it.   Using localhost:631 is great once you know about it, but it is not intuitive and ubuntu desktop needs to be intuitive for the general public to start using it.

Thanks for your help.

---

