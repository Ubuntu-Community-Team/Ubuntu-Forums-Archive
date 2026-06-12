---
title: "freezeup boot problems"
date: 2018-09-06
forum: General Help
---

### Post by jgw on 2018-09-06
I just had my machine freeze up again.  This time my browser was shut down and the monitor graphs didn't show any excessive use (cpu, network, memory, drives)  I was trying to edit something (forget what).  When I booted I thought I would try for the grub menu.  Shift did not work (either holding it down or pressing repeatably).  I then stopped the boot and started again.  This time I pressed the 'esc' key and was immediately taken to the [grub] prompt.  I did find out that if you press 'help' at this prompt it will fill the screen with commands, none of which seemed to be helpful in my quest.  I think it was the 'boot' command which asked me to insert a disk to continue even though my drive was bootable.  When I entered ls it told me that it couldn't read 0.0 on drive 0.  When I looked that up I found it meant nothing as it was looking for a dvd or something else not there.

In neither case (shift or esc) was I able to get to the grub menu (if there is a way I would REALLY like to know how to do that).  

I would also like to know why my machine continues to freeze.  When I say freeze I mean REALLY freeze.  The mouse goes away, the keyboard stops working, my monitor graphs freeze, and there is no disk activity light.  The only way to move on is to power down and then up (in these instances I have actually left the frozen machine for over 4 hours and come back to find it still frozen so its not a wait problem).  It would be very nice if I could get to the advanced boot menu to check my filesystem, etc (to see if the power down the screwed things up (which has happened to me))  when I have to do this.  The problem is that seems to be impossible as far as I can tell.  I have done everything but edit the grub file and I really don't want to do that (the last time I did that had a genuine mess on my hands)  I also got the grub customizer in the hope that would allow me to fix it so I could get to the menu - It didn't help with that.

I then thought I would goto the syslog, grab the pertinent area (it was 32 mb long) and post that.  What happened is that it started loading it and THAT froze my system.  (no mouse no keyboard).  I waited a couple of minutes and it finally came back but, is loading something to edit supposed to freeze a system?  If anybody wants me to post that syslog just let me know.

I guess I should also mention that I am getting over 15 updates a day for 18.04.   Over 20 percent of the updates, every day seem to be for vlc.  Today I was told there were over 30, when I tried to update I was told I had duplicates in the sources file.  When I checked all duplicates were disabled with a hatchmark.  I also check with y-ppa for duplicates there and there were none.  I guess I could go back into the sources file and delete all the hashtagged entries but am not sure that is a good idea (I am started to get a bit paranoid).  Right now I am told that there are now 55 to update but I can't because I am being told I have duplicates which is not true.

I know, this is disparate and rambling.  Since I rarely get an answer when it comes to stuff about freezing so I just thought I would at least vent a little.  I also went to ask ubuntu and searched for 18.04 freeze - 24 pages of "18.04 freeze"

Thank you.........

---

