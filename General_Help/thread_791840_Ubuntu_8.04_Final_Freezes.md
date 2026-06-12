---
title: "Ubuntu 8.04 Final Freezes"
date: 2008-05-12
forum: General Help
---

### Post by alcfez on 2008-05-12
Hello,
I installed Ubuntu 8.04 (final) on 14 stations (HP Compaq Desktop, P4, 3Ghz, 256 RAM, dual boot with Win xp pro)
Ubuntu freezes (all computers) from time to time for no reason, without even touching anything. I would start a machine, freeze right away. I can't type or move the mouse and the 2 lights on keyboard keep flashing.
This didn't happen when I had 7.10. I did a clean install after formating 7.10 partitions.
Can someone help, please?

Thank you

---

### Post by TeoBigusGeekus on 2008-05-12
Your ram is a bit too low. I suppose 7.10 was running on the edge...
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by alcfez on 2008-05-13
Thank you,
I will add more ram  and see if that would help..

Shokran!

A

---

### Post by PSP_DEMOLISHER on 2008-05-13
i have installed Ubuntu 8.04 and it freezes as well, it even did when i tried to instal it, it took me 3 tries before it would finish without freezing, now im running an intel board with a 3.33ghz processor and a gig of ram, can someone help me?

---

### Post by alcfez on 2008-05-14
Hello,
I tried something else and it seems to be working fine, for now.
I followed instruction on [Ubuntu Documentation]("https://help.ubuntu.com/community/SwapFaq")  to create a new swap file of 512Mb (I think the default size that Ubuntu 8.04 creates is bout 700Mb) and it seems to work.
Thnx

a

---

### Post by jatoo on 2008-05-15
mine keeps freezing too. i have about 1.5GB of RAM. It freezes at seemingly random times, usually the screen freezes as it is, sometimes it goes completely white.

are you saying decreasing the swap would solve this?

please help!

---

### Post by TeoBigusGeekus on 2008-05-15
Not necessarily... Perhaps it is a graphics problem.
Is everything ok with the restricted drivers?

---

### Post by alcfez on 2008-05-28
Hello,
Bad news. Increasing swap didn't help. It kept freezing. I added 1 RAM stick of 512MB (so now 749MB detected by Ubuntu, beyond minimal requirements) but it still freezes from time to time, blinking Keyboard lights (2 of 3). I have 14 HP Compaq 5100SFF. I have read [here]("http://forums12.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1211966738983+28353475&threadId=1113848") that other users had same problem. 
Sadly, I had to downgrade 1 computer to Ubuntu 7.10 and see what will happen. I have defended Ubuntu and bragged about it, a LOT, and I hate to go back to the other system.
If anyone has any ideas, please let me/us know.

PS. When I click "Restricted Driver" I get this message: "Your hardware does not need any restricted drivers"

---

### Post by TeoBigusGeekus on 2008-05-28
Just a suspicion...

Did you install Ubuntu on all pcs with the same cd? Check its integrity and if necessary redownload it - preferably through torrents.

---

### Post by Mighty_Joe on 2008-05-28
I have a problem with Hardy freezing, though I don't have the keyboard lights flashing.  
[my experience has been]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/227882") that the Hardy's 2.6.24 kernel is broken, but Fedora 9 and the still-being-determined Intrepid Ibex's kernel (both 2.6.25-based) work fine.
I'm sticking with Kubuntu 7.04, which is stable on my hardware, until I see a fix (or Ibex).

---

### Post by alcfez on 2008-05-28
Thank you,
I have installed Ubuntu using 6 different CDs, that I downloaded using torrent. I have checked integrity of CDs I used and the result was positive.
This morning, after downgrading to 7.10, I upgraded using Update Manager. So far so good. I will keep an eye on this test computer and will post results.
thank you 

A

---

### Post by jmmL on 2008-06-13
@ alcfez

I'm also new to ubuntu, and i'm also having freezes in hardy, but they're of a different type to yours by the sound of it.

I guess you've probably sorted out your problems by now, but you mentioned earlier on that you had 2 flashing lights on your keyboard when it froze. I've heard elsewhere that this indicates a kernel panic - just thought this might be useful if you ever come across it again in the future.

---

### Post by alcfez on 2008-06-13
Thank you jmmL,
This is what I did and all computer have been doing great, even after enabling the "desktop effects"
After adding a 512MB memory, I downgraded to 7.10, installed all available updates and then upgraded to 8.04 thru Update Manager.
I tested them, playing movies and using other software... work just fine,
Thank you all for your help.

A

---

