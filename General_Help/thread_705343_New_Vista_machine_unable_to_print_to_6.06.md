---
title: "New Vista machine unable to print to 6.06"
date: 2008-02-23
forum: General Help
---

### Post by ddmiller on 2008-02-23
So, I was merrily computing along, when our IT group at work informs me that my laptop is EOL and will be replaced with a new one - complete with Vista.

I've managed to cope with the transition OK, but there's one annoying problem:  my new Vista laptop is unable to print to my home server, which runs 6.06 LTS.

Now, I know the linux file/print server is configured correctly - I was able to print to it with my previous machine, with two other XP machines in the house, and the configuration hasn't changed.

I've installed the printer in Vista as a remote printer using the "http://<server>:631/printers/<printer>" format (which is what I used on the XP machines), and I have the driver installed locally on the Vista box.

However, when I print a test page, it shows up in the Vista queue, but hangs there.  It never shows up in the queue on the Linux box.

Any suggestions?

Thanks in advance,

---

### Post by ddmiller on 2008-03-15
OK, I'll answer - sort of - my own question here ...

... I've still not gotten Vista to print to a printer configured via the TCP/IP port (http://<servername>:631/printers/<printer>).  However, when I tried sharing the printer via Samba and connecting to it that way, it worked.  I can't view the queue in Vista, but I can browse the server's CUPS page and see it that way, so it basically works - at least for the small volume of printing I do here.

Maybe Vista SP1 will fix the TCP/IP printing issue....

---

