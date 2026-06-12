---
title: "How do I load Xubuntu without bootloader?"
date: 2014-01-26
forum: General Help
---

### Post by dadoublem on 2014-01-26
I just installed Xubuntu. But it failed to install the boot-loader. How can I access Xubuntu without the boot-loader?

---

### Post by Impavidus on 2014-01-26
Boot from your live disk again (the one you used for installing). Then try Boot-Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). It should be able to fix the bootloader. If it doesn't, you can post here the link to the summary it gives you. It will give us some more information.

---

### Post by monkeybrain20122 on 2014-01-26
Boot from a live usb. locate the partition where you have installed xubuntu with the command
```
blkid
```
So let's say xubuntu is in /dev/sda1

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note that the first line is /dev/sda1 while the second is /dev/sda 

Then reboot.

---

### Post by dadoublem on 2014-01-27
My computer is too slow for either of those options. I installed it with an alternate install disk. And it doesnt have internet.

---

### Post by dadoublem on 2014-01-28
What do I do?

---

### Post by ian-weisser on 2014-01-28
monkeybrain20122 told you what to do.
Until you actually do it, not much more we can help with.

---

### Post by dadoublem on 2014-01-28
my computer cannot boot from usb, it cannot run live cd, and it has no internet.

---

### Post by ian-weisser on 2014-01-28
Ah, that's important information.

You have two options:
1) Put the Alternate CD in the drive and try reinstalling.
2) Put the hard drive in a different machine that can use a Live environment.

If grub fails to work, there is usually a reason for it.
If it fails to install, there is usually an error message.
Error messages have important information in them. Tell us every detail, including all the details and codes you don't understand.

---

