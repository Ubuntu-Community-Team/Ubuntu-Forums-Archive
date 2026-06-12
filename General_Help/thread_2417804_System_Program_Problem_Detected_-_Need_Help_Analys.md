---
title: "System Program Problem Detected - Need Help Analysing Two Crash Reports"
date: 2019-04-27
forum: General Help
---

### Post by searsquid on 2019-04-27
My system is otherwise performing just fine. However, after I log in on Xubuntu, I am greeting with a dialogue box. "System Program Problem Detected." After a couple of minute of Google searching, I located where my crash reports are stored. There are only two crash reports. These reports are as follows:

#1: _usr_sbin_lightdm.0.crash
#2: _usr_sbin_ndisgtk.0.crash

I know what both of these are (I installed NDISwrapper package myself.) However, I am not really sure what else to do. I'm not sure what is causing these applications to crash. Here are my Pastebin links for the crash reports, as plain text:

NDISWrapper_Crash_Report.txt: [https://pastebin.com/1uNUVG5n](https://pastebin.com/1uNUVG5n)
LightDM_Crash_Report.txt: [https://pastebin.com/Tx4P6NT3](https://pastebin.com/Tx4P6NT3)

---

### Post by dragonfly41 on 2019-04-27
I usually just delete all crash reports in /var/crash and don't try to understand them.

---

### Post by searsquid on 2019-04-27
If I delete them, won't they just return upon reboot? I kind of want to figure out what's causing the crashes for these two programs in the first place...

---

### Post by Rubi1200 on 2019-04-27
Hi and welcome to the forums :-)

You could try running these commands in a terminal first of all to see if it helps sort out the issue:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by searsquid on 2019-04-27
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

You could try running these commands in a terminal first of all to see if it helps sort out the issue:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Thanks!

I performed those three commands, shut down, and rebooted my machine.

Unfortunately, I am still greeted with the same dialogue box upon login. :(

---

### Post by Rubi1200 on 2019-04-27
Thought that might happen but just wanted to eliminate other possibilities first.

So, you have two possibly separate issues:

1. lightdm, see this link and fixes [https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/](https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/)

2. why do you need NDISWrapper? My understanding is that it was not available for Linux past Windows XP. This might be the main cause of the errors.

---

