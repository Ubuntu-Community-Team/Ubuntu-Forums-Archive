---
title: "Antivirus software"
date: 2017-01-24
forum: General Help
---

### Post by gordie692 on 2017-01-24
hey guys I've been hearing a lot of talk on Ubuntu needing an antivirus software so I downloaded comodo but it didn't install in software center do I need one I was just thinking maybe having one for my system but for my Windows friends system

---

### Post by howefield on 2017-01-24
Moved to the *"General Help"* forum.

Ubuntu doesn't necessarily need an anti virus solution but there are valid reasons for running one, see here for details : [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

What was the name of the file that you downloaded and where did you download from ? You'll likely need to install via the command line.

ClamAV is an anti virus solution already in the repositories so it would be easier to install, that's not an endorsement of quality just that it is there.

---

### Post by HermanAB on 2017-01-24
ClamAV is in the repos, but you need to read up on it to know how to actually use it.

---

### Post by ajgreeny on 2017-01-24
If it any comfort to you I have been running *ubuntu family OSs for eleven years now having started with 5.10 properly, and without Windows left on my machines, apart from a VM in VBox for one specific use.

As a result of using only Linux I do not feel the need for any antivirus software; there are no Linux viruses in the wild, and I do not feel I should worry about passing on any viruses to those I might send any files to, all of whom use Windows. They all use an antivirus and it is up to them to safeguard their own systems.

Personally I have seen no problems of any sort related to malware or viruses in those 11 years of use, and as I've said to others in the past, the weak link in any OS is usually the person pushing the buttons.

---

### Post by SuperFreak on 2017-01-24
[https://www.virustotal.com/](https://www.virustotal.com/)
Provides a free online antivirus that does not require an install.

---

### Post by g33zr on 2017-01-24
Many Nixers claim that you don't need antivirus software if you run Linux, but with hackers targeting Linux servers and the like, it probably doesn't hurt to install and run something like ClamAV. I also installed a root kit hunter, i.e., rkhunter and run both periodically. Neither takes up much memory and both are easy to use. You might also want to consider running firewall software such as ufw or gufw. Some folks will argue that it's overkill, but if it gives you a semblance of peace of mind, go for it.

---

### Post by &amp;KyT$0P# on 2017-01-24
See [this]("https://ubuntuforums.org/showthread.php?t=2337052&p=13546076&viewfull=1#post13546076").

---

### Post by deadflowr on 2017-01-24
> **gordie692 said:**
> hey guys I've been hearing a lot of talk on Ubuntu needing an antivirus software so I downloaded comodo but it didn't install in software center do I need one I was just thinking maybe having one for my system but for my Windows friends system

What exactly was the problem with the software center.

You might try the command line alternative:
```
sudo apt install /path/to/the/downloaded/deb-file.deb
```
replace the obvious path to file line with the correct path to the file.

Alternative to the command line method is the tried and true gdebi method.
install gdebi
```
sudo apt install gdebi
```
and then you can install any downloaded Ubuntu .deb files using that.
Which works fairly well, or has for me and countless others.

---

### Post by poorguy on 2017-01-24
I would recommend downloading and installing firejail sandbox for added security.

[https://firejail.wordpress.com/](https://firejail.wordpress.com/)

You can download the latest version here.

[https://sourceforge.net/projects/firejail/files/firejail/](https://sourceforge.net/projects/firejail/files/firejail/)

New versions are always being released so I would check the download link regularly.

---

### Post by SeijiSensei on 2017-01-24
> **g33zr said:**
> Many Nixers claim that you don't need antivirus software if you run Linux, but with hackers targeting Linux servers and the like, it probably doesn't hurt to install and run something like ClamAV.
Ordinary people running desktop Ubuntu behind a masquerading router aren't being targeted the ways servers sitting directly on the Internet are.  I run mail servers that use ClamAV (via MailScanner) and manage an outbound gateway for a couple hundred users that uses SquidClamAV to scan every object downloaded over HTTP through the gateway's Squid proxy.  In both instances I'm scanning to block Windows viruses coming into the system or network.

I've never used an antivirus product on a desktop computer running Linux either Ubuntu, or Fedora when I was using that back in the day.  I can see running ClamAV if you have a Samba server that multiple people connect to from Windows desktops to make sure the shared resources are free of malware.  But for ordinary desktop Linux users antivirus is pretty much unnecessary unless it provides some psychological peace-of-mind.

---

