---
title: "ubuntu locking up forcing a hard reboot."
date: 2019-09-25
forum: General Help
---

### Post by syngreis on 2019-09-25
computer locking up completely.

here are the logs from gnome-system-log

[https://pastebin.com/LmTh2PQE](https://pastebin.com/LmTh2PQE)

all the info i got, had to post quick before it locks up again.

---

### Post by TheFu on 2019-09-25
It is the computer or just the GUI?
Tried using <cntl><alt>-F1 .... F3 to get to a different TTY.
About a year ago, my laptop appeared to lock up.  I was able to ssh in from a different computer.  It was just the GUI, not the whole computer.

In the end, it turned out to be the swap was much too small and huge programs were demanding more RAM than the system had.

**dmesg** would show most hardware issues.  Failing HDDs/SSDs can cause a system lock up.

I skimmed the log. Nothing in there jumped out. Some systemd stuff is the only thing I'd research more.  Gnome stuff constantly spews issues. All unimportant.  Remove all the gnome issues from the list and some issue much jump out easier.

I'd check which programs were using lots of CPU and RAM - use **top** for that.
**free -hm** will show how swap is being used up or not.

You can have the logs retained between boots, if you like. There's a setting.  To search most of them, use 
**sudo egrep -i 'error|warn' /var/log/*g**

---

### Post by syngreis on 2019-09-25
still new to linux.

dmesg im not sure what i should be looking for.

free -hm produced these results...


              total        used        free      shared  buff/cache   available
Mem:          7.7Gi       1.7Gi       2.4Gi       518Mi       3.6Gi       5.2Gi
Swap:         975Mi       1.0Mi       974Mi

for top i dont see anything jumping out. memory hardly used but gnome disk is taking up easily 80%+ cpu.

egrep produced these results...[https://pastebin.com/rkrGj66i](https://pastebin.com/rkrGj66i)

---

### Post by TheFu on 2019-09-25
Updated:
Can't tell the swap for certain since the post above isn't wrapped in "code" tags.  Adv Reply/Edit # - use it like "quote" or "bold" tags. Please edit the existing post.  Looks like I misread the output and almost no swap is being used. Code tags would have prevented that mistake. Sorry.

You should look for errors and warnings in all output.  Then do research on any reported problems.

I don't use many of the things in the output.  I don't use Gnome. I don't use snaps. I don't use 18.04.  Any desktop of mine will have 4.1G of swap. Less than 1G of swap is anaemic, IMHO, especially if you use google's browser, which will easily grow larger than 4GB.

Looks like there are some permissions issues too - usually caused by abusing sudo/root.  Don't use sudo with any GUI programs.

---

