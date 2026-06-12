---
title: "K/Ubuntu Security"
date: 2007-02-18
forum: General Help
---

### Post by ShareBuntu on 2007-02-18
Hello everyone,

I recently decided to switch to Kubuntu as my sole operating system after dual-booting Windows XP for a while. I've had no major problems and I'm currently testing Feisty. I have one question regarding my new operating system, and it's about security.

After a bit of browsing around I've come to understand that running an anti-virus program isn't really necessary given the obscure number of viruses that exist for the Linux environment (especially if regular backups are kept). Also, is a firewall really necessary since most ports are closed anyway?

What I'm really interested in is finding out whether you use any security tools? And if any, what tools would you recommend?

I found this page really helpful outlining the various (most popular) tools available for Linux: [https://help.ubuntu.com/community/InstallingSecurityTools]("https://help.ubuntu.com/community/InstallingSecurityTools")

---

### Post by aysiu on 2007-02-18
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by ShareBuntu on 2007-02-18
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
Thanks for the promt response, aysiu. I've found [http://psychocats.net]("http://psychocats.net") most useful in the past. The way I see it spyware and viruses are a thing of the past if you're an Ubuntu user. It seems as if rootkits however carry more weight than the traditional malware we're used to coming from Windows environments. Are both rkhunter and chkrootkit available for KDE?

---

### Post by aysiu on 2007-02-18
Any application that works in Gnome will also work in KDE.

Applications have ideal (mainly for visual purposes) environments, but they work anywhere (Gnome, KDE, XFCE, IceWM, Fluxbox, etc.).

---

### Post by TheWizzard on 2007-02-18
> **'Ace[of]Bytes said:**
> Thanks for the promt response, aysiu. I've found [http://psychocats.net]("http://psychocats.net") most useful in the past. The way I see it spyware and viruses are a thing of the past if you're an Ubuntu user. It seems as if rootkits however carry more weight than the traditional malware we're used to coming from Windows environments. Are both rkhunter and chkrootkit available for KDE?

both rkhunter and chkrootkit are command line programs and don't use gnome or kde libraries. 

the practice i'd recommend: 
- do a weekly scan with both. you can use cron to do this automatically. 
- mail the output and forward it to you.

here is the script i use. it is not elegant, but does the job. 



```
#!/bin/bash

#f-prot virus definities updaten:
/usr/lib/f-prot/tools/check-updates

#scannen op virussen en het resultaat mailen:
#f-prot /bin /dev /home /lost+found /misc /net /proc /sbin /srv /tmp /var /boot /etc /lib /media /opt /root /selinux /usr -ext | mail -s "f-prot output alpha" root

f-prot /bin /etc /initrd /lib /media /opt /root /srv /tmp /var /boot /dev /home /lost+found /proc /sbin /usr -ext | mail -s "f-prot output alpha" root



#scannen op rootkits en het resultaat mailen:
chkrootkit 2>&1 | mail -s "chkrootkit output alpha" root


#rkhunter rootkit definities updaten:
rkhunter --update

#scannen op rootkits en het resultaat mailen:
rkhunter -c --report-mode --cronjob 2>&1 | mail -s "rkhunter output alpha" root



# 2>&1 sends the error output to the same place as the standard output
# see: http://www.luv.asn.au/overheads/bash.html
```

---

### Post by ShareBuntu on 2007-02-19
Thanks for the script, TheWizzard. I've settled on chkrootkit, rkhunter and set up iptables as a firewall using Guarddog. I'm still not sure about anti-virus. I don't mind installing an anti-virus package to manually scan my system but I'm not really interested in real-time protection as this would consume valuable system resources.

Can anyone recommend a package with scan-only type functionality? Would KlamAV do the trick?

---

