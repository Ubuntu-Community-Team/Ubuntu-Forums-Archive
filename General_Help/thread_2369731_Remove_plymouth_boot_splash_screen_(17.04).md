---
title: "Remove plymouth boot splash screen (17.04)"
date: 2017-08-26
forum: General Help
---

### Post by forgeuk on 2017-08-26
Hi all, I've been looking at solutions via google and searching on here, so far none of the suggested solutions work for me and most are 3+ years old, so maybe things have changed?

So... during boot up I see a blue animated Xubuntu logo, I want to see all the geeky boot messages instead.

Here's what I've tried so far:
```
sudo nano /etc/default/grub
```

and I've altered the line with various suggested options:

```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

Saved the file and did a

```
sudo update-grub
```

after each edit. I then reboot and there's the blue boot splash screen like an unflushable turd that it is.
Is there some part of Plymouth I can remove without destroying the OS?
Eg. Looking at removing "plymouth-theme-xubuntu-logo" would also remove vital stuff too. :-(

---

### Post by harterc2 on 2018-04-29
on boot bring up the grub menu.  edit the command and remove splash as an option if it is there.

---

### Post by forgeuk on 2018-04-30
Thanks for the reply, I think that would have worked too. After upgrading to 17.10 last year it worked by altering this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
``` in the grub config file mentioned above. (default is "splash" or "quiet splash")

---

