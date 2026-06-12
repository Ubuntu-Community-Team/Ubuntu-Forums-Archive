---
title: "Screen on as lid is closed"
date: 2017-08-21
forum: General Help
---

### Post by haralde on 2017-08-21
Hello, I just installed Ubuntu 17.04 on my Kaby Lake Dell XPS 13. The laptop came with Win 10 and I am now dualbooting it with Linux. Relatively new to Ubuntu, but I have managed to make most things work as they should, but I have one major problem. Whenever I finish my work and close the lid, it only puts the computer in locked mode. It does not turn the screen off.

I do not seem to find any settings for this. If anyone on here could find an solution for me I would be very happy. Thanks.

---

### Post by Futant on 2017-08-21
Hi, welcome to the forum. You should be able to change what happens when you close the lid in the power management settings, click on the battery icon in the top right of the screen and choose 'power settings'.

---

### Post by haralde on 2017-08-21
Thank you for your reply, and your welcome. I have checked the power/battery settings but they're allright, I think It's more of a bug-thing.

---

### Post by Futant on 2017-08-21
In that case things might get a bit more complicated :P 

This is a problem that seems to come up a lot... If you haven't updated yet, try that first. I had the same issue a while ago and as far as I can remember an update sorted it out one day. 

Have a look through syslog and Xorg.log (in /var/log) for any errors or messages that stand out, post them here (in code tags or as attachments if they are very long). Try using different drivers - open 'additional drivers' and choose one of the other options - if you're using the open source drivers try the proprietary ones and vice versa. You could also try installing a newer kernel, although this could produce other issues. It's easy to go back though.

Check for similar bug reports and if needs be [file your own]("https://help.ubuntu.com/community/ReportingBugs#Complete_the_bug_report_filing_process"). This helps the developers improve Ubuntu.

If you want to get into editing system files there are a number of things you could try (a quick search threw up a few options), but you run the risk of causing other problems. It is quite likely that the issue will get fixed in an update soon...

---

