---
title: "Thunderbird locked accounts on Mate, and Bionic. XFCE works fine"
date: 2018-05-14
forum: General Help
---

### Post by freacert on 2018-05-14
Hello,

I am using Thunderbird 52.7.0 64 bit on three operating systems and three partitions, with a shared home directory for private stuff and the Thunderbird mail and settings directory. The normal home folders of the operating systems have a symbolic link to the (hidden) .thunderbird folder in that shared home directory. 

Last week I installed Ubuntu 18.04, which is now installed besides Ubuntu 16.04 Mate, and Ubuntu Media 16.04 which runs on XFCE, 

Before I had no problem to open my mails in any of the operating systems, (I replaced Antergos for Ubuntu 18.04). 

Now suddenly the Ubuntu 18.04 and the Ubuntu Mate, show the accounts I have set up in Thunderbird, but I cannot see any folders or mail. Neither the RSS feeds are showing up. 

I checked the permissions, and double checked, reset them, and all the operating systems have the same user name and use the same password. 

When I open Thunderbird as root (sudo Thunderbird from terminal)  I can see the mail in the other two operating systems where I as a normal user were not able. But I have read that this naughty behavior can wreck my configuration even more, so it was just a test. 

Any ideas?

(cross posted this question here: [https://support.mozilla.org/en-US/questions/1217616](https://support.mozilla.org/en-US/questions/1217616)

---

### Post by freacert on 2018-05-21
nobody?

---

### Post by PaulW2U on 2018-05-21
> **freacert said:**
> When I open Thunderbird as root (sudo Thunderbird from terminal)  I can see the mail in the other two operating systems where I as a normal user were not able. But I have read that this naughty behavior can wreck my configuration even more, so it was just a test. 
if you have been opening Thunderbird as root then it is highly likely that the ownership of some of the files or directories under ~/.thunderbird has been changed from your user to root. That has prevented you from seeing any folders or mail within Thunderbird when you are logged on as yourself.

I think you need to check the ownership of all files and directories under ~/.thunderbird and make appropriate changes.

Please post back with what you find and ask for instructions if you are unsure of how to change file/directory ownership.

---

### Post by freacert on 2018-05-21
Thank you Paul

> **PaulW2U said:**
> I think you need to check the ownership of all files and directories under ~/.thunderbird and make appropriate changes.


But this is not the case. Before I logged in as root, I had the problem, to make myself sure, I recursively added ownership again to myself. And if only root would have ownership, then I would not be able to use Thunderbird in XFCE (ubuntu media 16.04.4)

---

