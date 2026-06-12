---
title: "How to Troubleshoot Laptop Resume Failure 14.4"
date: 2014-09-02
forum: General Help
---

### Post by 7-webmaster on 2014-09-02
About 25% of the time when I open the lid of my laptop running Ubuntu 14.4 the system does not resume.  It just sits there with the screen blank, the keyboard dead, and no disk activity.  The only way out is to power off and back on again which, of course, wipes out everything I was working on when I closed the lid.  When the system resumes Ubuntu reports EIGHT crashes, which I diligently transmit, hoping for some improvement in resume support.  The system has been doing this since I bought it, and the problem has not changed in behavior since 12.4.

Since the screen and keyboard do not work and the laptop is not listening to the network how can I troubleshoot this problem?  I cannot go to the OEM because the system is only supported for Windoze.  When I look at the dmesg output after the reboot it starts with the reboot, with no knowledge of what happened before, which is of course understandable since the memory was cleared by the power off.

---

### Post by 7-webmaster on 2014-11-01
I have been reporting here and elsewhere that I have not been able to get Ubuntu to resume reliably since 12.04.  EVery time I dutifully submit the crash reports but the system still does not work, and I have to power my laptop off and back on, throwing away everything I was doing before I closed the laptop.  I have repeatedly posted here and elsewhere on this fundamental flaw in the system, but I get no feedback.  After over 2 years I am no longer willing to wait until the volunteers who specialize in solving these problems get around to it.  I want to know how to determine where the problem is so I can go in and fix the code myself.

---

### Post by grahammechanical on 2014-11-01
This is a user forum. We do not fix bugs. And if there is a bug in Linux then all that the Quality Assurance team can do is pass the bug upstream to the developers who maintain the code that has the bug.

Linux developers will put the bug fix in the next kernel to be released rather than back port the fix to an earlier kernel. Ubuntu developers bring these newer Linux kernels into the next release of Ubuntu and then back port them to an earlier LTS release during the six month "point" releases of the LTS.

[https://help.ubuntu.com/community/PowerManagement/Hibernate](https://help.ubuntu.com/community/PowerManagement/Hibernate)

[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

Regards.

---

### Post by ibjsb4 on 2014-11-02
> EVery time I dutifully submit the crash reports but the system still does not work
About your crash reports.

1. Apport collects potentially sensitive data, such as core dumps, stack traces, and log files. They can contain passwords, credit card numbers, serial numbers, and other private material.

2. During the development release we already collect thousands of crash reports, much more than we can ever fix. Continuing to collect those for stable releases is not really useful

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by Bucky Ball on 2014-11-02
Thread closed.

See here: [http://ubuntuforums.org/showthread.php?t=2249000](http://ubuntuforums.org/showthread.php?t=2249000)

Your other threads regarding this are closed. People did help you. Instead of quadruple posting what you do is 'bump your thread every 24 hours or so if you are getting no response. That easy. In future, DO NOT duplicate, triplicate, quadruple post (or any other amount of replicas regarding the same problem). 

Just 'bump' the thread by simply posting 'bump', or better still, what you have tried in the last 24 hours to fix it.

(PS: I found no thread from two years ago regarding this issue. November 2013, but that was 13.10.)

---

