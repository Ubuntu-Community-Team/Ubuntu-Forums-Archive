---
title: "How do i remove the ubuntu reports and the amazon button"
date: 2019-05-29
forum: General Help
---

### Post by placidchat on 2019-05-29
In disco dingo, there's a button for amazon on the taskbar, how do i remove that? And also i noticed there are ubuntu-reports processes that are running. How do i remove them all?

---

### Post by cruzer001 on 2019-05-29
> **placidchat said:**
> i noticed there are ubuntu-reports processes that are running. How do i remove them all?
Are these processes by chance called "apport"?

---

### Post by Rubi1200 on 2019-05-29
> **placidchat said:**
> In disco dingo, there's a button for amazon on the taskbar, how do i remove that? And also i noticed there are ubuntu-reports processes that are running. How do i remove them all?

1. you can usually right click the icon and choose to remove from favorites

2. where are you seeing these reports?

---

### Post by grahammechanical on 2019-05-29
You can also open System Settings>Security & Privacy. The Diagnostics tab might be what you want. 

Regards

---

### Post by deadflowr on 2019-06-01
ubuntu-reports differ from apport.
This is ubuntu reports
[https://packages.ubuntu.com/disco-updates/ubuntu-report]("https://packages.ubuntu.com/disco-updates/ubuntu-report")
It's part of the anonymous collection process they've started to get a better understanding of how users setup their Ubuntu installs.
Seen here for 18.04:
[https://www.ubuntu.com/desktop/statistics]("https://www.ubuntu.com/desktop/statistics")

Since it's just a package you can go ahead and remove it if you want.
Especially if it's gone rogue for some reason.
Removing it should stop/kill those pesky runaway processes.

---

### Post by cruzer001 on 2019-06-01
I have added your post to my collection, thanks deadflowr :)

---

### Post by deadflowr on 2019-06-01
>  there's a button for amazon on the taskbar, how do i remove that
Removing the amazon launcher can be/should be done/doable with this terminal command
```
sudo apt remove ubuntu-web-launchers
```

Back to the Ubuntu-report package
For what it's worth, they just updated the ubuntu-report package on 19.04 so that might be why it was running various processes.
(But that's a just a random guess)

When they updated it? I don't know, but sometime within the last week.
(since that was the last time I ran a regular non-security update on my 19.04 install)

Which is really why I posted in the first place, I read this thread a few days ago and didn't give it much thought until I saw the update.

---

