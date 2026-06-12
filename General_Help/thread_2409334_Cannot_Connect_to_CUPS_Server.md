---
title: "Cannot Connect to CUPS Server"
date: 2018-12-31
forum: General Help
---

### Post by merlinus on 2018-12-31
I just re-installed Ubuntu 18.04, and did all the updates.  But when I try to add or use a printer, I get an error message that it cannot connect to the cups server: /run/cups/cups.sock

I checked and the cups server (and all else)  is installed.  I even re-installed the server.

---

### Post by him610 on 2018-12-31
Are correct Printer drivers installed? What make/model printer? 
How is it connected? (IEEE 802.3 wired, IEEE 802.11 wireless, RS-232 serial, IEEE 1284 parallel, USB 2/3)

May we see your system characteristics?* inxi -F* from the command line. (Copy and paste between code tags.)

You can check to see if it is configured, ```
sudo cat /etc/cups/printers.conf 
or
sudo  lpstat -s

```

---

### Post by clementc on 2018-12-31
Hi [**[COLOR=#000000]merlinus[/COLOR]**]("https://ubuntuforums.org/member.php?u=277749"),

In addition to what [**[COLOR=#000000]him610[/COLOR]**]("https://ubuntuforums.org/member.php?u=248298") asked you to run and report back here, can you please run the following command in Terminal and let us know of the result: service cups status

---

### Post by HermanAB on 2019-01-01
Once you confirmed that cupsd is actually running, type this in your web browser:
[http://localhost:631/admin](http://localhost:631/admin)

---

### Post by merlinus on 2019-01-01
Thanks for the assistance!  It is working now.

---

