---
title: "Problem with cups"
date: 2020-03-06
forum: General Help
---

### Post by lunalui on 2020-03-06
Hello,

I've recently changed my laptop and yesterday I realized I have some serious issues with cups that I'm unable to solve.
My laptop is a fusion III from pc specialist on which I've installed ubuntu mate 18.04 (64 bit). I believed I copied the cups configuration files from my previuous laptop in order to have all the printers readily available. Unfortunately, when I tried printing yesterday I could not: the printers were visible, but my files were queuing forever and never processed. I tried different types of files (pdf, txt) printing from terminal or from applications (evince, reader) and even tried removing extensions to the file names but to no avail. I also tried reinstalling the printer and sending the job to different printers (hp, toshiba) with the same results. 
I tried reinstalling cups several times, but nothing worked. I then realised (maybe as a consequence of the fixes I tried and did not work) that cups does not start on boot and actually now it looks like I'm not even able to start it manually.

systemctl status cups.service -al -n150

gives


cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2020-03-06 14:55:55 CET; 32min ago
     Docs: man:cupsd(8)
  Process: 2653 ExecStart=/usr/sbin/cupsd -l (code=exited, status=127)
 Main PID: 2653 (code=exited, status=127)

Mar 06 14:55:55 -Fusion-III systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Mar 06 14:55:55 -Fusion-III systemd[1]: cups.service: Scheduled restart job, restart counter is at 5.
Mar 06 14:55:55 -Fusion-III systemd[1]: Stopped CUPS Scheduler.
Mar 06 14:55:55 -Fusion-III systemd[1]: cups.service: Start request repeated too quickly.
Mar 06 14:55:55 -Fusion-III systemd[1]: cups.service: Failed with result 'exit-code'.
Mar 06 14:55:55 -Fusion-III systemd[1]: Failed to start CUPS Scheduler.


I've googled the result and found a similar problems [in this thread]("https://forums.linuxmint.com/viewtopic.php?t=293487") but the solution did not work for me.

The cups version is 2.2.7

Any help with this issue would be greatly appreciated! and of course I can provide more pieces of information if required. thanks a lot in advance

---

### Post by lunalui on 2020-03-09
No one has an idea? It turns out that the problem with cups not starting was related to the fact that I had introduced an inconsistency with some library. The fact that the files are never processed still remains, thoug...:(

---

### Post by him610 on 2020-03-10
Was there some advantage to copy '/etc/cups/cupsd.conf' from the previous laptop to the current laptop?
Personally, that is something I never do, but then again, it is something I have never considered. I would have thought there were enough subtle differences between two different systems to have avoided sharing configuration files.

---

### Post by him610 on 2020-03-10
I began looking into your issue. Were you perhaps attempting to save some time by not installing and configuring your printers by copying over the '/etc/cups/cupsd.conf'? I looked at the cupsd.conf on two different computers; I could detect no difference in the files. Not saying there was no difference; just saying I did not notice any difference.
There is another configuration file, */etc/cups/printers.conf* that describes the configuration of installed printers. It is not for casual viewing, and I would think it is*** not ***meant to be copied from one device to another since it has some UUID identification in it.
If you need help installing printers on you new fusion III, just ask.

---

