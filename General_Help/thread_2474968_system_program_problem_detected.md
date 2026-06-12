---
title: "system program problem detected"
date: 2022-05-12
forum: General Help
---

### Post by cam17 on 2022-05-12
When I boot up ubuntu 20.04.1 I get a pop saying there is a syste program problem. How can I determine what this problem relates?

---

### Post by TheFu on 2022-05-13
Check the log files.

---

### Post by cam17 on 2022-05-14
I found the problem. In the /var/crash logs a report for an App was logged. The problem occurs when the app is running and Ubuntu is restarted.

---

### Post by mIk3_08 on 2022-05-15
> **cam17 said:**
> I found the problem. In the /var/crash logs a report for an App was logged. The problem occurs when the app is running and Ubuntu is restarted.
What is the installed application that causes your Linux Ubuntu Operating System to restart? Can you name it, so the community may know/aware of that application that causes your Linux Ubuntu Operating System  to restart when its running. Thanks a lot and cheers.

---

### Post by mIk3_08 on 2022-05-16
> **cam17 said:**
> I found the problem. In the /var/crash logs a report for an App was logged. The problem occurs when the app is running and Ubuntu is restarted.
Hey can you elaborate more about your issue. The community are willing to help you even though some of them are volunteered but they are willing to help you with your concern. And also you can help others in this community with the same issue as you are. Regards and Cheers.

---

### Post by lazlo-lebrun-q on 2022-07-11
I had the same problem on current Ubuntu Mate.

Delete the file in /var/crash and the problem did not return.

But why aren't the files in /var/crash listed in the log file viewer from Mate?
I have scrutinized for hours all logs there and did not find anything...
:(

---

