---
title: "Ubuntu worked perfectly for months, then suddenly won't boot."
date: 2017-03-08
forum: General Help
---

### Post by steve169 on 2017-03-08
I run Windows 7 and Ubuntu 16.04.02 on a Dell Inspiron 660 PC. Both operating systems are in their own partitions, and I select them using Grub 2.

Ubuntu worked beautifully for months, then this morning it refused to boot. The only thing I did since Ubuntu last worked was to back up my Windows 7 partition using Norton Ghost 15.

Here's what happens now:

[INDENT]GRUB comes up and I select Ubuntu.

The Ubuntu logo appears, and the orange dots begin blinking.

After a short while, emergency mode appears with these error messages:

[/INDENT]
[INDENT=2][B]*ERROR* uncleared pch fifo underrun on pch transcoder A

[/B][/INDENT]
[INDENT=2]***ERROR* PCH transcoder A FIFO underrun**[/INDENT]
[INDENT]
I reboot and enter "Advanced options for Ubuntu."

I go to recovery mode and run "dpkg - Repair broken packages," then "grub - Update grub bootloader."

Ubuntu still won't boot.
[/INDENT]

I dread having to reprogram Ubuntu from scratch. Is there something I should try first?

---

### Post by Cavsfan on 2017-03-08
> **steve169 said:**
> I run Windows 7 and Ubuntu 16.04.02 on a Dell Inspiron 660 PC. Both operating systems are in their own partitions, and I select them using Grub 2.

Ubuntu worked beautifully for months, then this morning it refused to boot. The only thing I did since Ubuntu last worked was to back up my Windows 7 partition using Norton Ghost 15.

Here's what happens now:[INDENT]GRUB comes up and I select Ubuntu.

The Ubuntu logo appears, and the orange dots begin blinking.

After a short while, emergency mode appears with these error messages:

[/INDENT]
[INDENT=2][B]*ERROR* uncleared pch fifo underrun on pch transcoder A

[/B][/INDENT]
[INDENT=2]***ERROR* PCH transcoder A FIFO underrun**[/INDENT]
[INDENT]
I reboot and enter "Advanced options for Ubuntu."

I go to recovery mode and run "dpkg - Repair broken packages," then "grub - Update grub bootloader."

Ubuntu still won't boot.
[/INDENT]

I dread having to reprogram Ubuntu from scratch. Is there something I should try first?

Have you tried grub repair from a live disk? [http://linuxpitstop.com/repair-grub-boot-loader-on-ubuntu-linux/](http://linuxpitstop.com/repair-grub-boot-loader-on-ubuntu-linux/)
Just boot up with the DVD and select Try Ubuntu, then do the steps above.

I boot Windows 10, Arch Linux, Xubuntu 16.04 LTS and Zesty Zapus 17.04 currently.

That should work. I've used it several times and many, many other people have too.

---

### Post by steve169 on 2017-03-11
I tried to repair Grub, but it did no good.

So I threw in the towel and just reprogrammed Ubuntu from scratch. It's working now.

I'll mark this "solved," even though there was no true solution.

But thanks anyway, [[COLOR=#000000]Cavsfan[/COLOR]]("https://ubuntuforums.org/member.php?u=889820"). Without you guys we newbies would perish.

---

### Post by Cavsfan on 2017-03-11
> **steve169 said:**
> I tried to repair Grub, but it did no good.

So I threw in the towel and just reprogrammed Ubuntu from scratch. It's working now.

I'll mark this "solved," even though there was no true solution.

But thanks anyway, [[COLOR=#000000]Cavsfan[/COLOR]]("https://ubuntuforums.org/member.php?u=889820"). Without you guys we newbies would perish.

Sometimes the best solution is a clean install. Glad you got it back together.

You are very welcome!

---

