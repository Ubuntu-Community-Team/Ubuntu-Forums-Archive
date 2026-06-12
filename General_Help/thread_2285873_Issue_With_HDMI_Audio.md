---
title: "Issue With HDMI Audio"
date: 2015-07-08
forum: General Help
---

### Post by georgec10_05 on 2015-07-08
Hello All,

I'm fairly new to Ubuntu and Linux in general. I am running Ubuntu version 14.10 x64 on an HP Pavilion dm1-3025dx. I would like to hook this computer up to my TV via an HDMI cable. The video displays just fine but am not getting any audio out of the TV. Instead audio still comes out of the laptop's speakers. When I was running Windows 7 on this machine, the audio played through the TV without issue. What should I start looking at to solve this problem? Thanks in advance for the help.

---

### Post by papibe on 2015-07-08
Hi georgec10_05. Welcome to the forum ):P

Have you tried opening 'Sounds' and tried to change the default audio there?

Could you open a terminal, run these commands and post back the results (you can copy/paste the text)?
```
aplay -L

lspci -nnk | grep -iA2 vga
```

Regards.

---

### Post by georgec10_05 on 2015-07-09
Going into Sounds worked. Thanks for the help.

---

### Post by Bucky Ball on 2015-07-09
Good news you got it working. Just FYI I wanted to throw in a side note. 14.10 will reach end-of-life on July 23rd, so you will need to upgrade to a supported release at that time. Your options are 15.04 (support until Jan 2016) or the current long-term support release 14.04 LTS (support until April 2019). 

Good luck however you go and please mark thread as solved (see second link in my signature). Thanks. ;)

---

