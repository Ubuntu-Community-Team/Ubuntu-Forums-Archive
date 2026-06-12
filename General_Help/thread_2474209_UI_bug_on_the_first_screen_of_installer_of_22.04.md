---
title: "UI bug on the first screen of installer of 22.04"
date: 2022-04-24
forum: General Help
---

### Post by ibobak on 2022-04-24
It would be good if you forward this to the developers:

[IMG]https://i.ibb.co/z6m9B2x/ksnip-20220424-100057.png[/IMG]

---

### Post by guiverc on 2022-04-24
I suspect your settings are the cause of this issue, please check.

The [minimum display resolution specification for Ubuntu Desktop]("https://help.ubuntu.com/community/Installation/SystemRequirements") is

> VGA capable of 1024x768 screen resolution

Does your `virtualbox` settings meet that, as the only time the issue has appeared, is when people use resolutions below the minimum documented.

FYI:  The default for `virtualbox` does not meet that standard, until you change it.

Thank you for taking the time to report this issue and helping to make Ubuntu better, it's best if reported on a bug tracker (*details of screen resolution would have then been provided*).  Details can be found here - [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

