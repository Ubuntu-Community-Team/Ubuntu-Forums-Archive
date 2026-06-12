---
title: "Weird message after updating apt database &amp; not receiving automatic updates"
date: 2016-11-26
forum: General Help
---

### Post by chaaderf on 2016-11-26
Hi all

I think I maybe have two different problems, or they may be caused by the same problem, I don't know. Maybe someone can help?

At first, I installed Xubuntu 16.04 in October, and I've set the Software & Updates to update the system. I've selected:

Automatically check for updates: Daily
When there are security updates: Download and install automatically
When tere are other updates: Display immediately

But this has clearly not worked for me more than once during this time. I've also occasionally run manual update & upgrade on terminal and received usually a lot of updates. And sometimes I've got a message on the desktop that apt cache is outdated and I should update it, which I've done and received a lot of updates.

On the other hand, when I issue a command 'sudo apt-get udpate', I see it working as well as my previous years with *ubuntu, but sometimes - not always - I got a message after it has finished:

'AppStream cache update completed, but some metadata was ignored due to errors.'

But then, if I run 'sudo apt-get upgrade' or even 'sudo apt-get dist-upgrade' I receive updates - well if there are something to upgrade I guess. My last attempt was yesterday.

Now the questions: 
1) What should I do to get autoupdate working?
2) How to get rid of the AppStream message after running 'sudo apt-get update'?

Thank you!

---

### Post by speartip on 2016-11-26
Not sure why updates aren't working properly. Although when I'm warned of updates, I install them, & invariably there are more when I check in synaptic. I now just check manually once a week. That way I know exactly what's being installed.

As for your error message, it seems this is a known bug.
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498)
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1575248](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1575248)
It might be a good idea to subscribe to both bugs & hopefully it will get fixed.

---

### Post by Dennis N on 2016-11-26
I have a thread about the problem with automatic update checks started in July, merged there with posts from another recent thread at post #7. Both contain lots of information about this. 

[https://ubuntuforums.org/showthread.php?t=2330407](https://ubuntuforums.org/showthread.php?t=2330407)

I added a link to your report to the thread at post #9

---

### Post by ian-weisser on 2016-11-26
You have not yet shown that unattended-update is not working properly.
Lots of updates are not security updates. Your settings tell the system to ignore those. Discovering lots of uninstalled updates is expected behavior.

Look at a few days of your /var/log/unattended-upgrades/unattended-upgrades.log
The log will clearly indicate if unattended-update installed security updates, and exactly which packages were installed and when.
The log will also clearly indicate if there is a problem or failure.
If there is a problem or failure on one day, please show us (copy and paste) that entire day of the log. Just that one entire day.

---

### Post by Bucky Ball on 2016-11-26
Just a note, always 

```
sudo apt update
```

... *before* 

```
sudo apt full-upgrade
```

You should be updating before upgrading, not running the upgrade command by itself. ;)

You also only need those two commands in newer versions, not 'apt-get', just 'apt'. Try this:

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Post any and all errors you receive after any of those commands and please use code tags (first line, green link in my signature at the bottom of this post).

---

### Post by Dennis N on 2016-11-26
> What should I do to get autoupdate working?
So far, I have seen no solution offered for this observed problem in 16.04 by anyone who has experienced it. If you do find one (I haven't), please post it - thanks. 

The "problem" I am referring to here is the failure of "automatic check for updates" not "automatic updating (and upgrading)" which is the same as "unattended upgrades". Although the latter is clearly not working for you either, it will when the automatic checking is fixed.

---

### Post by chaaderf on 2016-11-28
Thank you for replies! I'll keep an eye on the situation and I'll come back later if there is something I wish to say or ask.

---

