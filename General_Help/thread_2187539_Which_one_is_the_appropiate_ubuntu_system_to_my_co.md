---
title: "Which one is the appropiate ubuntu system to my computer?"
date: 2013-11-12
forum: General Help
---

### Post by gbarreras93 on 2013-11-12
Hello all,
a week ago I installed Ubuntu 12.04 in my computer. 
My computer was overheating for no apparent reason. Well, it was the graphic card driver thing.
My computer is  Sony Vaio Intel i5 with a ATI Mobility Radeon HD 5650 and 6GB DDR3.
I spent so much time searching in this forum, among other ones.
I tried different relaseases but any of they seemed to work fine.
What I could read is ATI stopped updating their driver for Ubuntu. There are some open source drivers. However, any worked for me.

Besides, I installed BackTrack 5 R3, which is based on Ubuntu 10.04.3 LTS and following this link [http://www.backtrack-linux.org/wiki/index.php/Install_OpenCL](http://www.backtrack-linux.org/wiki/index.php/Install_OpenCL) I could fix the problem. This is, it seems to work fine with that ubuntu version and the driver provided in that BackTrack page.

So, my question is the following: What ubuntu version should I install to avoid overheating problems related to graphic card incompatibilities?
Thanks.

---

### Post by deadflowr on 2013-11-12
AMD drivers still support radeonhd5xxx and up.
They dropped support for 4xxx and down.

But it could be for naught, as I've found both nvidia and amd closed-source drivers to be hit or miss at times.

more
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by gbarreras93 on 2013-11-12
So you say I can run Ubuntu 12 or Ubuntu 13 with a stable release of ATI Radeon Hd 5xxx drivers?

---

### Post by deadflowr on 2013-11-12
> **gbarreras93 said:**
> So you say I can run Ubuntu 12 or Ubuntu 13 with a stable release of ATI Radeon Hd 5xxx drivers?

Possibly.

I would just state that AMD says they still support the 5XXX cards.

Whether that support is actually good or not good is something I wouldn't know...

---

### Post by QIII on 2013-11-12
AMD still supports the HD 5000 series and they work just fine with Saucy.

---

### Post by gbarreras93 on 2013-11-13
I've just installed Ubuntu 13.10. I switched the ATI controller from the privative to the open source X.Org one.
After reboting, ati card is at +75 ºC, obviously much warmer than running Ubuntu 10.4. Is this the right controller to Mobility Radeon HD 5650?
[ATTACH=CONFIG]247803[/ATTACH]
Sorry about being in spanish, but you can guess :D.

---

### Post by gbarreras93 on 2013-11-21
Hey, I'm reopening the thread again.
A few hours ago I used aircrack-ng to decrypt a .cap file (Don't yell at me, I was only doing my homework :D).
The interesting thing is I used dictionary cracking, with the "/etc/dictionaries-common/words", which is a plain text file with 99K words in it.
I executed the aircrack-ng command in this ubuntu 13.10 machine and my computer turned off in less than one minute. I did it twice for being sure, the second time I had let the computer rest a while before turn it on again.
I also tried that from my BackTrack R5 (Ubuntu 10.04) in command line mode, The computer was overheating quickly as well, but since it hadn't have to support the graphic system, it could finnish the task in slightly more than 1 minute.
Can you believe it? 
As far as I know, command line does not overload the graphic card. Not even aircrack-ng running in the console in Ubuntu graphic card uses grapic card. Therefore, aircrack-ng execution has overloaded CPU up to activate the security turn off.
How can a 99K words file can beat a Intel i5 2 x 2.67 GHz Processor?
I'm too confused about all this Ubuntu drivers staff. So I let you check my Hard Info report. (by the way, at the top of the file it says the computer has 4 cores instead of 2, which makes me even more confused)
I couldn't upload the file here because it exceeded the maximum size for a txt file, so here it is:
[https://www.dropbox.com/s/lcx2acggr7mige8/hardinfo_report.txt](https://www.dropbox.com/s/lcx2acggr7mige8/hardinfo_report.txt)
PD: My computer exceeded hight temperature levels (not critical, though) while doing the report's benchmark tests.
PD: If there is any risks for sharing this information file, please tell me.
Thank for your help.

---

