---
title: "Cannot reboot linux (error reading Lunix header, have logs)"
date: 2014-04-08
forum: General Help
---

### Post by Stephen_Montgomery on 2014-04-08
I recently needed to restart a machine we have had running non-stop for several months.

Afterwards, it was not booting normally. It went to the grub prompt. And I couldn't do anything there.
Largely, I couldn't get past a problem identifying linux headers when I ran the "linux /vmlinuz" command

So, I switched to running the boot-repair disk.
After running, I get the message

```
error: cannot read Linux header
error: you need to load the kernel first.
   Failed to boot both default and fallback entries.
Press any key to continue.
```

Not sure what to do now. There is data in the home directories I would like to keep, so I don't want to reinstall if possible.

Here is the boot-repair disk log
[http://paste.ubuntu.com/7222573/](http://paste.ubuntu.com/7222573/)

Thanks for any help!

---

### Post by Stephen_Montgomery on 2014-04-09
I was able to start up using the LiveCD and then mount the hard drive.  My goal is to transfer the data off and then just reinstall.  Was hoping for a way to recover though

---

