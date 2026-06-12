---
title: "linux hard drive partition won't show up in ubuntu"
date: 2007-03-23
forum: General Help
---

### Post by Logan1310 on 2007-03-23
Hi fellow Ubuntu users,

  I installed Ubuntu successfully in a XP/ Ubuntu dual-boot configuration.  My problem is the Linux partition won't show up in the explorer (not sure what its called I'm new to Ubuntu).  I know the partitions there but why can't I see it.  I can see my Windows partition.  Thanks for your help in advance.

---

### Post by daynah on 2007-03-23
That's the linux default, no worries. It doesn't touch your other harddrives unless you tell it to, just like a proper gentlemen.

So here's how you tell it you like it rough: [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

It's called mounting a harddrive. Whenever you install a harddrive, you have to mount it. If it's a linux harddrive (formatted into ext3 format), you will be able to write in it, while you're in Ubuntu. If it's a windows format (NTFS format) by simply mounting it, you wont be able to write on it unless you take extra steps to make it writable. The guide I just gave you includes all the steps to mount it and make it writeable.

Since you're new, I suggest doing what I did when I was new. Printing this out (if you don't have your printer on Ubuntu yet, print it somewhere else) and mark out on the paper what you did at each step, so that when there's a problem you know exactly how to come back to this  thread and say "AH this exact step didn't work!"

Things will get easier as you use linux. :) I never sat down and studied mounting hard drives, but I've had to do it so many times (I'm in a linux club and I install linux for friends) that, though I still follow a guide, I understand it and it seems really easy to me. You'll get to that level quickly, it's great. :) Remember to have fun with it! I think modding the -inside- of your computer is way more fun than modding the case, the outside.

---

### Post by Logan1310 on 2007-03-23
Thanks for the help, but I don't need to mount my NTFS partition right now I was just worried that I might be writing to the NTFS partition and not to the my ext3 partition.

---

