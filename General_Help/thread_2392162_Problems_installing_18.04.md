---
title: "Problems installing 18.04"
date: 2018-05-17
forum: General Help
---

### Post by Old Jimma on 2018-05-17
Hi Community:

I've had "a little trouble" installing 18.04 and can't get it to boot. Previous to doing the install 16.04 was installed and working nicely. :p

In my installations of Ubuntu, I
[LIST]
[*]install the operating system on a 128GB ssd, and
[*]have my /home on another 1 Tb hard drive.
[*]
[/LIST]

It hasn't been hard to install my system on the last 2 or 3 LTS releases. :KS

To achieve this set up, choose "do something else" at the beginning of the install.

On the SSD I
[LIST]
[*]Allocate 16Gb for swap,
[*]Allocate 40BG for \ as an exp4 partion,
[*]Allocate 18GB for \boot as an exp4 partition,
[*]Allocated 18GB to \var as an exp4 partition
[*]Allocated 18GB to \tmp as an exp4 partition.
[*]
[/LIST]

During this installation set up, I identify the HD with my home directory, assign it to be \home, and tell the installation NOT to format it.

:popcorn:

After I get all of this done, I tell my machine to boot from the SSD device.

However, nothing happens.... it won't boot!!!

What am I doing wrong?? :confused:


Thanks,
Old Jimma

---

### Post by dino99 on 2018-05-17
you probably miss the /boot/EFI partition    lp:1767703

---

### Post by Old Jimma on 2018-05-17
Hi Dino:

Not sure what you mean. 

What else am I supposed to do?

Thanks, 

Older than Rock Jimma

---

