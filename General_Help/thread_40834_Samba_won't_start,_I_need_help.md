---
title: "Samba won't start, I need help"
date: 2005-06-10
forum: General Help
---

### Post by mperks14 on 2005-06-10
I'm trying to set up a maching with ftp access and samba running. I chose ubuntu because its the easiest to maintain in my opinion and this is going into an office where eveyone is afraid of linux.

Every time a try to start samba it fails. here's the log file

sambaftp@ubuntu:/var/log/samba$ cat log.smbd
[2005/06/06 10:45:22, 0] smbd/server.c:main(760)
  smbd version 3.0.10-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004
[2005/06/06 10:45:22, 0] printing/pcap.c:pcap_printer_fn(361)
  Unable to open printcap file /etc/printcap for read!
[2005/06/06 11:06:32, 0] smbd/server.c:main(760)
  smbd version 3.0.10-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004
[2005/06/06 11:06:32, 0] printing/pcap.c:pcap_printer_fn(361)
  Unable to open printcap file /etc/printcap for read!
[2005/06/06 15:27:24, 0] param/params.c:Section(258)
  params.c:Section() - Empty section name in configuration file.
[2005/06/06 15:27:24, 0] param/params.c:pm_process(592)
  params.c:pm_process() - Failed.  Error returned from params.c:parse().
[2005/06/06 15:27:24, 0] printing/pcap.c:pcap_printer_fn(361)
  Unable to open printcap file /etc/printcap for read!

anyone have any ideas?

thanks

---

### Post by elvis on 2005-06-24
Samba is having issues sharing your printers (or possibly, you have no printers defined and it doesn't know what to do).

From a terminal, type

"sudo nano -w /etc/samba/smb.conf"

and set "load printers = yes" to "load printers = no".  Save by hitting "CONTROL+X" and answering the prompts.  Restart Samba, and all should be well.

---

