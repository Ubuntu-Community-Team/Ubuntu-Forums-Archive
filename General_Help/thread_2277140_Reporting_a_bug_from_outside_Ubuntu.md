---
title: "Reporting a bug from outside Ubuntu"
date: 2015-05-07
forum: General Help
---

### Post by sanssadness on 2015-05-07
Is there a way to report a bug using just a web browser instead of running the tool ubuntu-bug? For one, I don't want this tool to gather potentially sensitive information on my computer. There used to be a way to report a bug on Launchpad here: [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

But they seem to have changed it now so I can only report it using ubuntu-bug. Is there any way around this? I mean, what if I was using a Windows or Mac computer to report the bug? Surely ubuntu-bug can't be the only way. Besides, my bug doesn't neatly fit into any of the categories specified by ubuntu-bug. I want to report this problem here: [http://ubuntuforums.org/showthread.php?t=2274556](http://ubuntuforums.org/showthread.php?t=2274556)

It doesn't fit neatly into any of the categories. Please help! The bug report guide is comprehensive, but seems to indicate that there's no way to report a bug outside of ubuntu-bug. Is there no other way?

---

### Post by QIII on 2015-05-07
I think apport (the ubuntu-bug back-end) may be the only way to do it any more.

The problem with manual bug reporting is/was that they were often simply marked of as "Incomplete" because people didn't know how to provide the needed information the developers need -- which is usually gathered from logs.

The last time I reported a bug manually on launchpad I followed the initial post with half a dozen logs.  That was probably 7 or 8 years ago.

I understand your reluctance to send what might be sensitive information.  If you get on a dev mailing list, you might be able to get someone to walk you through giving them the required information without giving them any "dirty laundry" :)

You might try this as a start: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

### Post by cariboo on 2015-05-07
Have a look at [this page]("https://help.ubuntu.com/community/ReportingBugs"), scroll down to Filing bugs when offline or using a headless setup. That will tell you what you need to know.

---

### Post by sanssadness on 2015-05-07
Thanks. How would you classify the bug I described in my original post though? What is the executable path for Power Button/System Settings/Security & Privacy?

---

