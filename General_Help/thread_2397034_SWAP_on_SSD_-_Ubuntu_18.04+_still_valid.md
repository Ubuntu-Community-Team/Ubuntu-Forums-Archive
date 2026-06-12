---
title: "SWAP on SSD - Ubuntu 18.04+ still valid?"
date: 2018-07-24
forum: General Help
---

### Post by SnuKies on 2018-07-24
I'm planing on installing Ubuntu 18.04 on my laptop (Sony Vaio SVE1711), but I am not sure if I still need or not a /swap are for my system.

From what I've been reading so far, most of the people say that I should not create a swap, since it will wear off my SSD faster, but others say that I should still create one with 2-4GB, since modern SSDs are better.
(the IT guy from my workplace told me to create a /swap partition with only 2 GB and disable Hibernate)
I will mostly do programming on my laptop, meaning that IDEs like Android Studio, Intellij and other web-development tools will be on most of the time (*but not all in the same time!!!) *

My system configuration:
[LIST]
[*]8GB RAM
[*]i5-2450m
[*]Intel HD Graphics 5000
[*]Kingston A400 240GB SSD
[/LIST]



Topics I read:
[LIST]
[*][https://askubuntu.com/questions/1032082/is-it-still-bad-to-use-swap-on-a-modern-ssd](https://askubuntu.com/questions/1032082/is-it-still-bad-to-use-swap-on-a-modern-ssd)
[*][https://www.quora.com/Is-it-a-good-idea-to-put-a-Ubuntu-swap-on-an-SSD](https://www.quora.com/Is-it-a-good-idea-to-put-a-Ubuntu-swap-on-an-SSD)
[*][https://askubuntu.com/questions/652337/why-no-swap-partitions-on-ssd-drives](https://askubuntu.com/questions/652337/why-no-swap-partitions-on-ssd-drives)
[*][https://unix.stackexchange.com/questions/218078/linux-ssd-and-swap](https://unix.stackexchange.com/questions/218078/linux-ssd-and-swap)
[*][https://unix.stackexchange.com/questions/219231/8g-ram-and-ssd-how-big-should-the-swap-be](https://unix.stackexchange.com/questions/219231/8g-ram-and-ssd-how-big-should-the-swap-be)
[/LIST]

Most of them say it's okay for /swap area to exists, but some are old and some are new.

And also, what more should I do (beside disabling hibernation) to ensure a proper medium for my SSD?

---

### Post by deadflowr on 2018-07-24
Ubuntu no longer uses swap partitions (though you can create and use one if you want.)
It now creates a swap file.

Refer:
[http://https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files]("http://https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files")
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html?utm_source=omgubuntu]("http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html?utm_source=omgubuntu")

---

### Post by SnuKies on 2018-07-24
I read more on swap files and found out that Ubuntu will create a 2GB file automatically, meaning that I should worry not anymore about swap (correct me if I'm wrong)

---

### Post by oldfred on 2018-07-24
If you have 4GB or more of RAM, you will not use swap as long as you do not open 100's of tabs or edit video. Then you really want unlimited RAM.

You also do not want to use swap as it is orders of magnitude slower than RAM. 

The compromise of a 2GB swap file is that then it works for low RAM systems with 1 or 2GB of RAM, and does not use much file space for larger systems which may never or extremely rarely use it. 
I like to just have some, since system seems to expect to find some.

And SSD now have life similar to HDD, but not unlimited, so good back ups required. The issue with SSD may be they fail suddenly, where HDD often give errors on increased sector failures as  a warning.

---

### Post by HermanAB on 2018-07-24
The SSD will likely outlast you.

My Macbook Pro has no spinning rust, it has swap and logs enabled and it is now 6 years old.

---

