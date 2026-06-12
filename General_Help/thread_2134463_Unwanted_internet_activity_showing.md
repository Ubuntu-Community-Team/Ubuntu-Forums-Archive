---
title: "Unwanted internet activity showing"
date: 2013-04-11
forum: General Help
---

### Post by holadebob on 2013-04-11
After noticing that it took longer than normal to open a file (jpg) in my Home folder, I turned on the Network Monitor and selected some more files, and have internet activity for about 10 seconds each time I access a file. I have noticed this behavior before, but didn't mentally connect it to network ops. After restarting the system, the suspicious activity is gone. I am assuming that someone or something is getting info from my computer without my knowledge. That's scary.

Anyone have any ideas on how to locate the source of this problem?

Thank you

---

### Post by mustafi05 on 2013-04-11
even if you chaked download updates automatically , there will be some data traffic (receiving) that does not show any graphic notification .

---

### Post by pfeiffep on 2013-04-11
GUI option may exist - here are some cli options to explore

netstat -an -c    redirect to a file
top  using batch mode
[snort]("http://www.debian-administration.org/articles/318")

---

### Post by holadebob on 2013-04-11
I have more info for those interested and thank you for the help. I have two xubuntu 12.042 computers tied together and am using system/Shared Folders set up to share certain files. 

I just ran chkrootkit and rkhunter with no errors or suspect problems. 

I have a list of jpg's in a home folder and now, when things are "normal"  if I open any of it's jpg files, the jpg image instantly displays. 
During the problem times, it doesn't immediately come up (6-7 seconds delay) and the system monitor shows about 10 seconds of network activity during that time. Each and every time. 

The coincidence makes me believe the computer is talking to someone else, either my other computer (no one is using at the time) or someone "out there in netland" is somehow getting access to my activities here. 

I realize this is a bizarre situation, but there's got to be a explanation, right? 

pfeiffep, When the problem returns, I'll try your ideas.

Thank you

---

