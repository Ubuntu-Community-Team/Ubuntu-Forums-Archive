---
title: "Rewrote boot partition"
date: 2008-01-23
forum: General Help
---

### Post by Lostincyberspace on 2008-01-23
I posted this in the installation section and figured I would post here too so I get more people to see it since I want to get this figured out in the next hour or so I can reinstall if I have to and still be able to do more work.

I, for my brand new linux installation monday, went and made seperate partitions for my /boot and my /home partitons, pretty smart thing I thought. The install went fine and I really liked it. But to day when I went and installed my testbed on a seperate partition I told it to over right the previous /boot partition thinking that thinking that would be a good way to keep clutter out of my system. When I realised I coulden't boot to my regular partition I imediatly whiped out my supergrub disk and rebooted. And it all went down hill from there. And to make a long story short I can't boot any thing any more and am rather flustered about what to do next. 
 
 Could someone help me figure out how I could fix my biggest mistake ever (with computers at least).
 
 If this helps the main partition is Linux Mint, and the test bed partition is Xubuntu though neither boots right now, So they won't be much help to me.

---

### Post by t20racerman on 2008-01-23
What happens when you try to boot the computer? What messages do you get?

---

### Post by Lostincyberspace on 2008-01-23
ACtualy the firstime I tried to boot I got error 17, the second erro 16 , the third error 12 and about five others. I canctually boot to windows now because I booted back into the grub super disk and set the mbr to look there.

---

### Post by louieb on 2008-01-23
Look around this site [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")
It has a write up on creating a dedicated GRUB partition. You'll probably have to modify it a bit to get you boot partition back in shape.

But from the way you described it you deleted your Linux mint kernel.  You may have to reinstall Linux mint just to get the kernel back. But at least you have a separate /home its cases  like this that it sure comes in handy.
Just don't format /home.

---

