---
title: "Problem mounting NTFS"
date: 2007-12-18
forum: General Help
---

### Post by Ares2 on 2007-12-18
I've read many threads about my problem but none of them seems to find a solution that would work with my case.

It seems like last time Ubuntu did a disk check, something went wrong because since then, I can't mount my ntfs partition neither can I boot windows on it. I read about about installing ntfsprogs then running ntfsfix /dev/sdXXX

It doesn't seem like it does anything. The problem is that I can't boot in windows anymore because when I try to, my windows blocks after the loading image. Like it enters windows, I can see the blue wallpaper but then I can't log on or do anything. After trying the ntfsfix, when I booted windows, it did a discheck. Then, the same problem occured, I couldn't boot or anything.

By the way, this is what I get when I try to mount my disk:

```

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sda1 /mnt/sda1 -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sda1 /mnt/sda1 ntfs-3g defaults,force 0 0
```

Note that now that I tried the force options, I get this instead:
```
$LogFile indicates unclean shutdown (0, 1)
```

---

### Post by HermanAB on 2007-12-18
Get BartPE, boot off a CDROM and do a checkdisk: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

Herman

---

### Post by Ares2 on 2007-12-18
That would be a great idea, I'm gonna try it when I'll be back from my vacancy.

I'm gonna post in January to see if it works or not because right now I got exams to study then I'll be going out of town anyway. Thanks for the fix ill try it and give news

---

