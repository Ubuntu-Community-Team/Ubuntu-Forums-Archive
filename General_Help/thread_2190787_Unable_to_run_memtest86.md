---
title: "Unable to run memtest86"
date: 2013-11-29
forum: General Help
---

### Post by J_Me on 2013-11-29
Hello I don't know where to post this thread so I'll try here. I get the memtest86  menu up(without any hotkey options) but it doesn't run through any cycles. Things I've tried are - swapped out memory - left it to run overnight - used live usb kubuntu12.04 - used xubuntu - used an old hdd with kubuntu10.04 on it I posted about this within another thread 2 weeks ago [http://ubuntuforums.org/showthread.php?t=2186659](http://ubuntuforums.org/showthread.php?t=2186659) and swapping out the memory solved those other issues except for memtest86. what else should I try. Also this is a 4 year old netbook with no cd drives. Thanks

---

### Post by mikewhatever on 2013-11-29
Just like my Dell Mini 10..., a four years old netbook, and could never make the Memtest run among other problems. Consider filing a bug report.

---

### Post by J_Me on 2013-11-29
Thanks for the reply, it's not just my Dell mini 10 then. I'm fairly confident that I ran memtest86 on this netbook in the past but can't remember the ubuntu distro flavour or number. Just for the record this netbook came with ubuntu8.04 preinstalled from Dell. I'll try and do a bug report, never did one before though. Thanks again

---

### Post by mikewhatever on 2013-11-29
There is a bug report: [https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/856055](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/856055)

---

### Post by J_Me on 2013-11-29
That's good to know, and it's on medium importance. Do you think it would help to add my own confirmation there as well, looks like it's been two years since the last post.

---

### Post by efflandt on 2013-11-29
I have not tried running memtest86+ from the grub menu for awhile, because there was a problem launching it from there in some Ubuntu versions (because grub2 was too big and took up some of the RAM). You could always download a memtest86+ iso and put it on CD or USB memory stick. That has always worked for me, but not sure what CPU is on your netbook. [http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

---

### Post by J_Me on 2013-11-29
That was suggested to me, but 1- I've run out of usb sticks and 2- I couldn't find an md5sum for that program and I'm always thinking I could make things worse.

---

### Post by mikewhatever on 2013-11-30
I've replied with more details in your original thread about freezing, ...to sum up, it's not the RAM. I guess it is a hardware or BIOS fault, but don't really know.

PS: Just tried running Memtest from Lubuntu 13.10 Live USB, and it works! Go figure.

...2 hors later, 3 passes, no errors.

---

### Post by J_Me on 2013-11-30
@mikewhatever Thanks alot for all your help it's much appreciated, I'll give lubuntu13.10 a try and it's probably time to start looking for a new netbook. Thanks again

---

### Post by mikewhatever on 2013-11-30
Most welcome, and if you really want a new netbook (and live in the right country), [here is one]("http://www.amazon.com/gp/product/B00COQK8QY/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00COQK8QY&linkCode=as2&tag=eriyvewoo-20"). It is definitely a much better machine then the horrible abomination produced by Dell.

---

