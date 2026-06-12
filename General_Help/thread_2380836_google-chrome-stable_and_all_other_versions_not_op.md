---
title: "google-chrome-stable and all other versions not opening after restart!!"
date: 2017-12-22
forum: General Help
---

### Post by markackerman8@gmail.com on 2017-12-22
Any help appreciated by I doubt there is a real fix.

In the past 2 weeks chrome has stopped opening after I restart my computer.  It opens in the background as can be seen in the task manager (System Monitor). But not on the screen.

I am a long time Linux user and have never had this problem.  I have tried and done many things, and will list them.

Purging and re-installing solves the problem 10/20 times.
```
sudo apt-get purge google-chrome-stable
```

for the other times, I needed to remove the config file - "AS WELL" as purging chrome.
```
rm ~/.config/google-chrome* -rf
```
note: be sure to back up your bookmarks to be safe but google sync will put them back in every time at least so far.

This may help others, now can someone help me.  Why does it still happen again and again, and again, and again ...and I am not kidding about the ~20 times I have re-installed it in the past month.

Oh and I tried another thing that google hits suggests, which is "Disabling the laptop Display' if using a separate monitor.  In the new Ubuntu 17.10 one can only just turn it off by selecting a single and separate screen - my TV Monitor.  But this has helped others and did not help me.  Even "Mirroring" them did not change anything.  I did not play around too much with this as using the laptop screen alone or mirrored is not an option.
I have also tried chromium but it does not support netfilx (at least for me). And why should one use chromium when Google has put out ChromeOS in Chromebooks which is completely  and smartly based on linux. So they must know how to install and run it in Linux!!!!!  Not to mention all their servers are using Linux.   And for the record i ALSO tried the two other version of chrome (Unstable and Dev) ... same issue.

So as one can see I have tried 1,2,3,4,5,6 things is there a 7th or 8th.

I hope there is something missing, and I highly doubt this is only happening to me so any new suggestions on this recurring topic, would be much appreciated by me and doubtless a lot more people too.


Thanks in Advance, Mark
p.s. I sure hope it is not a proprietary glitch by Google trying to make sure you are using only it and not other browsers, or the such, but my paranoia is getting to me.

---

### Post by markackerman8@gmail.com on 2017-12-22
And 2 other things that may help others:

1/  Every time you re-install using terminal (the best way):
```
sudo apt-get install google-chrome-stable
```
It adds their PPA even if it was/is already there so make sure to delete the redundant entry as Update Manger does NOT like redundant entries.

2/  And I tried many time to install it using Three different "Current" google chrome .deb files (my 8th and 9th and 10th), and no difference.

Now the question is is there an 11th thing to try?

Thanks, Mark

---

