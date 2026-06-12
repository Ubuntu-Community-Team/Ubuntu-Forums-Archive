---
title: "Crashed ubuntu, dual boot."
date: 2014-02-19
forum: General Help
---

### Post by Niemil on 2014-02-19
I have a dual boot with Ubuntu 13.10 and Windows 7.
I used Ubuntu mostly in beginning and only Windows for some administration as ubuntu couldn't have a secured bank ID software I needed to have in order to send in some papers each month.

But in start/middle of December last year I started only use Windows 7 because I frequently used graphic softwares that doesn't work very well in Ubuntu.

Now I wanted to return to Ubuntu, but it has changed a little.
At startup of Ubuntu the logo Ubuntu and it's dot had changed font, it was looking very ugly. Also those debug text were on the purple surface with the logo, not on a plain black page as it always use to be.


Then when I got into Ubuntu it was quite lagging, atleast at the beginning. But overall if just felt slow.
Internet also didn't work, I am using Wireless network, and before it been working fine. But now I couldn't even find any settings for wireless or anything. It just said that I had no wire icon in the task manager field (on right top).




Another thing I discovered lots earlier, almost as I started use Windows frequently, were that when I get to the place of choosing OS, that purple place where I choose to start ubuntu or windows.
It used before to count down 10 seconds before it made automatic choice on the selected item (by default it were Ubuntu).

Well, now it doesn't do that 10 seconds, it waits for me until I choose. 




I wonder how to fix these problems?

---

### Post by tgalati4 on 2014-02-20
If you have not used Ubuntu in a while it helps to perform some updates.  Boot into Ubuntu, plug in an ethernet cable (since wireless is not working for you), open a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

Take note of the number of packages that get updated.  Then reboot and make a careful list of problems.  You will want to work one problem at a time on these forums.

---

