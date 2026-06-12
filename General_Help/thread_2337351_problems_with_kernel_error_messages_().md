---
title: "problems with kernel error messages (?)"
date: 2016-09-16
forum: General Help
---

### Post by carljohnny on 2016-09-16
Hi! I recently installed ubuntu 16.04 on my new laptop so I'm a complete noob. Here comes a very lengthy explanation of my troubles (sorry for that)

Installation went fine (at the third try) except some ominous error messages. The same error messages tend to pop up whenever I'm booting the system or changing user. I tends to go to fast for me to actually see what it says exactly and I don't really know where else to find it. In the kern.log file I find this:[INDENT]Sep 16 02:57:41 carljohnny-HP-Pavilion-Gaming-Notebook kernel: [    8.536311] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
Sep 16 02:57:41 carljohnny-HP-Pavilion-Gaming-Notebook kernel: [    8.536319] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)
Sep 16 02:57:41 carljohnny-HP-Pavilion-Gaming-Notebook kernel: [    8.536323] pcieport 0000:00:1c.5:   device [8086:a115] error status/mask=00000001/00002000
Sep 16 02:57:41 carljohnny-HP-Pavilion-Gaming-Notebook kernel: [    8.536327] pcieport 0000:00:1c.5:    [ 0] Receiver Error     
[/INDENT]

The message above keeps on repeating for quite a bit and keeps coming up at regular intervals.  


Searching around on the web and this forum among others I found that both the ethernet card or my video card could have something to do with it. Since the system seemed to work anyway I didn't care too much about it. The wifi have been sketchy at best and non-functional at worst so instead I have tried to solve that issue (which I now wonder now if its connected to the previous problem). 

After a couple of days of using the system however, I started getting error messages that root is low on space. I managed to locate a couple of logs in /var/log that seemed to take up waaay to much space (roughly 14 gb). Searching for a solution I came to understand that one of the most reasonable explanations was that something was problematic (for the kernel (?)) and therefore row after row of error messages was being recorded to the log. At which point I figured that the first issue was likely causing all the other issues? And that of course I have no idea how to solve.

As a side note I can also mention that after the error started  popping up some really weird things have been going on like the search  function in unity launcher does not find any apps while many of them can  be started in the terminal etc. Software center will not open at all,  and root-password not being recognized any more.

So. Can you help me with this? What do I need to do to give you some more to work with? 

Would love to continue to use ubuntu so thankful for any help! I also apologize if my language is hard to read but english is not my native language. 

Best regards

---

### Post by mörgæs on 2016-09-18
This is not high-quality advice but since noone else has responded I post anyway.

If it were my computer I would reinstall using another of the 16.04.1 Buntus (K/X/Lubuntu). I know that they use the same kernel but still I would begin experimenting and gathering observations.

---

### Post by carljohnny on 2016-09-18
Thanks for the advice. I have tried openSuse which gave me the same response but perhaps one of the others will work!

---

### Post by carljohnny on 2016-09-18
Not sure if anyone will read. But if someone stumbles over the same problem it seems to be a common bug and the solution seems to work:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)

---

