---
title: "Printer applet fails to start"
date: 2007-07-14
forum: General Help
---

### Post by colossus73 on 2007-07-14
Hi,

when I run:

gt[sdb10]$ python /usr/share/system-config-printer/applet.py
system-config-printer-applet: failed to start PrintDriverSelection service

I get the error message above and no applet appears on the systray. The cups daemon is
started but strangely I cant get its page in the browser at localhost:631

gt[sdb10]$ ps ax | grep cups
 9184 ?        Ss     0:00 /usr/sbin/cupsd

Any idea of what happened? I use Xubuntu.

Thanks,

---

### Post by TheExplorer on 2007-07-15
Find your printer [here]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters?highlight=%28%28HardwareSupportComponentsPrintersHp%29%29"). Read the instructions and reinstall the driver.
To manage your printer use: [http://127.0.0.1:631/]("http://127.0.0.1:631/").
P.S. Try to avoid configs with gui cause they suck. My applet that came with feisty distrib doesn't work at all :)
Trust your hands only.

---

