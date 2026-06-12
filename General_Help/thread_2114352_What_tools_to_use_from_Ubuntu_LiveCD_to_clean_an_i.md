---
title: "What tools to use from Ubuntu LiveCD to clean an infected Windows computer"
date: 2013-02-09
forum: General Help
---

### Post by greavette on 2013-02-09
Hello,

A family member has asked me to assist with cleaning up her PC.  Security Essentials found a trojan and worm and other malware (she doesn't remember the names).  I'm suggesting we use a Linux Live CD to scan her harddrive and clean it of any and malware.

What tools would you suggest I use on the live cd to clean this harddrive?

Thank you.

---

### Post by haqking on 2013-02-09
> **greavette said:**
> Hello,

A family member has asked me to assist with cleaning up her PC.  Security Essentials found a trojan and worm and other malware (she doesn't remember the names).  I'm suggesting we use a Linux Live CD to scan her harddrive and clean it of any and malware.

What tools would you suggest I use on the live cd to clean this harddrive?

Thank you.

there are tons of AV and malware scanners out there, all as useless as the next ;-)

This is about as good as any, download and burn it then boot to it:

[https://support.kaspersky.com/viruses/rescuedisk](https://support.kaspersky.com/viruses/rescuedisk)

Best AV is the user and modified habits.

Peace

---

### Post by cwsnyder on 2013-02-09
**clamav** from the repositories should be installed to scan and remove viruses.  If you want a GUI, you can install **clamtk**.  **freshclam** from the CLI would refresh the virus definitions, while **clamscan -r /media/win** on the CLI would do the actual scanning of the drive after mounting your Windows drive on the folder /media/win.

---

### Post by greavette on 2013-02-09
Agreed...I think she's learned a hard lesson.

Much appreciative for your suggestion.

Thank you.

---

### Post by Marzata on 2013-02-11
You better clean Windows and replace it with some nice Xubuntu Linux.

---

### Post by hawthornso23 on 2013-02-11
\begin{joke}
To fix windows with the ubuntu live CD try clicking "install".
\end{joke}

---

### Post by Marzata on 2013-02-11
> **hawthornso23 said:**
> \begin{joke}
to fix windows with the ubuntu live cd try clicking "install".
\end{joke}

:d

---

### Post by Bufeu on 2013-02-11
Kaspersky Rescue Disk: [http://support.kaspersky.com/4162](http://support.kaspersky.com/4162)
BitDefender Live CD: [http://download.bitdefender.com/rescue_cd/](http://download.bitdefender.com/rescue_cd/)
F-Secure Rescue Disk: [http://www.f-secure.com/en/web/labs_global/removal-tools/-/carousel/view/142](http://www.f-secure.com/en/web/labs_global/removal-tools/-/carousel/view/142)
AVG Rescue Disk: [http://www.avg.com/us-en/226386](http://www.avg.com/us-en/226386)
TrendMicro Rescue Disk: [http://www.trendsecure.com/Info/Rescue_Disk/html/download.html](http://www.trendsecure.com/Info/Rescue_Disk/html/download.html)

ESET NOD32 Antivirus for Linux (trial): [http://www.eset.com/download/home/detail/family/71/](http://www.eset.com/download/home/detail/family/71/)

Some tools you can use to remove malware from Live-CD.

---

### Post by psilentrain1 on 2013-02-11
> **hawthornso23 said:**
> \begin{joke}
to fix windows with the ubuntu live cd try clicking "install".
\end{joke}

=d>

---

### Post by SantaFe on 2013-02-11
> **Marzata said:**
> You better clean Windows and replace it with some nice Xubuntu Linux.

I always use this stuff myself! :D:D

---

### Post by Mark Phelps on 2013-02-11
OF the links provided in post #8, I have generally found the Kaspersky and AVG tools to be the best.

Not only are these FREE (!) but when you burn their CDs and boot from them, they actually crank up Linux.

How's that for irony!

---

### Post by greavette on 2013-02-12
Nicely done...I love the comments.

She found it quite easy to connect her wireless and install Teamviewer (with my instruction over the phone) so maybe after this is over she'll want to delve more into using Linux...I can only hope!  ;)

---

