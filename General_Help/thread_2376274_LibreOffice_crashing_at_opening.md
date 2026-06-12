---
title: "LibreOffice crashing at opening"
date: 2017-11-01
forum: General Help
---

### Post by robpeteuk on 2017-11-01
Hi, I have just installed Ubuntu after running Lubuntu for a year or so with no probs. After installation I found that immediately I tried to open a document with libreoffice it crashed and crashed the whole system needing a restart. I tried older versions of lo and also oo. All had the same result. I am guessing it may be some sort of conflict with the combination of my graphics card, a Nvidia GeoForce 7025, ubuntu 16.04 and LO. The snap version of LO installed from the software centre v 5.3.4.2 so far seems to work but I cannot open files with it without first moving them to my home folder. Otherwise when trying to open them I get an error message such as  ""Access to /media/rob/data/reply puppystandby.abw was denied"" message. Neither can I open folders other than in my home folder from the menu of LO. any suggestions  Rob

---

### Post by HermanAB on 2017-11-01
Run soffice from a terminal to see the error messages returned by it.

---

### Post by robpeteuk on 2017-11-02
Installing from terminal gives me
(soffice:2161): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
Libre Office immediately crashes, crashing the Operating System with it. Version of libreoffice is 5.1.6.2 I think though it is difficult  to see as it crashes before I can open it. It is the version installed with Ubuntu 16.04 and that is the version of LO installed on my laptop with 16.04 which is fine. As I said the snap version seems to run fine but I cannot open files unless I move them to my home folder, which I think is something to do with snap installations.

---

### Post by robpeteuk on 2017-11-03
any ideas

---

### Post by VMC on 2017-11-03
Have you tried removing/renaming "~/.config/libreoffice"?

---

### Post by ian-weisser on 2017-11-03
Check syslog (/var/log/syslog or syslog.1) around the time of a crash.
If there are error messages related to the crash, show us.

---

### Post by robpeteuk on 2017-11-05
Needed libre office so reinstalled Lubuntu. LO now runs faultlessly. I notice the graphics driver it uses is Noveau not Nvidia 304 which was the recommended linux driver for my card. Wonder if that could be a factor. I am fine now with Lubuntu but will try ubuntu again running from USB when I have more time. Thanks for the answers.

---

### Post by mr2131 on 2017-11-30
This seems to be a recurring problem. I spent most of this spring and summer, unable to open a document in Libre Office. Bad news for a writer. This fall, it was working fine. I went to open the program today, and it's back to crashing on opening. The only changes I've made have been to install the updates that Ubuntu sends along. I would prefer to work with my Ubuntu desktop, but I'm just not able to.

---

### Post by mörgæs on 2017-12-01
Let's see if you also have Nvidia hardware. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post the results in CODE tags.

---

