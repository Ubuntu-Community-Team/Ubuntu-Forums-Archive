---
title: "[SOLVED] (initramfs) - Ubuntu Boot error"
date: 2007-12-08
forum: General Help
---

### Post by darck on 2007-12-08
I had problems with ext3 Ubuntu partition after resizing with Pargon Partition Manager. After resize I've made backup of files in that way:

```

sudo tar cvpzf arsgeek.backup.tgz &#8211;exclude=&#8221;/proc/*&#8221; \
&#8211;exclude=&#8221;/lost+found/*&#8221; &#8211;exclude=&#8221;/dev/*&#8221; \
&#8211;exclude=&#8221;/mnt/*&#8221; &#8211;exclude=&#8221;/media/*&#8221; &#8211;exclude=&#8221;/sys/*&#8221; \
&#8211;exclude=&#8221;/tmp/*&#8221; &#8211;exclude &#8220;/var/cache/apt/*&#8221; /

```

formated partition, installed ubuntu once again
and restored backup by:  sudo tar xvpfz backup.tgz -C /

And now have problem, because when i choose normal Ubuntu boting in Grub it hungs on loading.

When i choose in Grub failsave start - it hungs somewhere during detecting hdds - it says something about DMA. hungs for few minutes and leaves me with bash user:
(initramfs)

Any way to repair this? Partition with ext3 was somewhow corrupted by Partition Tool, but I beliefe files I backed up are OK

--------------------
Or how to restore as much files as I can from this backup. I think about reinstallation of Ubuntu once again and copying only home dir. What else can i copy to have ubuntu as much as before?

---

### Post by darck on 2007-12-12
if anyone will see this in future: problem was with /boot/grub/menu.list file - there was old (incorrect) UUID, like: UUID=cccacfba-5179-42de-a063-7cd46e784c0c
soulution: repair grub

---

### Post by p_quarles on 2007-12-12
You can increase the likelihood that others with similar problems *will *see this by using the "thread tools" button at the top of the page to mark this (and the other) thread solved.

---

### Post by diaz028 on 2007-12-17
How do I repair Grub?

---

