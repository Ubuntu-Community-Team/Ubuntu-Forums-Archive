---
title: "UNinstall Ubuntu from dual boot system."
date: 2006-12-31
forum: General Help
---

### Post by ronkas on 2006-12-31
Hi guys.

I would like to uninstall my Ubuntu from this dual boot system (WinXP + Dapper) how can I do it?
It's risky for my data on win?

---

### Post by pseudonym on 2006-12-31
Hi, If you're going to install another linux distro over ubuntu, you don't need to uninstall. You will be able to just reformat the ubuntu partition(s) during installation of the new distro.

If instead you want to go back to just windows (why? :confused:  ) you can just boot up the ubuntu live cd and use the 'cfdisk' utility to delete the ubuntu partition(s). Assuming you installed to a single IDE hard disk, just open up a console from the live cd and type - ```
sudo cfdisk /dev/hda
``` Then highlight each ubuntu partiton one by one and select 'delete'. Then choose 'write' to save the changes.

Doing this just turns your ubuntu partitions back into free space. you can then reformat them how you like from windows. As long as you don't highlight any windows partition by accident in cfdisk, your windows data is perfectly safe.

The GRUB bootloader will still be installed in your hard disk's master boot record (MBR), but it will still allow you to boot windows. But if you want to get rid of that too, you'll need to boot up your windows install CD and go into the recovery console to restore the MBR. The windows CD explains how to do this.

---

