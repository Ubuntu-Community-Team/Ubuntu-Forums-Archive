---
title: "Updating Breezy SERVER to Dapper"
date: 2006-07-09
forum: General Help
---

### Post by mikesty on 2006-07-09
SUMMARY:

My Goal:
-- Install Breezy 5.10 base install
-- Update to Dapper 6.06 LTS from base install
-- Install Xubuntu Package
-- Run Xubuntu 6.06

Problem: 
-- Trouble editing sources.list

Hello all,

I'm very new to Ubuntu, but I've been able to figure out most of the hitches I've bumped into so far. This is the first big problem I've run into.

Basically, I've been installing Ubuntu on some old machines I have around the house. I have a fresh Ubuntu 6.06 Dapper CD and a fresh Xubuntu Dapper CD and neither of them work. They hang up at some point, and doing a verbose check indicates some read errors. I read up on this, and apparently older computers have trouble reading burnt Dapper CDs. Well, it will take a while for my pressed CDs to arrive, so I just made a fresh Breezy 5.10 CD and had fun with that.

I installed that on one computer and it was fantastic. I was definitely impressed with Ubuntu. Gnome was growing old and I didn't like it too much. Friday, someone asked me if I could give them a crummy old computer to "email, AIM, and check myspace" on.   Low and behold, I get a call from my buddy who's headed off to college. He gave me his old crummy HP Pavilion. I decided I'd go with Ubuntu yet again, but this time I wanted to do XFCE / Xubuntu on it.

So I load up Breezy, do a server install, and then figure how to install the Xubuntu package. Hooray! I loved XFCE after a few tweaks I did to it. It's perfect for a desktop simpleton, IMO. However, I was having some trouble and I wanted to update to Dapper to stay current. I realized that "apt-get dist-upgrade" wasn't working because I had it set to check for Breezy upgrades.

I read a half-dozen webpages that said the same thing - adjust sources.list to say "dapper" where it says "breezy." This didn't work, and failed miserably. Error messages flew across the screen  left and right. Bleh!

Any help would be appreciated. Thanks in advance :)

~mikesty

---

### Post by T700 on 2006-07-09
Did you do a ```
sudo apt-get update
``` first?  Also, don't forget to run it as "sudo".  I'd also suggest using "aptitude" instead of "apt-get" (same syntax).  It is much better at package management and will let you remove things more easily, if ever needed.

Paul

---

### Post by mikesty on 2006-07-09
Yes, I always run update :)

I guess I'll give aptitude a shot :) 

Thanks!!!

---

### Post by mikesty on 2006-07-09
Consider it fixed :) I think I didn't do the extra "update" AFTER saving sources.list, and I also think I correctly edited the sources.list file. Regardless, it appears to work now. Thanks a lot for your support :)

---

