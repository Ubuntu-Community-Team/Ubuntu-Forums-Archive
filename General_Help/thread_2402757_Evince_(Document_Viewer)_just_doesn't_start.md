---
title: "Evince (Document Viewer) just doesn't start"
date: 2018-10-04
forum: General Help
---

### Post by barben360 on 2018-10-04
Hello,

I have a problem with evince I'm stuck with.

When I try to run it, nothing happens except one of my CPU cores running to 100%. When I run it from a terminal I have no output. I see no log entry with journalctl.

I tried removing/purging and installing again, still the same problem.

Any idea of what could cause that? And how to get more debug information?

Thanks!

N.B: I'm on an on-date Ubuntu 18.04 LTS.

---

### Post by i7Fd-2sCB1 on 2018-10-04
From my understanding could you post the output of 

```

top

```

or

```

htop

```

This may show you what's using the CPU usage or causing the CPU usage increase. I've got those commandlines from this thread [https://ubuntuforums.org/showthread.php?t=1642561](https://ubuntuforums.org/showthread.php?t=1642561) but it may also help looking at this bug report here [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/384062](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/384062) which the problem was reported fixed though it may not be in this case....

---

### Post by Claus7 on 2018-10-04
Hello,

just to verify that evince is responsible for the high consumption of memory:
i) open a terminal and type evince and at the same time 
ii) open a new terminal and type ps ux | grep evince
iii) while having all these opened, if in a third terminal you type top, can you discern which is the program that occupies most of your memory?

EDIT: just beaten from *centralpython* for a couple of minutes.

Regards!

---

### Post by barben360 on 2018-10-04
Thanks for your answers. As expected, the job called "evince" takes 100% of my CPU.

---

### Post by Claus7 on 2018-10-04
Hello,

could you try okular instead? It is a document viewer. If okular works, then it should be evince related. If not, then I suppose that the problem might lie in the drivers of your graphics card. You can install okular from synaptic package manager.

Also, how have you installed evince? Is it from synaptic package manager? Which version?

Regards!

---

### Post by ajgreeny on 2018-10-04
Have you installed evince as 18.04 yourself has now moved on to Atril?

Did you clean install, or did you upgrade your system from 16.04 to 18.04 which have pulled in evince as it was still there in 16.04?

---

### Post by Claus7 on 2018-10-04
Hello,

> **ajgreeny said:**
> Have you installed evince as 18.04 yourself has now moved on to Atril?

Did you clean install, or did you upgrade your system from 16.04 to 18.04 which have pulled in evince as it was still there in 16.04?

evince in my flashback 18.04 session is working fine. Atril in synaptic package manager is mentioned as mate's document viewer.

Regards!

---

### Post by ajgreeny on 2018-10-04
Perhaps Ubuntu itself still uses evince; I use Xubuntu so should have checked.

---

### Post by barben360 on 2018-10-05
Answering all questions:

- okular works, any other work (currently I open my pdf with Google Chrome). Only evince doesn't work but it is the one integrated with Ubuntu, it's simple and fast and I'm used to it so I'd like to get it working.
- My system has been cleanly installed and evince was still working a few days ago.
- Atril is default pdf reader from MATE. However it is in Ubuntu 18.04 repo and works.

Note: I have the exact same clean install on my laptop and evince works.

I also tried to install evince as a snap package from Ubuntu Software, it works (though it can only access the documents from my home, which is not interesting for me as most of my documents are on a secondary drive).

---

### Post by Claus7 on 2018-10-05
Hello,

> **barben360 said:**
> Answering all questions:

- My system has been cleanly installed and evince was still working a few days ago.


then if it is system related, if you load a usb stick at the same computer, launch evince and still does not work, then I guess that either an update caused the issue or it is graphics card related.

Some suggestions:
i)try ubuntu from usb and if it is working, try to update every package and check again  
ii)check a different flavor of ubuntu
iii)change your theme, yet, if it was theme related you should have observed some messages
iv)reinstall your graphics card drivers
EDIT v) maybe you have tried it yet, close all programs and try to launch evince->sometimes if a new configuration is taking place or something was closed unexpectedly, cpu usage increases a lot. If you do not care for your desktop to run high for a minute or so, the problem might get fixed, since as you have mentioned, you are not getting any messages while evince is launched (especially if your system has low cpu and/or memory). Actually, if you open evince from terminal, what you will see is all the recent files evince has opened. There might be a file that caused that issue.
vi) instead of launching evince from terminal as: evince, launch it by opening a specific file (e.g. evince test.pdf), this might avoid a recent document failure
vii) have you tried to launch evince as root - is it opening?

Regards!

---

### Post by barben360 on 2018-10-09
> **Claus7 said:**
> Hello,



then if it is system related, if you load a usb stick at the same computer, launch evince and still does not work, then I guess that either an update caused the issue or it is graphics card related.

Some suggestions:
i)try ubuntu from usb and if it is working, try to update every package and check again  
ii)check a different flavor of ubuntu
iii)change your theme, yet, if it was theme related you should have observed some messages
iv)reinstall your graphics card drivers
EDIT v) maybe you have tried it yet, close all programs and try to launch evince->sometimes if a new configuration is taking place or something was closed unexpectedly, cpu usage increases a lot. If you do not care for your desktop to run high for a minute or so, the problem might get fixed, since as you have mentioned, you are not getting any messages while evince is launched (especially if your system has low cpu and/or memory). Actually, if you open evince from terminal, what you will see is all the recent files evince has opened. There might be a file that caused that issue.
vi) instead of launching evince from terminal as: evince, launch it by opening a specific file (e.g. evince test.pdf), this might avoid a recent document failure
vii) have you tried to launch evince as root - is it opening?

Regards!

I tried everything on my own distro: deinstalling, purging configuration, closing everything, upgrading graphics card drivers running from terminal, I still can't get it to run and I'm not getting any log...

---

### Post by Claus7 on 2018-10-09
Hello,

I do not know if you will find any luck in this link:
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1386120](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1386120)

especially post #4.

Regards!

---

### Post by barben360 on 2018-10-09
I found the problem!
The problem was about a folder 'fontconfig' I had created in ~/.config to have colored emojis. It was root-accessible only while evince was trying to read its content when starting (it probably looped on that action since one CPU core was 100% busy). I simply removed the folder and now it just starts.

---

