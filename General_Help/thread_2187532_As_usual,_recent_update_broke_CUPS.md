---
title: "As usual, recent update broke CUPS"
date: 2013-11-12
forum: General Help
---

### Post by dargaud2 on 2013-11-12
Hello all,
as every few months, CUPS broke again.
I have a ubuntu server with a USB printer on it. I can print fine from the server.
I also have a first Ubuntu laptop and I can print on the server printer from it.
But now I can't print anymore from the 2nd laptop. It used to work. I've tried everything: unsinstall/reinstall the printer plenty of time (as ipp, htpp, etc), restart cups, etc.
I see the jobs in the client queue for a few seconds and also on the server queue (17%, 60%...) but then they disappear. 
I've enabled debugging and there's nothing strange in [/var/log/cups/error_log]("http://www.gdargaud.net/BugFest/error.log")

1st question: why is there no discovery of network printers from a client ? Why do I have to type the full ipp://server/whatever/IhaveNoIdeaWhatToWriteHere ?
2nd question: on the laptop that woks, on the cups page, if I click on [Prnters], the link to the printer takes me to [http://server:631/printers/EpsonR1800](http://server:631/printers/EpsonR1800), but on the laptop that doesn't work, that link is [http://localhost:631/printers/R1800](http://localhost:631/printers/R1800), but still, as I wrote above, it does send data to the server when I print.

Oh god I hate printers.

---

### Post by tgalati4 on 2013-11-12
Try deleting all of the printers and reinstalling them.  Often after a kernel update, the print queues get messed up.  It's been my experience to expect broken CUPS queues with kernel updates, so I put them off for a while.

---

### Post by dargaud2 on 2013-11-13
I did, on the messed up client, and as already stated I reinstalled it as ipp, http, etc... I don't want to break the server and the other client by uninstalling there ! Should I ?

---

