---
title: "Headless Server Goes Completely Offline While Still Turned On"
date: 2021-09-10
forum: General Help
---

### Post by czarian on 2021-09-10
I have a server running Ubuntu desktop 20.04 headlessly, with Teamviewer and ssh set up to control it.  

After a seemingly random interval (usually 1-3 days) the server becomes completely inaccessible despite still being powered on.  I am forced to restart it without being able to see what happened because it is only accessed via network.

Any ideas on how to troubleshoot this? Is there somewhere like event viewer in windows that I can check the logs on?  


Thank you for any help.

---

### Post by Doug S on 2021-09-11
Check log files in /var/log and it subdirectories. In particular, check /var/log/kern.log and /var/log/syslog.

---

### Post by czarian on 2021-09-15
After checking the log I found something strange that seems to line up with one instance of the server going offline.

Within  /var/log/syslog it seems to be failing to get a new DHCP lease, but I'm  not sure why.  I can see several instances of this happening in the  file.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289174&stc=1[/IMG]
[https://pastebin.ubuntu.com/p/jtPmkR3cdg/](https://pastebin.ubuntu.com/p/jtPmkR3cdg/)
After that the log is flooded with autossh failing to connect.

In another spot the log is also flooded with
```
systemd-resolved[649]: Failed to send hostname reply: Invalid argument
systemd-resolved[649]: message repeated 2 times: [ Failed to send hostname reply: Invalid argument]
systemd-resolved[649]: Using degraded feature set (UDP) for DNS server 1.1.1.1.
```
Not sure if this is related but it seems to also happen around the time that freedesktop.nm_dispatcher comes up.

Thanks for your help, any insight is much appreciated.

---

