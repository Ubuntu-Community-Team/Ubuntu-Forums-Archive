---
title: "Hard Drive not Detected"
date: 2008-05-25
forum: General Help
---

### Post by SurrealWraith on 2008-05-25
For school, I bring to my classes and use a Lenovo IBM Thinkpad T60.  Unfortunately, my high school's Tech Department has informed the Deans that freeware, sharewere, and opensource software is all illegal(quite similarly to Comcast's logic that all torrents are illegal), and I am therefore not allowed to run Ubuntu at school. 

While I have a working Windows serial, Windows installation disks do not recognize there being a hard drive.  I have partitioned and formatted the the hard drive in FAT, FAT32, and NTFS, yet it is still not recognized.  I tried to see if there was anything in my BIOS that would account for this problem, but it appears that my father set a password on the BIOS, which he has now forgotten.  How can I get the Windows installation to recognize the hard drive so I can dual-boot, and if this requires accessing my BIOS, how can I reset my password? 

Thank you in advanced for your help.

---

### Post by abhiroopb on 2008-05-26
Firstly I'd like to ask what right they have to tell you what is legal and what is not. I don't mean to be pretentious but it is you're laptop. At least with Comcast's logic there is SOME element of truth. Opensource (almost by definition) can't be "illegal". Even the idea is a bit weird. Anyway thats beside the point, but I think you should perhaps talk to the Dean yourself. At my high school I managed to get ubuntu installed on all the machines. It was a LOT easier to maintain, overheads were cheaper, and there were less requests for tech support. Of course this was coupled with a lot of things not working, but in a way this was good as what didn't work was stuff like flash (this was a while back), which simply meant no miniclip games!!

What kind of hard drive do you have? SATA? When you run windows XP cd and get to the point where it asks you to pick a partition to install to, what shows up?

---

### Post by SurrealWraith on 2008-05-26
> **abhiroopb said:**
> 
What kind of hard drive do you have? SATA? When you run windows XP cd and get to the point where it asks you to pick a partition to install to, what shows up?

I believe it is an IDE hard drive, and the installer does not even get far enough to ask me about partitions.  When I press ENTER to initiate the installer, I am told there is no connected hard drive and asked to restart my machine.

---

### Post by Nameless Neko on 2008-05-26
Personally, I'd bring it to your dean's attention that he was incorrectly informed, as none of those three categories of software are illegal in the slightest, and see about getting his ruling reversed.  Point him to Wikipedia articles and other sources of information on open-source software if need be.

Back on topic, sorry, but laptops aren't really my field of expertise, though it sounds like you might have an SATA hard drive that needs drivers for Windows to be installed on it.  Look around online for drivers for your particular model of laptop and toss them on a floppy disk, if you have a floppy drive in your laptop.

Seriously though, talk some sense into your dean for me.  That's just utter BS.

Edit: [http://www.notebookreview.com/default.asp?newsID=2767](http://www.notebookreview.com/default.asp?newsID=2767)
according to the specs listed here, it is indeed an SATA hard drive, and I don't see a floppy disk drive on it.  You might have to use a program like nLite to integrate SATA drivers into a custom XP CD in order to get it installed.

---

### Post by abhiroopb on 2008-05-27
If its SATA it might be giving you trouble. Use nlite to streamline an XP installation. Do it by installing Ubuntu and using a virtual machine to configure it. Alternatively get an XP theme :P [http://ubuntu.online02.com/node/14](http://ubuntu.online02.com/node/14)

Need more help with nlite let me know (got a 181mb install that takes 25 minutes to install!

---

### Post by nilgiri on 2008-09-12
I just had to reinstall one of these at work and figured it out while I was looking for an answer.  Since I am an avid Ubuntu user, I thought I might pitch in here.  I expect you have a SATA drive as I expect all T60 do.  If this is correct, then you need to set the SATA controller to "Compatibility" mode.  In the BIOS (F1 at boot to enter BIOS setup), select Config > SATA > Compatibility.  After changing this, The Windows XP pro installer found the HD with no trouble.

As for getting into the BIOS, if you are being prompted for a password after hitting F1 at boot, then you might be stuck.  You could contact Lenovo, but they are not likely to tell you how to hack their security.  I would open up the laptop and look for some kind of removable system battery, however I can't recommend you do this.  If you do, you do so at your own risk.  Besides, the chances are slim the popping this, if there even is one, will actually reset clear the password.  If it does, it is pretty week security.

There is also a password reset service that are available on this, but you have to subscribed to it using a tool that is available in windows and I expect you have to be in windows to reset it.  I imagine you are hosed on both fronts.

Oh, and for what it's worth, I just gave up on this T60 here because it gets part way into the XP setup and then just powers off.  WTF!?

Finally, if you give me your Dean's contact info and that of your IT folks, I'll personally call them and straighten this out.  I am sure there is just a mis-communication some where.  If not, the free software foundation will be all over their respective asses.

---

